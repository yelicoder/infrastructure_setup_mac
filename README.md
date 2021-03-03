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
$docker exec -it postgres-demo psql -U postgres
$create database conference_app;
$\c conference_app // connect to conference_app database

