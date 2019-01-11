This page captures useful code snippets that are too small to be a Planet package. 

[[Specifying a HMAC-SHA1 stuffer for the stateless web-server]]  
[[Split a string into lines]]  
[[Fetch the contents of a URL]]  
[[generate a n-byte key for use in MAC authentication]]  
[[How to generate a Message Authentication Code (MAC) and authenticate a signed message|generate a MAC and authenticate a signed message]]  
[[Redirecting an HTTP-scheme URL to an HTTPS-scheme URL using two servlets]]  
[[Parsing libpcap files]]  
[[Directly calling the OpenSSL executable from Racket|Directly calling OpenSSL]]  
[[OpenSSL on Amazon Linux]]  
[[On Error Resume Next using Pattern Matching Macros]]  
[[How to generate a rotating key-value, which changes at some arbitrary interval|How to generate a rotating key value]]  
[[AJAX: How to build a response to an HTTPXmlRequest]]  
[[How to Build a Context-Free Grammar with Racket's unique Recursive Contract System]]  
[[How to transform a Tree (see above) into an x-expression]]  
[[Web Server: Creating an Interface Definition Language (IDL) between an HTTP-request and Racket code, Part I|Creating an Interface Definition Language]]  
[[Cookies and the Web Server]]  
[[AJAX and the Web Server]]  
[[Generating a GUID using the Win32 API]]  
[[Sending a file to the Windows Print Spool using the Win32 API]]  
[[Quickly create a large file]]  (e.g. for testing, or to reserve disk space for later use)  
[[More convenient printing of multiple values]]  


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
