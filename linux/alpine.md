# alpine用户创建和管理

https://blog.csdn.net/qq_41980563/article/details/88897088

**创建用户组用addgroup**

```
addgroup -g 1000 -S redis
```



**创建用户用adduser**

```
adduser redis -D -G redis -u 1000 -s /bin/sh
```



**切换用户**

```
# su bh
# exit
# whoami
```

