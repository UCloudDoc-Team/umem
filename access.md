# 实例访问



出于安全性考虑，云内存Memcache实例仅能在内网进行访问，以Memcache协议为例简述如何访问云内存Memcache实例。

## telnet访问

```
telnet 127.0.0.1 11211
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
add id 1 0 4
1234
STORED 
get id
VALUE id 1 4
1234
END
delete id
DELETED
```

## php访问

``` php
<?php
    $memcache = new Memcache;
    $memcache->connect('10.4.7.17', 11211);
    $key = "testkey";
    $tvalue = "testvalue";
    $memcache->set($key, $tvalue, false, 10);
    $nvalue = $memcache->get($key);
    print_r($nvalue . "\n");
?>
```

## Python访问示例

``` python
#!/usr/bin/env python2
# coding=utf8

import sys, os
import time
import memcache

if __name__ == "__main__":

    ip = '10.4.7.17'
    port = 11211

    addr = "%s:%d" % (ip , port)
    mc = memcache.Client([addr], debug=0)

    key = 'testkey'
    tvalue = "testvalue"
    mc.set(key, tvalue)
    nvalue = mc.get(key)
    print nvalue
```
