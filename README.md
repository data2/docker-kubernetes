# nacos
```
docker run -d  --name nacos  -p 8848:8848  -p 9848:9848   -p 9849:9849   --restart=always -e MODE=standalone  -e PREFER_HOST_MODE=hostname  -e NACOS_AUTH_USERNAME=nacos -e NACOS_AUTH_PASSWORD=jsDp@kfb=.  -v D:\volume\nacos\data:/home/nacos/data -v D:\volume\nacos\logs:/home/nacos/logs -v D:\volume\nacos\conf:/home/nacos/conf nacos/nacos-server
```
