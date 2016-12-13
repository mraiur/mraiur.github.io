---
published: true
title: CasperJS + Reactjs
layout: post
tags: [casperjs,javascript,unit-testing,phantomjs]
categories: [casperjs,javascript]
permalink: /2015/07/casperjs-reactjs/
---
There where two problems with the current latest casperjs(1.1.0-beta3), phantomjs(v1.9.17) and reactjs.

I have several hours of fiddeling until i found a working solution.

The problems:

1. PhantomJS has no funciton.bind prototype and its required for build version of React.
2. Also there where infinite errors for:

{% highlight javascript %}
Unsafe JavaScript attempt to access frame with URL about:blank from frame with URL file:///usr/lib/node_modules/casperjs/bin/bootstrap.js. Domains, protocols and ports must match.
{% endhighlight %}

The solution for problem 1 is:

{% highlight javascript %}
casper.on('page.initialized', function() {
        casper.evaluate(function() {
            var isFunction = function(o) {
                return typeof o == 'function';
            };

            var bind,
                slice = [].slice,
                proto = Function.prototype,
                featureMap;

            featureMap = {
                'function-bind': 'bind'
            };

            function has(feature) {
                var prop = featureMap[feature];
                return isFunction(proto[prop]);
            }

            // check for missing features
            if (!has('function-bind')) {
                // adapted from Mozilla Developer Network example at
                // https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function/bind
                bind = function bind(obj) {
                    var args = slice.call(arguments, 1),
                        self = this,
                        nop = function() {
                        },
                        bound = function() {
                            return self.apply(this instanceof nop ? this : (obj || {}), args.concat(slice.call(arguments)));
                        };
                    nop.prototype = this.prototype || {}; // Firefox cries sometimes if prototype is undefined
                    bound.prototype = new nop();
                    return bound;
                };
                proto.bind = bind;
            }
        });
    });
{% endhighlight %}

[Source](https://www.snip2code.com/Snippet/499383/Casperjs-bind-polyfill)


And the solution for problem two at the moment is to downgrade the phantomjs version:

```
sudo npm -g install phantomjs@1.9.7-15
```

[Source](http://dexpage.com/unsafe-javascript-attempt-to-access-in-capserjs-duplicate/)
