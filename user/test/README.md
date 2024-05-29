openssl rand -hex 16 > random.txt

openssl pkeyutl -sign -inkey ../private.key -in random.txt > test.sig

openssl x509 -in ../proof.crt -pubkey -noout > public_key.pem

openssl pkeyutl -verify -pubin -inkey public_key.pem -sigfile test.sig -in random.txt