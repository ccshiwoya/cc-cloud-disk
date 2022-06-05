
    	分布式网络云盘cloud-disk

### 项目环境
* Ubuntu 16.04
* Qt（windows， 5.15.2 MinGW 64-bit）

===============

一、特点如下：
------------
1、使用Nginx作为代理服务器，将动态请求转发给后台的FastCGI程序进行进行处理；

2、使用FastDFS分布式文件系统保存用户文件，并配置Nginx模块实现快速下载；

3、使用MySQL保存用户和文件信息，Redis保存客户端令牌等信息；

4、Qt作为云盘客户端，实现用户登录、注册，文件上传、快传、下载、删除、共享、转存等功能。

二、启动准备：
------------

1、部署 MySQL 数据库、 Redis 数据库

* 安装 mysql-server + mysql-client + libmysqlclient-dev；

* 运行 mysqlscript 目录下的 clound_disk.sql 脚本，创建数据库 和 相关表；

* 安装 Redis + Hiredis 库。

2、部署 FastDFS 集群

* 安装 FastDFS  和 libfastcommon 程序库；

* 在家目录创建 fastdfs 文件夹，存放集群所有内容；
* .
├── client
├── storage
└── tracker

* 配置 /etc/fdfs 下的 tracker.conf、storage.conf、client.conf  文件；（配置可参考 \server\conf 中的文件，配置前先备份）

3、配置 Nginx

* 安装 Nginx + PCRE库 + zlib库 + OpenSSL开发库，配置、编译、安装；

* 向 Nginx 中编译 fastdfds-nginx-module 模块，可以通过Nginx访问FastDFS；

* 向 Nginx 中编译 ngx_http_fastcgi_module 模块，使得 Nginx 将接收到的请求转发给后台 FastCGI 进行处理；

* 搭建 FastCGI 程序运行环境：编译与安装 cgi 开发库，安装 FasiCGI 进程管理器 spawn-fcgi；

* 配置 /usr/local/nginx/conf 下的 nginx.conf 文件；（配置可参考 /server/conf/nginx.conf，配置前先备份）

4、服务端部署（server 目录）

* 配置 conf/ 目录下的 cfg.json 文件；

* chmod 赋予所有脚本可执行权限；

* 输入命令编译服务端程序；
make clean
sudo ldconfig 
sudo make

* 编译服务端程序， ./start.sh 启动服务端；

5、客户端部署（client 目录）

* Qt Creator 打开 cloudDisk.pro ，启动客户端；


项目参考：
------------
[1] https://github.com/dongyusheng/cloud-disk
