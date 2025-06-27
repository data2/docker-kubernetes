# ftp服务器

```
docker run -d -v /home/lighthouse:/home/vsftpd -p 20:20 -p 21:21 -p 21100-21110:21100-21110 -e FTP_USER=test -e FTP_PASS=test --name vsftpd fauria/vsftpd
```

# ollama deepseek
```

CPU模式
docker run -d -p 11434:11434 -v /d/volume/ollama:/root/.ollama --name ollama ollama/ollama

GPU模式
docker run --gpus=all -d -p 11434:11434 -v /data/ollama:/root/.ollama --name ollama ollama/ollama

docker exec -it ollama /bin/bash

ollama pull deepseek-r1:8b

curl http://localhost:11434/api/generate -d '{"model": "deepseek-r1:8b", "stream": false, "prompt": "你好"}'
```
# linux - conda -pytorch

```
wget https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Linux-x86_64.sh
sh Anaconda3-2024.10-1-Linux-x86_64.sh
vi ~/.bashrc
export PATH="$HOME/miniconda3/bin:$PATH"
source ~/.bashrc
conda config --remove-key channels
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2/
conda config --add channels defaults
conda config --set show_channel_urls yes
conda create -n pytorch-env python=3.10
conda activate pytorch-env
#conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
#conda install pytorch==2.5.1 torchvision torchaudio cudatoolkit=11.3 -c pytorch
conda install pytorch==2.1.0 torchvision==0.16.0 torchaudio==2.1.0 pytorch-cuda=12.1 -c pytorch -c nvidia

python -c "import torch; print(torch.__version__)"

pip install opencv-contrib-python==4.11.0.86
pip install scikit-learn==1.6.1
pip install matplotlib==3.9.2
pip install
pip install
pip install
pip install
pip install 

```

# docker
## yum 安装
```
yum install docker

vi /etc/docker/daemon.json

{
"registry-mirrors": [
	"https://do.nark.eu.org",
   "https://dc.j8.work",
   "https://docker.m.daocloud.io",
   "https://dockerproxy.com",
   "https://docker.mirrors.ustc.edu.cn",
   "https://docker.nju.edu.cn"
]
}

sudo systemctl start docker

```

## unbuntu snap 安装 

```
/var/snap/docker/current/config/daemon.json

{
    "log-level": "error",
    "storage-driver": "overlay2",
    "registry-mirrors": [
        "https://do.nark.eu.org",
        "https://dc.j8.work",
        "https://docker.m.daocloud.io",
        "https://dockerproxy.com",
        "https://docker.mirrors.ustc.edu.cn",
        "https://docker.nju.edu.cn"
    ]
}
sudo snap restart docker
```

# nacos
```
docker pull nacos/nacos-server

docker run -d  --name nacos  -p 8848:8848  -p 9848:9848   -p 9849:9849   --restart=always -e MODE=standalone  -e PREFER_HOST_MODE=hostname  -e NACOS_AUTH_USERNAME=nacos -e NACOS_AUTH_PASSWORD=jsDp@kfb=.  -v D:\volume\nacos\data:/home/nacos/data -v D:\volume\nacos\logs:/home/nacos/logs -v D:\volume\nacos\conf:/home/nacos/conf nacos/nacos-server

docker run -d  --name nacos  -p 8848:8848  -p 9848:9848   -p 9849:9849
--restart=always -e MODE=standalone
-e PREFER_HOST_MODE=hostname
-e NACOS_AUTH_USERNAME=nacos
-e NACOS_AUTH_PASSWORD=jsDp@kfb=.
-v D:\volume\nacos\data:/home/nacos/data
-v D:\volume\nacos\logs:/home/nacos/logs
-v D:\volume\nacos\conf:/home/nacos/conf
nacos/nacos-server

缺少nacos-logback.xml, 可以本地目录conf新建文件


<?xml version="1.0" encoding="UTF-8"?>
<!-- Logback configuration. See http://logback.qos.ch/manual/index.html -->
<configuration scan="true" scanPeriod="60 seconds" debug="false">

    <property name="LOG_PATH" value="./logs"/>
    <include resource="org/springframework/boot/logging/logback/defaults.xml"/>
    <include resource="org/springframework/boot/logging/logback/console-appender.xml"/>
    <jmxConfigurator/>

    <appender name="DAILY_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <encoder>
            <pattern>${FILE_LOG_PATTERN}</pattern>
        </encoder>
        <file>${LOG_PATH}/nacostest.log</file>
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <fileNamePattern>${LOG_PATH}/nacostest-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <!-- 文件大小触发重写新文件 -->
            <maxFileSize>100MB</maxFileSize>
            <!-- 日志文件保留天数 -->
            <maxHistory>15</maxHistory>
            <totalSizeCap>20GB</totalSizeCap>
        </rollingPolicy>
    </appender>
    <appender name="ERROR_FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
            <level>ERROR</level>
        </filter>
        <file>${LOG_PATH}/nacostest-error.log</file>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <fileNamePattern>${LOG_PATH}/nacostest-error-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>100MB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
            <maxHistory>15</maxHistory>
            <totalSizeCap>20GB</totalSizeCap>
        </rollingPolicy>
        <layout class="ch.qos.logback.classic.PatternLayout">
            <pattern>${FILE_LOG_PATTERN}</pattern>
        </layout>
    </appender>

    <root level="INFO">
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="DAILY_FILE"/>
        <appender-ref ref="ERROR_FILE"/>
    </root>

</configuration>
```
# MYSQL
```
docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=123456  -v D:\volume\mysql:/var/lib/mysql -d mysql:latest


```


# minio
```
docker pull  minio/minio

docker run -d  -p 9000:9000 -p 9001:9001 --name miniodata -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /mnt/miniodata:/data   -v /mnt/minioconfig/config:/root/.minio minio/minio server /data --console-address ":9001"

docker run -p 9000:9000 -p 9001:9001 --name minio -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /home/soft/minio/data:/data   -v /home/soft/minio/config:/root/.minio minio/minio server /data --console-address ":9001"

docker run -d  -p 9000:9000 -p 9001:9001 --name miniodata -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /mnt/miniodata:/data   -v /mnt/minioconfig/config:/root/.minio minio/minio:RELEASE.2022-10-24T18-35-07Z server /data --console-address ":9001"
```

# redis
```
docker pull  redis

# nginx

yum install nginx

systemctl start nginx

 /usr/sbin/nginx
 
 /etc/nginx/nginx.conf
 
 /usr/share/nginx/html
 
 firewall-cmd --zone=public --add-port=80/tcp
```

# nginx

```

docker run --name nginx -d -v D:\\volume\\nginx:/etc/nginx -p 8080:80 -d nginx:stable-alpine3.20-perl

docker run -d \
    --name nginx \
    -p 80:80 \
    -v D:\\volume\\nginx\\conf:/etc/nginx/conf.d \
    -v D:\\volume\\nginx\\logs:/var/log/nginx \
    -v D:\\volume\\nginx\\html:/usr/share/nginx/html \
    nginx:stable-alpine3.20-perl

获取nginx配置
docker run --name testnginx -p 8080:80 nginx:stable-alpine3.20-perl
docker cp testnginx:/etc/nginx D:\\volume

```

# webrtc-streamer


```

docker run -d -p 8000:8000 --cpus=".5" -it mpromonet/webrtc-streamer -o

docker pull mpromonet/webrtc-streamer

docker run -p 8000:8000 -it mpromonet/webrtc-streamer

```


