**以alpine镜像为基础将go应用部署在docker中**

https://www.jianshu.com/p/77293a891fee

```undefined
docker build -f golang/Dockerfile -t mygo11 .
docker run -d -p 9004:9000 mygo11
```