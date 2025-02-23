# SSL Certificates
To generate an SSL certificate and private key pair, use the following command:
```bash
openssl req -x509 -newkey rsa:4096 -keyout privatekey.key -out public-certificate.crt -sha256 -days 365
```

* Add the `-nodes` flag to disable DES passphrase encryption
* Add the `-addext "subjectAltName = DNS:foobar.com,IP:111.222.111.222"` to specify a subjectAltName
* `-days` specifies the time until expiry
