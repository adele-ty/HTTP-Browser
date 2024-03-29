GET和POST请求的差异主要表现在以下几个方面：  

- 请求方式：  
GET请求是通过将参数附加到URL后面的方式进行数据传输，例如：http://example.com/api?key=value。  
POST请求是将参数放在HTTP请求体（request body）中进行数据传输。  

- 数据长度：  
GET请求的参数长度受限于浏览器和服务器的约束，一般限制在2000字符以内。  
POST请求中，数据长度的限制更大，通常受服务器接收数据大小限制的约束，可以传输大量数据。  

- 数据类型：  
GET请求仅支持ASCII字符集的文本数据传输。  
POST请求支持多种数据类型，例如表单数据、二进制文件数据等。  

- 缓存和收藏：  
GET请求的URL可以被缓存和收藏，POST请求无法缓存和收藏。  

  GET请求的URL包含了请求所需的所有信息，浏览器、代理服务器等可以根据URL进行缓存。当相同URL的请求发生时，缓存机制可以直接从缓存中获取结果，提高响应速度。浏览器收藏夹可以存储URL，用户可以方便地保存和访问GET请求的URL。  

  当浏览器收藏一个POST请求时，由于请求体中的数据不能被收藏，重复提交这个请求可能会导致错误或数据丢失。因此，浏览器并不支持收藏POST请求。POST请求无法被缓存，因为缓存机制主要基于URL。由于POST请求的数据在请求体内，浏览器无法仅根据URL来识别请求，从而无法实现缓存。

- 安全性和隐私：  
GET请求的数据直接附加在URL后面，具有相对较低的安全性和隐私性，不适合传输敏感信息。  
POST请求的数据在请求体内，相对来说具有较高的安全性，适用于传输一些隐私信息。  

- 浏览器回退：  
GET在浏览器回退时是无害的，而POST会再次提交请求。  

  GET请求在浏览器回退时是无害的，因为它们是幂等的，不会修改服务器数据。而POST请求在回退操作中可能会再次提交，因为它们涉及到数据改变，导致副作用。  

- 数据包数量：  
GET产生一个TCP数据包，POST产生两个TCP数据包。  

  对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；
  而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。  

  然而，在实际应用中，HTTP/1.1协议默认启用了持久连接（persistent connections），可以通过单个TCP连接发送多个请求。此外，很多现代浏览器也使用了“请求合并”技术，将GET或POST请求的多个TCP数据包合并为一个或几个TCP数据包。这使得实际情况无法简单地将GET请求和POST请求的TCP数据包数量确定为一个或两个。  

**GET和POST本质上就是TCP链接，并无差别。但是由于HTTP的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同。**

参考[99%的人都理解错了HTTP中GET与POST的区别](https://mp.weixin.qq.com/s?__biz=MzI3NzIzMzg3Mw%3D%3D&mid=100000054&idx=1&sn=71f6c214f3833d9ca20b9f7dcd9d33e4)
