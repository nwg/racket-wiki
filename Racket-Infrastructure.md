This page describes _public_ details about Racket's infrastructure generally. Logins, administration details, and other private or security-sensitive information should not be included.

## Web

Racket's web presence includes a bunch of web pages, mostly hosted as static sites on Amazon S3 and fronted by the Cloudflare CDN.

## DNS

Racket uses Cloudflare's DNS for `racket-lang.org`. Racket infrastructure also includes `plt-scheme.org`, managed with AWS DNS, as well as some other sites, managed in other ways.

## Build systems

Racket releases are built ...

Racket snapshots are built at two sites, University of Utah and Northwestern University.

Racket CI is handled by cloud services, Travis CI and AppVeyor, as well as by drdr.racket-lang.org, which is a machine hosted at Indiana University. 

build-plot.racket-lang.org builds Racket and tracks time and memory use.

## Other Services

Racket mailing lists are hosted on Google Groups.

The old Racket bug tracker is hosted on a machine at Northeastern University. This is planned for retirement.