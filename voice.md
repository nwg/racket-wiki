Make your computer talk

## Windows 

```scheme
#lang racket/base

(require ffi/com)

(define voice
  (com-create-instance "SAPI.SPVoice"))

(com-invoke voice "Speak" "hello world")
```

## Linux

```scheme
#lang racket/base
(require racket/system)
(system "espeak 'Hello world!'")
```

## MacOS

```scheme
#lang racket 
(system "say 'hello mac world'")
```

