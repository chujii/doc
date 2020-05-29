**查看一级目录大小**

du -h --max-depth=1

**清理系统日志**

删除已归档的日志文件，直到它们使用的磁盘空间低于100M：

sudo journalctl --vacuum-size=100M

