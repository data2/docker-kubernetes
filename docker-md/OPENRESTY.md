
# openresty

               ```
docker search openresty
docker pull openresty/openresty
非挂载
docker run --name first-openresty -p 82:80 openresty/openresty

挂载配置文件
mkdir  /Users/leewow/openresty/
docker cp first-openresty:/usr/local/openresty/nginx/conf/ ./conf/
docker cp first-openresty:/usr/local/openresty/nginx/html/ ./html/
docker cp first-openresty:/usr/local/openresty/nginx/logs/ ./logs/

docker cp first-openresty:/etc/nginx/conf.d/  ./conf.d/
```

# 启动

```
docker run --name first-openresty -p 83:80  \
-v /Users/leewow/openresty/conf/nginx.conf:/usr/local/openresty/nginx/conf/nginx.conf  openresty/openresty
```

# docker-compose 启动

docker-compose。yml

```
version: '3'
services:
  minio:
    image: openresty/openresty
    container_name: resty
    hostname: "resty"
    environment:
      TZ: Asia/Shanghai
    privileged: true
    volumes:
      - ./conf.d:/root/soft/openresty-docker/conf
      - ./html:/root/soft/openresty-docker/html
      - ./logs:/root/soft/openresty-docker/logs
    ports:
      - 8080:80
```

docker-compose  up -d


