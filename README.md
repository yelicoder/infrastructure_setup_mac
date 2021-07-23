# infrastructure_setup_mac
Setup development environment on Mac
## Install Java

https://mkyong.com/java/how-to-install-java-on-mac-osx/

```
$brew search java to find all available Java-related formula
$brew info java
$brew install java
$sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk  
$brew install openjdk@11
$sudo ln -sfn /opt/homebrew/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
$ls -lsah /Library/Java/JavaVirtualMachines/ 
$brew tap adoptopenjdk/openjdk 
$brew search adoptopenjdk to find other versions of jdk
$/usr/libexec/java_home -V to list all jdk installed on the machine

$brew untap homebrew/cask-versions to clean up the homebrew/cask-versions tap
$brew install adoptopenjdk8
```
add the following to ~/.zshrc to switch between JDKs
```
jdk() {
      version=$1
      unset JAVA_HOME;
      export JAVA_HOME=$(/usr/libexec/java_home -v"$version");
      java -version
}

$jdk 1.8
$jdk 11
$jdk

```
## Install maven
```
$brew install maven
```
## config git
```
git config --global --edit
```
* once the personal access token in generated, use it once for push and you do not need to give it again.

## Install IntelliJ
Download IntelliJ.dmg
## Install Docker Desktop
Download Docker.dmg from hub.docker.com

$docker --version

$docker run hello-world
## Install mysql
$docker pull mysql

### Setup mySQL database
#### create docker-compose.yml
https://github.com/yelicoder/spring-security-conference/blob/master/docker-compose.yml
version: '3.8'

networks:

  default:
  

services:

   db:
   
     image: mysql:5.7
     
     container_name: conference_security
     
     ports:
     
       - 3306:3306
       
     volumes:
     
       - "./.data/db:/var/lib/mysql"
       
     environment:
     
       MYSQL_ROOT_PASSWORD: pass
       
       MYSQL_DATABASE: conference_security
       
       
#### Run $docker-compose up -d
       
## Install postgres
$docker pull postgres

$docker create --name postgres-demo -e POSTGRES_PASSWORD=pass -p 5432:5432 postgres:11.5-alpine

$docker start postgres-demo

$docker stop postgres-demo

#### Create the database

$docker exec -it postgres-demo psql -U postgres

$create database conference_app;

$\l // list databases

$\q // exit psql

$docker cp create_tables.sql postgres-demo:/create_tables.sql // copy the sql file to docker container

$docker exec -it postgres-demo psql -d conference_app -f create_tables.sql -U postgres // run the sql file

$docker cp insert_data.sql postgres-demo:/insert_data.sql // copy the sql file to docker container

$docker exec -it postgres-demo psql -d conference_app -f insert_data.sql -U postgres // run the sql file

#### After copy the sql file to docker container, you can also run the sql file after connect to teh database

$docker exec -it postgres-demo psql -U postgres

$create database conference_app;

$\c conference_app // connect to conference_app database

$\i create_tables.sql //run the create_tables.sql to create tables

$\dt list the tables created

#### Drop the database
DROP DATABASE conference_app;

### install pgadmin4 docker image
$docker pull dpage/pgadmin4

## Install MongoDB
* $docker pull mongo
* create docker-compose.yml
```
version: "3.8"
services:
  mongodb:
    image : mongo
    container_name: mongodb
    environment:
      - PUID=1000
      - PGID=1000
    volumes:
      - ./home/barry/mongodb/database:/data/db
    ports:
      - 27017:27017
    restart: unless-stopped
```
* $ docker-compose up -d


