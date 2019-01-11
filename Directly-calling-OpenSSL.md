#### Directly calling the OpenSSL executable from Racket 

This example generates a 1024-bit RSA key in PEM format 

Idea courtesy of Neil Van Dyke. Control flow suggested by Neil Van Dyke, Robby Findler and Eli Barzilay. 

```racket
(parameterize ([current-input-port (open-input-string "")])
  (with-output-to-string (λ _(system* (build-path "c:" "openssl-win32" "bin" "openssl.exe")
                                      "genrsa" 
                                      "1024"))))
```

#### More OpenSSL: generating an HMAC-SHA1 digest 
```racket
;;returns the string "(stdin)= 5df23ffdf57d5d925f150c885d64bee2eaf55a43\n"

(parameterize ([current-input-port (open-input-string "We are Spinal Tap!")])
  (with-output-to-string (λ _ (system* (build-path "c:" "openssl-win32" "bin" "openssl.exe")
                                      "dgst" 
                                      "-sha1"
                                      "-hex"
                                      "-hmac"
                                      #"mysecretkey"))))
```


