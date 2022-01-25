# SSL Certificates
To generate an SSL certificate and private key pair, use the following command:
```bash
openssl req -x509 -newkey rsa:4096 -keyout privatekey.key -out public-certificate.crt -sha256 -days 365
```

* Add the `-nodes` flag to disable DES passphrase encryption
* `-days` specifies the time until expiry
