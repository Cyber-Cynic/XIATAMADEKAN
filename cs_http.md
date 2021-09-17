## HTTP状态码
https://http.cat/

## HTTPS
1. 双方使用HTTP明文通信
> 中间人窃听，不能忍

2. 我们协定一个密码，把通信内容加密
> 加密解密用的同一个密钥，对称加密。问题是如何安全地传递这个密钥，总不能面对面的去告诉吧

3. 既然对称加密不行，那么就使用非对称加密
> 用公钥加密传输后使用私钥解密，但是 1.依然存在中间人问题 2.每次这么处理，速度有些慢

4. 中间人问题其实就是怎么证明“你是你”，怎么证明这个公钥就是你的公钥
> 引入CA。  
具体流程如下：    
1.服务器管理员向CA机构申请公钥  
2.CA机构确认身份后，对申请的公钥做签名（用CA私钥签），并将公钥+签名放入证书  
3.服务器将数字证书发到客户端，客户端使用CA（操作系统或者客户端内置）的公钥对证书签名进行验证 

5. 所以所谓的证书，全名叫做“服务器的公开密钥证书”，里面存放服务器的公钥和CA对其的签名

6. 速度慢的问题可以使用对称加密+非对称加密解决

## URL组成
URI = scheme:[//authority]path[?query][#fragment]  
authority = [userinfo@]host[:port]

![URL](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/URI_syntax_diagram.svg/1920px-URI_syntax_diagram.svg.png)

https://en.wikipedia.org/wiki/URL

