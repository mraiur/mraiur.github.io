---
published: true
title: Primer Numbers
layout: post
tags: [algorithms]
categories: [algorithms,euler]
permalink: /2013/07/primer-numbers/
---

```
function isPrime(number){
    while(number &gt; 0 ) {
        if(number%2===0 || number%3===0){
            return false;
        }else{
            return true;
        }
        number--;
    }
    if( number === 0){
        return false;
    }
    return true;
}

function nextPrime(number) {
    number++;
    while(number &gt; 0 ) {
        if(number%2!==0 &amp;&amp; number%3!==0){
            return number;
        }
        number++;
    }
}
```
