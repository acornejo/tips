# GPG

To generate a key: gpg --gen-key

To list your private keys: gpg -K

To output ascii version of key: gpg -a --export "key name"

Send to keyserver: gpg --send-keys "key name" --keyserver
hkp://subkeys.pgp.net

Encrypt using public key: gpg -e -r "recipient key name" file.txt

Symmetric Encryption (no keys): gpg -c file.txt

Decrypt: gpg -d file.txt.gpg
