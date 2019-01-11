#### Web Server: Creating an Interface Definition Language (IDL) between an HTTP-request and Racket code, Part I

**Discussion:** an HTTP request contains name/value bindings passed as byte-strings.

Maybe.

_**Sad, Tragic and Unfortunate Outcome space:**_

**1)** Bindings your Racket code expects could be missing. 

**2)** optional bindings might be present or absent

**3)** The underlying values might not be interpretable as the value types you expect (just when you expect an integer, the binding-value is "_frobnitzzz_")

**4)** The actual values passed might be outside the domain (i.e. allowable values) the Racket code works on


We want to catch these problems using the contract system before we create a server error. We use _functional composition_ to create **make-idl**, which will take four arguments:

Recall that in _composition_, the first function to execute is the rightmost argument, with its return value(s) being passed to the function-argument on its left

So reading **(make-idl....)** from right to left:

**binding-name**: the name of the binding we expect in the HTTP request

**optionality-fn**: one of two functions. either **required-arg**, or **optional-arg.** **required-arg** will throw an error if the binding is missing or malformed. **optional-arg** allows missing bindings to pass

**transform-fn** will transform the byte-string to some primitive type (number, boolean, etc.) or throw an error trying
and 

**contract-fn**, which is the actual domain-enforcing racket-contract we want to assert before we send the argument to the server

**(make-idl...)** returns a single function which operates on the **HTTP request-bindings**, and either returns a value which honors the description we memorialized in the four arguments, or throws an error

Usage and the missing helper functions will be discussed in Part II.

```racket
(require (prefix-in HTTP: web-server/http/request-structs)) 

(define/contract (make-idl            contract-fn
                                      transform-fn
                                      optionality-fn 
                                      binding-name)
  (-> contract? (-> any/c any/c) (-> any/c any/c) bytes? (-> (listof HTTP:binding?) any/c))
  (compose (λ (x) (if (not (contract-fn x))
                      (raise (exn:fail (format "IDL layer error: binding contract error\n" ) (current-continuation-marks)))
                      x))
           (λ (x) (if (not (transform-fn x))
                      (raise (exn:fail (format "IDL layer error: binding transformation error\n" ) (current-continuation-marks)))
                      (transform-fn x)))
           optionality-fn
           (λ (bindings) (HTTP:bindings-assq binding-name bindings))))

```

