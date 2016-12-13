---
published: true
title: Compare records
layout: post
tags: [php,mysql]
categories: [php,mysql]
permalink: /2013/06/compare-records/
---
Yesterday a colleague was struguling how to compare many fields and many records as a "unit test".
A simple solution came up in my mind and i worked.

Gel all the data using GROUP_CONCAT( field1, field2, etc ) as concat_fields

```
SELECT GROUP_CONCAT( field1, field2) as concatString FROM companies
```

After that get it with PHP and md5 on concatString and here is 2-3 line for comparing many fields and records to check if there is a change.

```
$query = 'SELECT GROUP_CONCAT( field1, field2) as concatString FROM companies';

$result = mysql_query($query);

$data = mysql_fetch_assoc($result);

$hash = md5($data['concatString ']);
```

example output of $hash is something like : **59458e11692fec53eb1633d2dacf10f9**
