FROM openjdk:8-jdk-alpine
VOLUME /tmp
ARG JAR_FILE
ADD ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-Dspring.datasource.password=changeme","-Dclientsecret=uaaXpertsecret","-Dlogin.clientsecret=adminsecret","-Dspring.datasource.url=jdbc:mysql://db:3306/comm?autoReconnect=true&useUnicode=true&characterEncoding=utf8","-Dspring.redis.host=redis","-Duaa.endpoint=http://uaa:8080/uaa","-jar","/app.jar"]
