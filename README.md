# infrastructure_setup_mac
Setup development environment on Mac
# Install Java11
$brew update

$brew install java11

$sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachine/openjdk.jdk
# Install IntelliJ
Download IntelliJ.dmg
# Install Docker Desktop
Download Docker.dmg from hub.docker.com

$docker --version

$docker run hello-world
# Install mysql
$docker pull mysql
# Install postgres
$docker pull postgres

$docker create --name postgres-demo -e POSTGRES_PASSWORD=Welcome -p 5432:5432 postgres:11.5-alpine

$docker start postgres-demo

$docker cp create_tables.sql postgres-demo:/create_tables.sql // copy the sql file to docker container

$docker exec -it postgres-demo psql -d conference_app -f create_tables.sql -U postgres // run the sql file

$docker cp insert_data.sql postgres-demo:/insert_data.sql // copy the sql file to docker container

$docker exec -it postgres-demo psql -d conference_app -f insert_data.sql -U postgres // run the sql file

## After copy the sql file to docker container, you can also run the sql file after connect to teh database

$docker exec -it postgres-demo psql -U postgres

$create database conference_app;

$\c conference_app // connect to conference_app database

$\i create_tables.sql //run the create_tables.sql to create tables

$\dt list the tables created

#### Drop the database
DROP DATABASE conference_app;


