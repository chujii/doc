**文档**

https://docs.gitlab.com/runner

**docker安装**

```
docker run -d --name gitlab-runner --restart always \
     -v /srv/gitlab-runner/config:/etc/gitlab-runner \
     -v /var/run/docker.sock:/var/run/docker.sock \
     gitlab/gitlab-runner:latest
```

**删除无效的runner**

gitlab-runner verify --delete --name xxx