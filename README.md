# OPenssl self signed certificates
```
You can generate your own self-signed certificates using OpenSSL if you don’t have access to a certificate authority (CA) 
for your organization and want to use Open Distro for Elasticsearch for non-demo purposes¹. Here are the steps to generate
a self-signed certificate for the root CA using OpenSSL:
1. Generate a private key for the root CA:
```
openssl genrsa -out root-ca-key.pem 2048
```
2. Next, use the key to generate a self-signed certificate for the root CA:
```
openssl req -new -x509 -sha256 -key root-ca-key.pem -out root-ca.pem
```
The `-x509` option specifies that you want a self-signed certificate rather than a certificate request.
The `-sha256` option sets the hash algorithm to SHA-256¹.

