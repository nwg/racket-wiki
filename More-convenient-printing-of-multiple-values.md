##### More convenient printing of multiple values

```
(define-syntax (say stx)
  (syntax-case stx ()
    [(_ a b ...)
     #'(displayln (~a a b ...))]))
```

Use as follows:

```  
(say "The value of x is: " x)
```
