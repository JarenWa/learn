
# Ubuntu
 Ubuntu 系统中，root 用户拥有执行任何命令的权限。不需要前缀 sudo。

 在运行 `apt-get install` 之前运行 `apt-get update` 是个好习惯，这确保了软件包列表是最新的。


# Docker 
菜鸟教程<https://www.runoob.com/docker/docker-tutorial.html>


直接输入 docker 命令来查看到 Docker 客户端的所有命令选项

## 镜像
```
docker pull ubuntu
```

## 容器
启动容器   置于后台 -d
```
docker run -itd --name ubuntu-test ubuntu /bin/bash
```
进入容器 镜像名后的是命令，这里我们希望有个交互式 Shell，因此用的是 /bin/bash。
```
docker exec -it 243c32535da7 /bin/bash
```


