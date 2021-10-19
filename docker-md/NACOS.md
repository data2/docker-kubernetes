docker pull nacos/nacos-server

# 单机模式
docker run --name nacos-standalone -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:latest

打开控制台
http://127.0.0.1:8848/nacos/index.html
默认登陆账号密码均为:nacos

此模式在docker容器停止后,在nacos配置的数据会丢失
下面介绍将数据保存到mysql数据库中

# 单机数据库

1\首先需要启动一个mysql新建数据库,我这边新建数据库取名叫:nacosConf

2\初始化数据库

https://github.com/alibaba/nacos/blob/master/distribution/conf/nacos-mysql.sql

3\执行命令

docker run --name nacos-standalone-mysql -e MODE=standalone \
--link mysql57:db \
-e SPRING_DATASOURCE_PLATFORM=mysql \
-e  MYSQL_SERVICE_HOST=db \
-e MYSQL_SERVICE_PORT=3306 \
-e MYSQL_SERVICE_DB_NAME=nacosConf \
-e MYSQL_SERVICE_USER=root \
-e MYSQL_SERVICE_PASSWORD=123 \
-p 8848:8848 -d nacos/nacos-server:latest 

