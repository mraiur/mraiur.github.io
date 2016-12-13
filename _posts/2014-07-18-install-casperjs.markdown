---
published: true
title: Install CasperJS
layout: post
tags: [linux,javascript,unit-testing]
categories: [linux,javascript]
permalink: /2014/07/install-casperjs/
---
First to install nodejs and npm.
On Ubuntu Server 14.04 i had to install via


```
 sudo apt-get install python-software-properties
 sudo add-apt-repository ppa:chris-lea/node.js
 sudo apt-get update
 sudo apt-get install nodejs
```

Next install phantom:

```
sudo apt-get update
sudo apt-get install build-essential chrpath git-core libssl-dev libfontconfig1-dev
git clone git://github.com/ariya/phantomjs.git
cd phantomjs
git checkout 1.9
./build.sh
```

Then instal CapserJS via npm:

```
npm install -g casperjs
```
