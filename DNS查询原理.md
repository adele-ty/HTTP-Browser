# DNS查询原理
* DNS查询：输入域名，浏览器就会在后台，自动向 DNS 服务器发出请求，获取对应的 IP 地址。  
* 域名结构：是一个树状结构，最顶层的域名是根域名（root），然后是顶级域名（top-level domain，简写 TLD），再是一级域名、二级域名、三级域名。  
以es6.ruanyifeng.com为例  
1. 根域名：所有域名的起点都是根域名，它写作一个点.，放在域名的结尾。  
2. 顶级域名：根域名的下一级是顶级域名。它分成两种：通用顶级域名（gTLD，比如 .com 和 .net）和国别顶级域名（ccTLD，比如 .cn 和 .us）。  
3. 一级域名：一级域名就是你在某个顶级域名下面，自己注册的域名。比如，ruanyifeng.com就是在顶级域名.com下面注册的。  
4. 二级域名：二级域名是一级域名的子域名，是域名拥有者自行设置的，不用得到许可。比如，es6 就是 ruanyifeng.com 的二级域名。  
* 域名的逐级查询：  
这种树状结构的意义在于，只有上级域名，才知道下一级域名的 IP 地址，需要逐级查询。每一级域名都有自己的 DNS 服务器，存放下级域名的 IP 地址。  
* 递归查询  
递归DNS服务器，ip地址为1.1.1.1，把分步骤的查询过程自动化，一次性获得结果。  
它内部有缓存，可以保存以前查询的结果，下次再有人查询，就直接返回缓存里面的结果。所以它能加快查询，减轻源头 DNS 服务器的负担。  

参考[DNS查询原理](https://www.ruanyifeng.com/blog/2022/08/dns-query.html) 