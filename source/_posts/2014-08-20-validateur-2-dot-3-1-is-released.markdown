---
layout: post
title: "Validateur 2.3.1 is released"
date: 2014-08-20 23:49:14 +0400
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 2.3 is a minor feature release.


## Changes Between 2.2.0 and 2.3.0

### unnest

`unnest` is a helper function useful for building UIs that validate on
the fly. Here's a basic example. Let's write some code to render a UI
off of a nested map and build up live validation for that map off of
component validators. Here are the components:

```clojure
(def profile-validator
  (vr/validation-set
   (vr/presence-of #{:first-name :last-name})))

(def secret-validator
  (vr/validation-set
   (vr/length-of :password :within (range 5 15))
   (vr/length-of :phone :is 10)))
```

And then the composed, user account validator:

```clojure
(def account-validator
  (vr/compose-sets
   (vr/nested :secrets secret-validator)
   (vr/nested :profile profile-validator)))
```

Next are the "rendering" functions. Imagine that these are input
components responsible for validating their input and displaying
errors when present. Our "render" phase will just print.

```clojure
(defn render-profile [profile errors]
  (prn "Profile: " profile)
  (prn "Profile Errors: " errors))

(defn render-secrets [secrets errors]
  (prn "Secrets: " secrets)
  (prn "Secret Errors: " errors))

(defn submit-button
  "Renders a submit button that can only submit when no errors are
  present."
  [errors]
  (prn "All Errors: " errors))
```

The `render-account` function renders all subcomponents, performs
global validation and routes the errors and data where each needs to
go:

```clojure
(defn render-account
  "This function accepts an account object, validates the entire thing
  using the subvalidators defined above, then uses `unnested` to pull
  out specific errors for each component.

  The entire validation error map is passed into `submit-button`,
  which might only allow a server POST on click of the full error map
  is empty."
  [{:keys [secrets profile] :as account}]
  (let [errors (account-validator account)]
    (render-profile profile (vr/unnest :profile errors))
    (render-secrets secrets (vr/unnest :secrets errors))
    (submit-button errors)))
    ```

Let's see this function in action. Calling `render-account` with an
invalid map triggers a render that shows off a bunch of errors:

```clojure
(render-account
   {:secrets {:password "face"
              :phone "703555555512323"}
    :profile {:first-name "Queequeg"}})


"Profile: " {:first-name "Queequeg"}
"Errors: " {[:last-name] #{"can't be blank"}}
"Secrets: " {:password "face", :phone "703555555512323"}
"Errors: " {[:phone] #{"must be 10 characters long"}, [:password] #{"must be from 5 to 14 characters long"}}
"All Errors: " {[:profile :last-name] #{"can't be blank"}, [:secrets :phone] #{"must be 10 characters long"}, [:secrets :password] #{"must be from 5 to 14 characters long"}}
```

Calling `render-account` with a valid map prints only the data:

```clojure
(render-account
 {:secrets {:password "faceknuckle"
            :phone "7035555555"}
  :profile {:first-name "Queequeg"
            :last-name "Kokovoko"}})

"Profile: " {:last-name "Kokovoko", :first-name "Queequeg"}
"Errors: " {}
"Secrets: " {:password "faceknuckle", :phone "7035555555"}
"Errors: " {}
"All Errors: " {}
```

### nest

`nest` is a helper function that makes it easy to validate dynamic
data that's not part of the actual map you pass into the
validator. For example, say you wanted to validate all user accounts,
then build up a map of userid -> validation errors:

```clojure
(for [account (get-all-accounts)]
  (vr/nest (:id account)
           (account-validator account)))

{[100 :profile :first-name] "can't be blank"
 [200 :profile :last-name] "can't be blank"
 ;; etc
 }
```


## Full Change Log

[Validateur change log](https://github.com/michaelklishin/validateur/blob/master/ChangeLog.md) is available on GitHub.



## Validateur is a ClojureWerkz Project

[Validateur](http://github.com/michaelklishin/validateur) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Validateur, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
