---
published: true
title: Setup PHPUnit
layout: post
tags: [php,tools]
categories: [php,tools]
permalink: /2013/04/setup-phpunit/
---
Its plain simple but better to describe the process.

Normally if you have pear installed is enough to install with:

```
pear channel-discover pear.phpunit.de
```

But if you got something like this:

```
invalid package name/package file "pear.phpunit.de/PHPUnit"
```

for this you must register the channel:

```
pear channel-discover pear.phpunit.de
```

And finish with installing PHPUnit

```
pear install pear.phpunit.de/PHPUnit
```

Here is an example test case with init at the bottom to test in browser:

```
require_once 'PHPUnit/Autoload.php';

class OutputTest extends PHPUnit_Framework_TestCase
{
    public function testExpectFooActualFoo()
    {
        $this->expectOutputString('foo');
        print 'foo';
    }

    public function testExpectBarActualBaz()
    {
        $this->expectOutputString('bar');
        print 'baz';
    }
}

$test = new OutputTest();
$test->testExpectFooActualFoo();
```



Great way to show and run your test in browser:
[https://github.com/NSinopoli/VisualPHPUnit](https://github.com/NSinopoli/VisualPHPUnit)
