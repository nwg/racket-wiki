# Racket web development tools

* [paper/talks/tutorials](#papertalkstutorials)
* [Examples](#examples)
* [Front-end dev](#front-end-dev)
* [Back-end dev](#back-end-dev)
* [Database tools](#database-tools)
* [Testing](#testing)
* [Internals](#internals)
* [Related](#related)

## paper/talks/tutorials

* [Continue: Web Applications in Racket](https://docs.racket-lang.org/continue) tutorial on creating a database backed web application
* [Web Applications in Racket](https://docs.racket-lang.org/web-server/) describes the Racket libraries for building Web applications.
* [Deploying Racket applications on Heroku](https://lexi-lambda.github.io/blog/2015/08/22/deploying-racket-applications-on-heroku/)

## Examples
Both these working example are on glitch.com. Racket is installed via the `install.sh` script.
You can click the 'Remix to Edit🎤' button to make yourself a copy you can experiment with. 
* [Pasterack](http://pasterack.org/): Racket pastebin.  [source](https://github.com/stchang/pasterack)
* [Rantstack](https://glitch.com/~rantstack): a simple web app in Racket (glitch.com)
* [elm-on-racket](https://glitch.com~elm-on-racket): a simple hello-world app, with an Elm frontend hosted by a simple Racket/Spin backend.

## Front-end dev
* [Urlang](https://github.com/soegaard/urlang) 'Urlang is JavaScript with a sane syntax'
* [RacketScript](https://github.com/vishesh/racketscript) Racket to JavaScript Compiler
  * [RacketScript Playground](http://rapture.twistedplane.com:8080/)

## Back-End dev

* [JSON Web Token (JWT) and JSON Web Signature (JWS)](https://docs.racket-lang.org/jwt/) JSON Web Token parsing and verification in Racket ([source](https://github.com/RenaissanceBug/racket-jwt))
* [Requests](https://github.com/jackfirth/racket-request) Package for simplifying HTTP requests and writing integration tests of REST-ful APIs in Racket
* [Riposte—Scripting Language for JSON-based HTTP APIs](https://github.com/vicampo/riposte)
* [json-pointer: Referring to bits of JSON](https://github.com/jessealama/json-pointer): JSON Pointer (RFC 6901) is a straightforward notation for referring to values embedded within a JSON document. (Racket implementation of a JSON Pointer evaluator (RFC 6901))
* [URI Template (RFC 6570) for Racket](https://github.com/jessealama/uri-template)
* [JSON](https://docs.racket-lang.org/json/) utilities for parsing and producing data in the JSON data exchange format to/from Racket values.
* [JSONSourcery](https://docs.racket-lang.org/json-sourcery/) A library built on top of the json package for improving JSON serialization and adding clearer syntax macros.

### Database tools
* [DB: Database Connectivity](https://docs.racket-lang.org/db/index.html) A database interface for functional programmers.
* [SQL: A Structured Notation for SQL Statements](https://docs.racket-lang.org/sql/index.html) provides an S-expression notation for a subset of SQL. It provides forms that produce statements (as opaque values rather than strings) that can be used directly with Racket’s db library. 
* [Racquel: An Object/Relational Mapper for Racket](https://docs.racket-lang.org/racquel/index.html)
* [sql-sourcery](https://github.com/adjkant/sql-sourcery)Database backed structs for functional programmers. An ORM for mapping structures in Racket to database entries in a SQL database. All versions 0.1.X are unstable Alpha releases. Current version 0.1.0

## testing 
* [**marionette**](https://github.com/Bogdanp/marionette): A Racket library that lets you control Firefox via the Marionette Protocol. (the aim of the Marionette protocol is to make automated browser testing easy)

## Internals 
* [Web Server: HTTP Server](https://docs.racket-lang.org/web-server-internal/index.html) manual describes the internals of the Racket Web Server.

## related
* [html5](https://github.com/jessealama/rhtml5) Racket implementation of the HTML5 parsing algorithm.
* [RFC 6455 WebSockets for Racket](https://docs.racket-lang.org/rfc6455/index.html) This package, rfc6455, provides RFC 6455 compatible WebSockets server and client interfaces for Racket, building on Racket’s web-server collection.
* [OpenSSL: Secure Communication](https://docs.racket-lang.org/openssl/index.html)
* [Amazon Web Services](https://docs.racket-lang.org/aws/index.html) provides support for many of the Amazon Web Services.
* [memcached](https://docs.racket-lang.org/memcached/index.html) an interface to memcached.