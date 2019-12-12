jenkins: https://blog.csdn.net/PersonalM/article/details/103252143

jenkins+docker实现自动编译、打包、构建镜像、容器部署
https://blog.csdn.net/xiaoxiangzi520/article/details/88842200

自动化部署之jenkins发布PHP项目
https://blog.csdn.net/weixin_33724046/article/details/89866598

jenkins教程发布PHP代码
https://blog.csdn.net/tianyaopen/article/details/92616248

Jenkins自动化构建vue项目然后发布到远程Linux服务器
https://www.cnblogs.com/djlsunshine/p/11059690.html
https://segmentfault.com/a/1190000020868116?utm_source=tag-newest
https://segmentfault.com/a/1190000018678157
https://blog.csdn.net/jonsonler/article/details/81317352

jenkins 权限控制插件 Role-based Authorization Strategy
https://blog.csdn.net/wanglei_storage/article/details/78339409

docker run -u root --name="jenkins" -d -p 8080:8080 -p 50000:50000 -v /alidata/docker/jenkins/jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkinsci/blueocean

//jenkins插件
https://updates.jenkins-ci.org/download/plugins/

//设置时区
System.setProperty('org.apache.commons.jelly.tags.fmt.timeZone', 'Asia/Shanghai')
//永久设置时间，取用添加启动脚本
https://www.jianshu.com/p/47d767cf893d

```
echo $PATH
node -v
npm -v
npm install
npm run build
```



node: not found
即使在PATH中找到了二进制文件并且该二进制文件是可执行文件，Alpine也无法运行：
发生这种情况是因为图像不包含libstdc++.so.6nodejs所需的图像：
换句话说，node: not found并不意味着node未安装（它是可执行文件，可以在中找到$PATH）。
这意味着node找不到依赖项之一。
我已经通过输入容器然后直接安装节点解决了这个问题,统一安装了依赖，其它版本也可以用
apk add --no-cache nodejs
https://stackoverflow.com/questions/43307107/jenkins-nodejsplugin-node-command-not-found

Gitlab web hook,404地址问题
仍可正常推送