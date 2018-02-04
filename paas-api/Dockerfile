FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
ADD ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-Dspring.profiles.active=local","-Dspring.datasource.password=changeme","-Dspring.datasource.url=jdbc:mysql://db:3306/PaasXpertPortal?useSSL=false&useUnicode=true&characterEncoding=utf8","-Dspring.redis.host=redis","-jar","/app.jar"]
