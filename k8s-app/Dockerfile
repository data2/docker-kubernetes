FROM openjdk:8-jdk-alpine
ENV TZ=Asia/Shanghai
COPY k8s-app-0.0.1-SNAPSHOT.jar /opt/k8s-app-0.0.1-SNAPSHOT.jar
COPY run.sh /opt/run.sh

EXPOSE 8089
ENTRYPOINT ["/bin/sh", "/opt/run.sh"]


