##### How to generate a Message Authentication Code (MAC) and authenticate a signed message.

This would be useful for creating the "Unforgeable Authenticator Cookie", discussed in section 4.1 of the MIT 
Cookie Eater's recommendations (see: "Do's And Don'ts of Client Authentication on the Web", Fu et al)

Note: Uses generate-authenticator-key from the preceding Artifact.

```racket
(require web-server/stuffers/hmac-sha1)

;use 128-bit key
(define *private-key* (generate-authenticator-key 16))

(define *signed-message* (let* ((plaintext #"We are Spinal Tap!")
                                (MAC (HMAC-SHA1 plaintext *private-key*)))
                           (bytes-append MAC plaintext)))
  
;;now we lose custody of *signed-message* by sending it to the client...

;;and now we get *signed-message* back and attempt to authenticate it

(let ((received-MAC (subbytes *signed-message* 0 20))
      (received-plaintext (subbytes *signed-message* 20)))
  (if (bytes=? received-MAC
               (HMAC-SHA1 received-plaintext 
                          *private-key*))
      "Message is authentic and not forged"
      "Message has been forged"))

```

