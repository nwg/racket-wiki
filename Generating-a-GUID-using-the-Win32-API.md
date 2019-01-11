#### Generating a GUID using the Win32 API

Demonstrates use of the Foreign Function Interface (FFI) to create a Globally Unique ID

```racket
#lang racket

#|
creates a GUID using the Win32API via the foreign function interface

usage:
(new-GUID) ; ->"3849203981-8836-19662-12178292003955076235"

;returns a max(43) length string, which we can store in database
and set a UNIQUE constraint to make sure same order isn't entered twice.
|#

(require  ffi/unsafe)

(provide new-GUID)

(define ole32 (ffi-lib "ole32.dll"))

(ffi-lib? ole32)

(define-cstruct _GUID ([Data1 _uint32]    ;32 bytes, max 10 char when converted to string
                       [Data2 _uint16]    ;16 bytes, max 5 char when converted to string
                       [Data3 _uint16]    ;16 bytes, max 5 chars when converted to string 
                       [Data4 _uint64]))   ;simulates 8x8 char array for 64 bytes total, max 20 chars when converted to string       

(define generate-GUID  (get-ffi-obj "CoCreateGuid" ole32 (_fun  _GUID-pointer -> _uint32)))
  
(define (new-GUID)
  (let* ((x (make-GUID 0 0 0 0)) ;note make-GUID returns a pointer to a _GUID structure
        (res (generate-GUID x)))
    (if (= res 0)
        (string-append 
         (number->string (GUID-Data1 x)) "-"
         (number->string (GUID-Data2 x)) "-"
         (number->string (GUID-Data3 x)) "-"
         (number->string (GUID-Data4 x)))
        (error "Unable to generate GUID"))))
  

```

