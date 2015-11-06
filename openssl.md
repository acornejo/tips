# OpenSSL

To generate a private/public key pairs with password:

    openssl genrsa -des3 -out private.pem 4096

To generate a private/public key pair without password

    openssl genrsa -out private.pem 4096

To view a key

    openssl rsa -in private.pem -text

To extract the public key from the private key

    openssl rsa -in private.pem -pubout -out public.pem

To encrypt FILE to FILE.enc using the public key

    openssl rsautl -encrypt -inkey public.pem -pubin -in FILE -out FILE.enc

To decript FILE.enc to FILE using the private key

    openssl rsautl -decript -inkey private.pem -in FILE.enc -out FILE

To produce signature of FILE using private key

    openssl dgst -sha256 -sign private.pem -out signature FILE

To verify signature of FILE using public key

    openssl dgst -sha256 -verify public.pem -signature signature FILE

To extract the public key out of certificate

    openssl x509 -pubkey -noout -in certificate.crt -out public.pem

To view a certificate

    openssl x509 -in certificate.{crt,cer,pem} -text -noout
