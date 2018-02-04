## maven, git, docker, docker-compose, uaac install
```
$ sudo apt-get install maven

$ sudo apt-get install git

$ sudo apt-get install docker.io
$ sudo groupadd docker
$ sudo usermod -aG docker $USER

$ sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose

$ sudo apt-get install rubygems
$ gem install cf-uaac
```

## bosh-lite install

## uaa
* git clone
```
$ cd uaa
$ git clone https://github.com/cloudfoundry/uaa.git
$ git checkout 4.6.0
```
* uaa.yml (uaa/src/main/resources/uaa.yml) 추가
```
spring_profiles: mysql,default

database:
  driverClassName: org.mariadb.jdbc.Driver
  url: jdbc:mysql://db:3306/uaa
  username: root
  password: changeme
```
* login.yml 생성
```
$ cd uaa/src/main/resources
$ cp required_configuration.yml login.yml
```
* war 생성
```
$ ./gradlew manifests
```
* war 복사
```
$ cp uaa/build/libs/cloudfoundry-identity-uaa-4.6.0.war ../webapps
```

## uaaxpert-ui
* git clone
```
$ cd comm-web
$ git clone ...
```

## paasxpert-ui
```
$ cd paas-web
$ git clone ...
```

## uaaxpert-api
```
$ cd comm-api
$ git clone ...
$ mvn -Dmaven.test.skip=true package
```

## paasxpert-api
```
$ cd paas-api
$ git clone ...
$ mvn -Dmaven.test.skip=true package
```

## docker-compose 실행 (docker-compose.yml 위치한 디렉토리에서 실행)
* 최초실행
```
$ docker-compose up --build -d
```
* 실행
```
$ docker-compose up -d
```
* 확인
```
$ docker-compose ps
$
     Name                   Command               State                       Ports                     
--------------------------------------------------------------------------------------------------------
uaa_comm-api_1   java -Djava.security.egd=f ...   Up                                                    
uaa_db_1         docker-entrypoint.sh mysqld      Up      0.0.0.0:3306->3306/tcp                        
uaa_paas-api_1   java -Djava.security.egd=f ...   Up                                                    
uaa_redis_1      docker-entrypoint.sh redis ...   Up      6379/tcp                                      
uaa_uaa_1        /opt/tomcat/bin/catalina.s ...   Up      0.0.0.0:9009->8009/tcp, 0.0.0.0:8080->8080/tcp
uaa_web_1        nginx -g daemon off;             Up      0.0.0.0:80->80/tcp, 0.0.0.0:9000->9000/tcp 
```
* log 확인
```
$ docker-compose logs -f
```
* stop
```
$ docker-compose stop
```
* start
```
$ docker-compose start
```

## 접속
* portal http://localhost
* admin http://localhost:9000