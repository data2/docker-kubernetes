# docker setup mysql
docker search mysql
docker pull mysql
docker images
docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql
