# 2 way SSL with spring boot

Example client (nt-gateway) and service (nt-ms) code to show how to get 2 way SSL setup with self signed certificate.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 

### Prerequisites

* Java 1.8
* Spring boot 2.1.2
* Java keytool utility


### Installing

Download nt-gateway and nt-ms projects in to your STS or Eclipse workspace. 

============
Follow below link for help

https://medium.com/@niral22/2-way-ssl-with-spring-boot-microservices-2c97c974e83
https://dzone.com/articles/hakky54mutual-tls-1


============
I have created same keystore and trustore and that can be used int both client and server side


keytool -genkeypair -keyalg RSA -keysize 2048 -alias server -dname "CN=Suleyman,OU=Altindag,O=Altindag,C=NL" -validity 3650 \
 -keystore keystore.jks -storepass password -keypass password -deststoretype pkcs12 -ext SAN=dns:localhost,ip:127.0.0.1;
 
 keytool -exportcert -keystore keystore.jks -storepass password -alias server -rfc -file server.cer
 
 keytool -keystore truststore.jks -importcert -file server.cer -alias server -storepass password
 
 keytool -importkeystore -srckeystore keystore.jks -destkeystore server.p12 -srcstoretype JKS -deststoretype PKCS12 \
 -srcstorepass password -deststorepass password -srcalias server -destalias sb2w -srckeypass password -destkeypass password -noprompt; 
