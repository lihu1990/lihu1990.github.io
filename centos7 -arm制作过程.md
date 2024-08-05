# centos7 -arm制作过程

## 在线拉取母盘操作系统arm64v8/centos:7

   ```shell
   docker pull arm64v8/centos:7
   ```

   

## 启动母盘系统

```shell
docker run  --privileged -it -d --name centos01 arm64v8/centos:7  /usr/sbin/init
```

## 进入母盘容器，安装必须插件

```shell
sleep 10s
#进入容器 （注意最好使用国内的yum源https://developer.aliyun.com/mirror/  注意这里是arm版本的哦）
docker exec -i centos01 bash
#开始安装jdk、unzip、net-tools、sudo、wget、curl
yum install -y java-1.8.0-openjdk
yum install -y unzip
yum install -y net-tools
yum install -y sudo
yum install -y wget
yum install -y curl
```

