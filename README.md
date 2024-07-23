# Java Application Deployment on Tomcat Server

This README file provides instructions for installing Java and deploying a Java application on an Apache Tomcat server.

## Prerequisites

- An Ubuntu server
- sudo privileges

## Step 1: Install Java

### 1.1 Update the Package Index

```bash
sudo apt update
Install Java
sudo apt install openjdk-11-jdk -y
java -version
openjdk version "11.0.11"
Install Apache Tomcat
Download Tomcat
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.91/bin/apache-tomcat-9.0.91.zip
unzip apache-tomcat-9.0.91.zip
mv apache-tomcat-9.0.91.zip /opt/tomcat
sudo chown -R $USER:$USER /opt/tomcat
sudo nano /etc/systemd/system/tomcat.service
[Unit]
Description=Apache Tomcat Web Application Container
After=network.target

[Service]
Type=forking

ExecStart=/opt/tomcat/bin/startup.sh
ExecStop=/opt/tomcat/bin/shutdown.sh

User=tomcat
Group=tomcat
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target

sudo systemctl daemon-reload
sudo systemctl start tomcat
sudo systemctl enable tomcat

cp /path/to/your/login.war /opt/tomcat/webapps/
http://<your-server-ip>:8080/login
