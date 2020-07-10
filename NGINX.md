# NGINX
  docker search nginx
  docker pull nginx
  
  非挂载方式
  docker run --name first-nginx -p 81:80 nginx
  curl localhost:81
  
  如果修改nginx配置，需要进入到容器内部 
  docker exec -it first-nginx bash 
  vi /etc/nginx/nginx.conf
  
  挂载方式
  
