# docker setup mysql
    docker search mysql
    docker pull mysql
    docker images
    docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql
    --name 指定名称 
    -p 指定宿主机:容器端口映射
    -d 后台运行
    