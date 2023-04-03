## Openssl to create CA
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
The `-sha256` option sets the hash algorithm to SHA-256.

### Create a config file 
To create a configuration file for OpenSSL certificate, you can create a new, empty folder and create a file named localhost.cnf.
Copy all of the following text into the file and save it:
```
[req]
default_bits = 2048
prompt = no
default_md = sha256
distinguished_name = dn

[dn]
C=US
ST=CA
L=SanFrancisco
O=MyCompany
OU=MyDivision
CN=localhost
emailAddress=webmaster@localhost.com
```
