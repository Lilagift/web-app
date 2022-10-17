# web-app
test-package
#!/bin/bash 
# Use this script to install tomcat in rehat servers 
echo assign a hostname to your server 
sudo hostnamectl set-hostname tomcat 
# install Java JDK 1.8+ as a pre-requisit for tomcat to run. 
cd /opt 
sudo yum install git wget -y 
sudo yum install java-1.8.0-openjdk-devel -y 
# Download tomcat software and extract it. 
sudo yum install wget unzip -y 
sudo wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz 
sudo tar -xvf apache-tomcat* 
sudo rm apache-tomcat-9.0.68.tar.gz 
sudo mv apache-tomcat-9.0.68 tomcat 
sudo chmod 777 -R /opt/tomcat 
sudo chown ec2-user -R /opt/tomcat 
sh /opt/tomcat/bin/startup.sh 
# create a soft link to start and stop tomcat 
sudo ln -s /opt/tomcat/bin/startup.sh /usr/bin/starttomcat 
sudo ln -s /opt/tomcat/bin/shutdown.sh /usr/bin/stoptomcat 
starttomcat 
sudo su - ec2-user 
starttomcat
