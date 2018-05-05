title: Spider学习笔记
date: 2015-12-02 20:43:42
tags: [spider, notes]
---
### import urllib.request
[import urllib.request](https://docs.python.org/3/library/urllib.request.html#module-urllib.request) -a urllib.request module uses HTTP/1.1 and includes Connection:close header in its HTTP requests.

`urllib.request.urlopen(url, data=None, [timeout, ]*, cafile=None, capath=None, cadefault=False, context=None)`
返回http.client.HTTPResponse 对象
也可以作为`context manager`有以下方法

1. geturl() — 返回资源检索网址，经常用来检查是否有**重定向**
2. info() — 返回**meta-information**例如 headers
3. getcode() –  返回HTTP **status code**
<!--more-->
#### HTTPResponse 对象
[httpresponse-objects](https://docs.python.org/3/library/http.client.html#httpresponse-objects)
`.read()`
`.readinto(b)`
`getheader('User-Agent')` -返回‘User-Agent’中内容
`getheaders()`
.............


`url` -可以是string或Request对象
`data` -
`timeout` -以秒为单位用于停止连接尝试

`class http.client.HTTPResponse(sock, debuglevel=0, method=None, url=None)`

### class urllib.request.Request
[urllib.request.Request](https://docs.python.org/3/library/urllib.request.html?highlight=urllib.request.request#urllib.request.Request)

### urllib.parse.urlencode
`urllib.parse.urlencode(query, doseq=False, safe='', encoding=None, errors=None, quote_via=quote_plus)` 
-将一个可能含有字符串或字节对象的mapping或包含多个由两个元素组成的元组的序列，转换成**ASCII文本字符串**
如果得到的字符串被作为data以urlopen()函数用于POST操作，该字符串因为被编码成**bytes**，否则会引起TypeError错误
### deque
`from collections import deque` -[deque](https://docs.python.org/3/library/collections.html?highlight=deque#collections.deque)
`append(x) appendleft(x) clear()`
`copy()` -Create a shallow copy of the deque.
`count(x)` -统计队列中x的个数
`extend(iterable) extendleft(iterable) index(x[,start[,stop]]) insert(i,x)`
`pop() popleft()` -会引起IndexError错误
`remove(value)` -删除第一个value值，会引起ValueError错误.
`reserve() rotate(n)`
### set
`set` -[set](https://docs.python.org/3/library/stdtypes.html?highlight=set#set)