# docker setup mysql
    docker search mysql
    docker pull mysql
    docker images
    docker rmi 70891d021f2b
    删除镜像
    
    docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql
    --name 指定名称 -p 指定宿主机:容器端口映射 -d 后台运行
    docker start e95a3a9c2487 
    docker stop e95a3a9c2487
    
    docker ps 
    docker ps -a 
    可以查看暂停的容器
    docker kill first-mysql
    docker kill 70891d021f2b
    docker rm first-mysql
    
    docker exec -it  first-mysql  bash 
    进入容器内部
    mysql -u root -p
    
    /usr/local/mysql/bin/mysql -h localhost -P 3307 -uroot -p
