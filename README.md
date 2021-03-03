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
# Install potgres
$docker pull postgres
