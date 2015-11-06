# Chrome-certificates

Run the following in the command prompt:

    certutil -d sql:$HOME/.pki/nssdb -A -t C,, -n mit -i file.crt
    pk12util -d sql:$HOME/.pki/nssdb -i file.p12
