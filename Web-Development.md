# Web Development in Racket

* [Papers, Talks and Tutorials](#papers-talks-and-tutorials)
* [Examples](#examples)
* [Back-end Development](#back-end-development)
* [Front-end Development](#front-end-development)
* [Database tools](#database-tools)
* [Authentication and Authorization](#authentication-and-authorization)
* [Testing](#testing)
* [Internals](#internals)
* [Related](#related)


## Books 

* [Server: Racket](http://serverracket.com/): Develop a web application with Racket.

## Papers, Talks and Tutorials

* [Continue: Web Applications in Racket](https://docs.racket-lang.org/continue): tutorial on creating a database backed web application
* [Web Applications in Racket](https://docs.racket-lang.org/web-server/): describes the Racket libraries for building Web applications.
* [Web Server: HTTP Server](https://docs.racket-lang.org/web-server-internal/index.html): describes the internals of the Racket Web Server.
* [Deploying Racket applications on Heroku](https://lexi-lambda.github.io/blog/2015/08/22/deploying-racket-applications-on-heroku/)
* [The Missing Guide to Racket's Web Server](https://defn.io/2020/02/12/racket-web-server-guide/)
* [Continuations in Racket's Web Server](https://defn.io/2020/05/11/racket-web-server-internals/)

## Examples

* [Nemea](https://github.com/Bogdanp/nemea): Web analytics tracker.
* [Pasterack](http://pasterack.org/): Racket pastebin.  ([source](https://github.com/stchang/pasterack))
* [Try Racket](https://try-racket.defn.io/): Racket playground. ([source](https://github.com/Bogdanp/try-racket))

The following working examples are on glitch.com. Racket is installed via the `install.sh` script and you can click the 'Remix to Edit🎤' button to make yourself a copy you can experiment with. 

* [Rantstack](https://glitch.com/~rantstack): a simple web app in Racket.
* [elm-on-racket](https://glitch.com/~elm-on-racket): a simple hello-world app, with an Elm frontend hosted by a simple Racket/Spin backend.

## Back-End Development

### Web Frameworks

* [HoLy](https://github.com/nihirash/holy): A simple HTTP-server Library for Racket.
* [koyo](https://docs.racket-lang.org/koyo@koyo-doc/index.html): A complete web application development toolkit.
* [Raf](https://github.com/z-song/raf/): A simple REST Application Framework.
* [Routy](https://github.com/Junker/routy): A lightweight high performance HTTP request router for Racket.
* [Spin](https://github.com/dmac/spin): Write RESTful web apps in Racket.
* [vela](https://github.com/nuty/vela): Simple web framework to build RESTful app in Racket.
* [web-galaxy](https://github.com/euhmeuh/web-galaxy): A minimalist web framework for the Racket web-server.

### Web Sockets

* [RFC 6455 WebSockets for Racket](https://docs.racket-lang.org/rfc6455/index.html): provides RFC 6455 compatible WebSockets server and client interfaces for Racket, building on Racket’s `web-server` collection.

### Static Site Generators

* [frog](https://github.com/greghendershott/frog)
* [polyglot](https://github.com/zyrolasting/polyglot): Create websites using a mix of any language or workflow.

### HTTP Clients

* [Request](https://github.com/jackfirth/racket-request): Package for simplifying HTTP requests and writing integration tests of REST-ful APIs in Racket
* [http-easy](https://docs.racket-lang.org/http-easy/index.html?q=http-easy): a high-level HTTP client with support for connection pooling, file uploads and a load of other stuff.

### JSON Processing

* [Riposte—Scripting Language for JSON-based HTTP APIs](https://github.com/vicampo/riposte)
* [json-pointer: Referring to bits of JSON](https://github.com/jessealama/json-pointer): JSON Pointer (RFC 6901) is a straightforward notation for referring to values embedded within a JSON document. (Racket implementation of a JSON Pointer evaluator (RFC 6901))
* [JSON](https://docs.racket-lang.org/json/): utilities for parsing and producing data in the JSON data exchange format to/from Racket values.
* [JSONSourcery](https://docs.racket-lang.org/json-sourcery/): A library built on top of the json package for improving JSON serialization and adding clearer syntax macros.

### Protocol

* [html5](https://github.com/jessealama/rhtml5) Racket implementation of the HTML5 parsing algorithm.
* [URI Template (RFC 6570) for Racket](https://github.com/jessealama/uri-template)

### Testing 

* [marionette](https://github.com/Bogdanp/marionette): control Firefox browsers using Racket.

### Web Services

* [Amazon Web Services](https://docs.racket-lang.org/aws/index.html) provides support for many of the Amazon Web Services.


## Front-end Development

* [Urlang](https://github.com/soegaard/urlang) 'Urlang is JavaScript with a sane syntax'
* [RacketScript](https://github.com/vishesh/racketscript) Racket to JavaScript Compiler
  * [RacketScript Playground](http://rapture.twistedplane.com:8080/)


## Caching

* [memcached](https://docs.racket-lang.org/memcached/index.html): an interface to memcached.
* [redis-rkt](https://github.com/bogdanp/racket-redis): a production-ready Redis client.


## [[Database Tools]]


## Authentication and Authorization

* https://github.com/johnstonskj/simple-oauth2
* https://github.com/tonyg/racket-google
* https://github.com/rmculpepper/webapi
* [JSON Web Token (JWT) and JSON Web Signature (JWS)](https://docs.racket-lang.org/jwt/): JSON Web Token parsing and verification in Racket ([source](https://github.com/RenaissanceBug/racket-jwt))
* https://github.com/eu90h/racket-github-api
* https://github.com/nitros12/racket-cord
* [dvanhorn/tweet.rkt](https://gist.github.com/dvanhorn/815bdda5cfcdee18d480cb6a5d1119f3)  (OAuth v1?)

