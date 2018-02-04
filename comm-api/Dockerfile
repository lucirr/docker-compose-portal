FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
ADD ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-Dspring.datasource.password=changeme","-Dclientsecret=adminsecret","-Dlogin.clientsecret=adminsecret","-Dspring.datasource.url=jdbc:mysql://db:3306/comm?autoReconnect=true&useUnicode=true&characterEncoding=utf8","-Dspring.redis.host=redis","-jar","/app.jar"]
