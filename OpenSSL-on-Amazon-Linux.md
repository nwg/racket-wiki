#### OpenSSL on Amazon Linux ####

When installing Racket on the Amazon Linux AMI, choose the Fedora build. For example use the `racket-5.2.1-bin-x86_64-linux-f14.sh` installer for Racket 5.2.1 with the 64-bit Amazon Linux AMI.

You may find that `openssl` module calls give a runtime error. This includes procedures like `ssl-connect`, and procedures that use it indirectly such as `get-pure-port` with an `https` scheme in the URI.

To fix, install the `openssl-devel` package:

`$ sudo yum install openssl-devel`

