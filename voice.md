Four lines to make your computer talk (on Windows):
```scheme
#lang racket/base

(require ffi/com)

(define voice
  (com-create-instance "SAPI.SPVoice"))

(com-invoke voice "Speak" "hello world")
```