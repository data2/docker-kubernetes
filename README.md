# docker
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
```

# minio

docker pull  minio/minio


docker run -p 9000:9000 -p 9001:9001 --name minio -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /home/soft/minio/data:/data   -v /home/soft/minio/config:/root/.minio minio/minio server /data --console-address ":9001"


# redis

docker pull  redis

# nginx

yum install nginx
