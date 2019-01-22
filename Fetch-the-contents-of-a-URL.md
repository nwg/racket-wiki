### Fetch the contents of a URL

```racket
;; Get a URL's entity, being sure to close the port.
(require net/url)
(call/input-url (string->url "http://www.google.com")
                get-pure-port
                port->string)

;; Get a URL's headers and entity, being sure to close the port.
(require net/url)
(define-values (headers entity)
  (call/input-url (string->url "http://www.google.com")
                  get-impure-port
                  (lambda (in)
                    (values (purify-port in)
                            (port->string in)))))
```
