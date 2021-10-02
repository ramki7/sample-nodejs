# sample-nodejs
---
create the docker-compose file for nodejs, mysql, mongo server and make connection between them.

and volume map for data storage.
----------
Reg SSL cert for Non-prod use Openssl cert.

if it is production use CA Cert.

for openssl cert create certificate using below commands
-----------
yum -y install mod_ssl openssl

cert=`hostname -i`

openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -out $cert.key

chmod 600 $cert.key

openssl req -new -key $cert.key -out $cert.csr

openssl x509 -req -days 365 -in $cert.csr -signkey $cert.key -out $cert.crt

--------------
place this ssl cert in nginx web-server to serve the traffic with SSL.

change the traffic port to 443 for hhtps.

In case of AWS ELB. place the CA Cert in certificate manager. then call to the ELB
