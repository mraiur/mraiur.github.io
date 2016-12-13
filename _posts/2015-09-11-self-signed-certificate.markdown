---
published: true
title: Creating a Self-Signed SSL Certificate
layout: post
tags: [certificate,linux,signed,self-signed]
categories: [linux,certificate]
permalink: /2015/09/creating-a-self-signed-ssl-certificate/
---
```
openssl genrsa -des3 -passout pass:x -out server.pass.key 2048
openssl rsa -passin pass:x -in server.pass.key -out server.key
rm server.pass.key
openssl req -new -key server.key -out server.csr

openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt
```
