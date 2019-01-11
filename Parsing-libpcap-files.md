#### Parsing libpcap files

This is a quick hack for parsing libpcap files (the standard format used by packet-capturing programs, e.g. wireshark) into packets. (John Clements)

```racket
(define (file->packets file)
  (define pcap-bytes (file->bytes file))
  
  (define global-header (subbytes pcap-bytes 0 (* 6 4)))
  
  (define packets
    (let loop ([offset 24])
      (cond [(< offset (bytes-length pcap-bytes))
             (define pcaprec-header (subbytes pcap-bytes
                                              offset
                                              (+ offset 16)))
             (define captured-len (integer-bytes->integer pcaprec-header
                                                          #f #f
                                                          8 12))
             (define packet-len (integer-bytes->integer pcaprec-header
                                                        #f #f
                                                        12 16))
             (when (not (= captured-len packet-len))
               (fprintf (current-error-port)
                        "warning: captured only ~v bytes of packet with ~v bytes\n"
                        captured-len packet-len))
             (printf "packet len: ~v\n" captured-len)
             (cons 
              (list pcaprec-header
                    (subbytes pcap-bytes (+ offset 16)
                              (+ offset 16 captured-len)))
              (loop (+ offset 16 captured-len)))]
            [else empty]))))
```

    