


docker run -p 9000:9000 -p 9001:9001 --name minio -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /home/soft/minio/data:/data   -v /home/soft/minio/config:/root/.minio minio/minio server /data --console-address ":9001"

docker run -p 19000:9000 -p 19001:9001 --name minio2 -e "MINIO_ROOT_USER=admin"  -e "MINIO_ROOT_PASSWORD=admin123456" -v /home/soft/minio2/data:/data   -v /home/soft/minio2/config:/root/.minio minio/minio server /data --console-address ":9001"

docker run -p 9000:9000 -p 9001:9001 --name minio -e "MINIO_ROOT_USER=admin" -e "MINIO_ROOT_PASSWORD=admin123456" -v /home/data/minio/data:/data -v /home/soft/minio/config:/root/.minio minio/minio server /data --console-address ":9001"
