HTTP connections using SSL

Using the `net/url` collection:

    #lang racket/load

    (module ssl-url.ss racket

     ;; From Eli Barzilay

     ;; This will give us ssl:--- for an ssl version of url.ss, but still need an
     ;; explicit port number specification since url.ss does not handle that
     (require racket/unit
              net/url-sig net/url-unit
              net/tcp-sig net/tcp-unit
              net/ssl-tcp-unit)
    
     (define-values/invoke-unit (compound-unit/infer (import) (export url^) (link tcp@ url@))
       (import)
       (export url^))
    
     (define ssl-tcp@ (make-ssl-tcp@ #f #f #f #f #f #f #f))
    
     (define-values/invoke-unit
       (compound-unit (import) (export URL)
                      (link [((TCP : tcp^)) ssl-tcp@]
                            [((URL : url^)) url@ TCP]))
       (import)
       (export (prefix ssl: url^)))
    
     (provide (all-defined-out))
     )
    
    (module sample-client racket/gui
    
     ; (require "ssl-url.ss")
     (require 'ssl-url.ss)
    
     (define LOGIN "https://myneu.neu.edu/myneu/login/lock.gif")
    
     (ssl:call/input-url
      (string->url LOGIN)
      ssl:get-pure-port
      (lambda (ip)
        (define file "login-image.gif")
        (with-output-to-file file (lambda () (copy-port ip (current-output-port))) #:exists 'replace)
        (make-object image-snip% file 'gif))))
    
    (require 'sample-client)

Most of the above is wrapped into a PLaneT package: http://planet.racket-lang.org/display.ss?package=ssl-url.plt&owner=offby1

Using the `bzlib/http` PLaneT library:

    (require (planet bzlib/http/client))
    (http-get <url> <list-of-headers>)
    (http-post <url> <data> <list-of-headers>)

See also: http://schemecookbook.org/view/Cookbook/WebFetchingHttpsUrl