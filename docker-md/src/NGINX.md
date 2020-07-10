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
    在宿主机上建挂载使用的文件夹
    mkdir -p /leewow/{conf,conf.d,html,logs} 
    如果有需要 ，从容器复制文件出来
    docker cp 3b17bd0db8db:/etc/nginx/nginx.conf /leewow/conf/nginx.conf
    docker cp 3b17bd0db8db:/etc/nginx/conf.d/default.conf /leewow/conf.d/default.conf
    
    启动
    docker run --name second-nginx -p 81:80 -v /leewow/html:/usr/share/nginx/html -v /leewow/conf/nginx.conf:/etc/nginx/nginx.conf -v /leewow/conf.d/default.conf:/etc/nginx/conf.d/default.conf -v /leewow/logs:/var/log/nginx nginx
    
      
