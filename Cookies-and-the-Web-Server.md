#### Cookies and the Web Server 

Two quick notes:

1) You can pass base64 encoded values to the browser as cookie-values as long as you strip both out the embedded and trailing carriage-return-line-feed sequences. 

**BAD:**
```racket
(define (start request)
  (response/xexpr `(html (head (meta ((name "viewport")(content "initial-scale=1.0, user-scalable=no")))
                               (meta ((http-equiv "content-type")(content "text/html; charset=UTF-8"))))
                                       (body (div "Cookies!")))
                  #:headers  (list (make-header #"Set-Cookie" #"Racketboy=XetM5o+My2BQYizra/y+NC7UJ0MxMjM0\r\nNTY2OQ==\r\n; Secure;"))))
```

**GOOD:**
```racket
...code...
#:headers  (list (make-header #"Set-Cookie" #"Racketboy=XetM5o+My2BQYizra/y+NC7UJ0MxMjM0NTY2OQ==; Secure;"))
...code...
```

2) The Secure flag in the cookie only instructs the **browser** not to send the cookie over a non-secure connection. The server will happily pass a Secure-flag cookie over a non-secure connection.

To prevent the a Secure-flag cookie from being sent over a non secure connection, set the #:ssl keyword argument to #t in serve/servlet.
