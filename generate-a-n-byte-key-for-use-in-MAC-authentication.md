##### generate a n-byte key for use in MAC authentication (like HMAC-SHA1)
```racket
;usage (generate-authenticator-key 32) -> returns 256-bit key
(define/contract (generate-authenticator-key key-len)
  (-> exact-positive-integer? bytes?)
  (list->bytes (build-list key-len (λ _ (random 255)))))
```
