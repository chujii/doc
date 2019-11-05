**docker run　新建容器** 

```
$ docker run -itd --name=demo centos:7 /bin/bash
```



**docker exec　进入容器**

```
$ docker exec -it demo /bin/bash
```





**FAQ**

win7下，挂载目录。需先目录挂载至虚拟机，选固定分配，自动挂载，重启后生效.