
> 最近由于公司这边代码仓库也放在github上，而且要求用公司对应的账户登录，所以遇到了git提交代码时候两个github账号切换的问题。



### First

先看一下我原来的ssh config里面github相关的配置入如下图：

```
Host github.com
HostName github.com
IdentityFile ~/.ssh/id_rsa
User git
```

目前是只有一个默认的github账户的情况下。



### Second

下面要在ssh新增一个配置：

```
Host xxxx
HostName github.com
IdentityFile ~/.ssh/id_rsa_xxxx
User git
```

注意这里的**Host**随便起的。



### Third

配置完ssh config之后，需要把用下面密钥配置的仓库重新设置一下 origin url;



```
git remote -v
```

查看一下你原来的url,例如原来的url git@github.com:feivorid/aaaaaa.git，那么需要设置为

```
git remote origin set-url git@xxxx:feivorid/aaaaaa.git
```

注意：这里的xxxx为第二个ssh 配置的host；

设置完之后就可以正常push pull 代码了！

