---
layout: post
title: memcached 常用命令
---

<br>
命令格式：
----------

`<command name> <key> <flags> <exptime> <bytes>`<br>
`<data block>`

参数说明：

| 字段 | 说明 |
|:------:|:------:|
| \<command name>	 | set/get/add/replace|
| \<key>	|查找关键字|
| \<flags> |客户机使用它存储关于键值对的额外信息|
| \<exptime> | 该数据的存活时间，0表示永远|
| \<bytes> | 存储字节数|
| \<data block> | 存储的数据块（可直接理解为key-value结构中的value）|


基本命令简介：
--------
**set** 设置foo的值为5，长度跟后面的值要一致，这里的flag是个自定义标志，只支持int类型，如foo已经存在，会更新老的值
返回值：成功返回STORED，失败返回 NOT_STORED

```
set foo 0 0 5
hello
STORED
```

**add** 只有不存在才会成功

**replace** 只有存在才会成功

**get** 获取foo的值,返回foo的flag，长度和值

```
get foo
VALUE foo 0 5
hello
END
```

**gets** 获取的值多个序号，是内部序号，如果该值变化过，则序号会变化


```
gets foo
VALUE foo 0 5 5
hello
END
```
**delete** 删除某个key, 成功返回DELETED

```
delete foo
DELETED
```
**cas** 当与传入的key存在，而且和传入的序列号一样，才会更新，否则不更新
返回值：序列号一样STORED，否则返回NOT_FOUND或者EXISTS

```
cas foo1 0 0 5 1
hello
NOT_FOUND
```

