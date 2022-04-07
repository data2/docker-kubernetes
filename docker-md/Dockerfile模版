# 指定基础镜像  基于centos镜像
FROM centos

# Maintainer  作者信息
MAINTAINER test test@example.com

# 安装一些依赖的包
RUN yum install -y pcre-devel wget net-tools gcc zlib zlib-devel make openssl-devel

# 安装nginx
ADD http://nginx.org/download/nginx-1.8.0.tar.gz .  # 添加nginx的压缩包到当前目录下

# 解包 创建nginx目录 编译安装 删除自带的nginx配置文件
RUN tar zxvf nginx-1.8.0.tar.gz   && \
	mkdir -p /usr/local/nginx   && \
	cd nginx-1.8.0 && ./configure --prefix=/usr/local/nginx && make && make install   && \ 
	rm -fv /usr/local/nginx/conf/nginx.conf 

# 添加nginx配置文件
ADD http://www.apelearn.com/study_v2/.nginx_conf /usr/local/nginx/conf/nginx.conf  

# 开放80端口
EXPOSE 80

# 这里是因为防止服务启动后容器会停止的情况，所以需要多执行一句tail命令
ENTRYPOINT /usr/local/nginx/sbin/nginx && tail -f /etc/passwd
