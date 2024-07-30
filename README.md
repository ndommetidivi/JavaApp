Java Application Deployment 

STEPS TO INSTALL JAVA
   ```bash
  sudo apt-get update
``` 
   ```bash
   sudo apt-get install openjdk-8-jdk -y

``` 
Command to check the Java version
   ```bash
  java -version
``` 
![Screenshot 2024-07-17 173830](https://github.com/user-attachments/assets/8fd010a8-f7a6-4157-88d0-3d80793df1c6)

To set the environment path 
   ```bash
   nano ~/.bashrc
``` 
   ```bash
   export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH
  
``` 
   ```bash
    source ~/.bashrc
``` 
steps to install maven 
   ```bash
  wget https://dlcdn.apache.org/maven/maven-3/3.9.8/binaries/apache-maven-3.9.8-bin.zip
``` 
   ```bash
  unzip apache-maven-3.9.8-bin.zip
``` 
```bash
ls
``` 
```bash
mv apache-maven-3.9.8-bin.zip /opt/maven 
``` 
```bash
  nano ~/.bashrc  
``` 
```bash
    export M2_HOME=/opt/maven
export PATH=$M2_HOME/bin:$PATH
``` 


```bash
source ~/.bashrc
``` 
```bash
mvn -version
``` 
Steps to install tomcat 
```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.89/bin/apache-tomcat-9.0.89.tar.gz 
``` 
Extract Tomcat:

Extract the downloaded archive to a directory where you want to install Tomcat. For this example, we'll use /opt/tomcat.
```bash
  sudo mkdir /opt/tomcat  
``` 
```bash
  sudo tar xzvf apache-tomcat-9.0.89.tar.gz   
``` 
Configure Permissions:
Set the appropriate permissions for the Tomcat directory.
```bash
 sudo chown -R $USER:$USER /opt/tomcat
sudo chmod +x /opt/tomcat/bin/*.sh    
``` 
Start Tomcat:
You can start Tomcat using the startup script provided in the bin directory.
```bash
/opt/tomcat/bin/startup.sh
``` 
Access Tomcat:
Tomcat should now be running. You can access the Tomcat server by navigating to
 http://your-server-ip:8080 in your web browser.
Set Up Tomcat as a Service:
To manage Tomcat as a service, you can create a systemd service file
```bash
  sudo nano /etc/systemd/system/tomcat.service  
``` 
```bash
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
Reload the systemd daemon to apply the changes:
sudo systemctl daemon-reload
Start and enable the Tomcat service:
sudo systemctl start tomcat
sudo systemctl enable tomcat
``` 



Steps to deploy Java Application : 

  Enter into the directory opt by using the command 
 
```bash
cd /opt
```
  Clone the java project from the github it looks as  below : 

 

Check in which branch the code was present.

Click on code and copy the URL of the master branch.

 ```bash
git clone -b master https://github.com/kvurukuti/JavaApp.git
```                      
 ![Screenshot 2024-07-17 185627](https://github.com/user-attachments/assets/50004c65-33b3-4bfa-901e-e36f410fda7a)
Now the project will be cloned into your directory /opt and enter the command 

![Screenshot 2024-07-17 190512](https://github.com/user-attachments/assets/4199f7ed-8c95-48e5-bdac-3fb670a9c8fa)


  ```bash
   ls
```

                    
Here you can see the cloned project named JavaApp.

Now enter into the directory where your project was located

```bash
cd /opt/JavaApp
```

                             
 Now enter the command  maven clean as given below :  

```bash
mvn clean
```
![Screenshot 2024-07-17 190521](https://github.com/user-attachments/assets/8165a43b-2b56-4279-b38d-d22794b087dc)



After the build was success enter the command maven install as given below : 


   ```bash
  mvn install
```
![Screenshot 2024-07-17 190626](https://github.com/user-attachments/assets/441d6b24-1663-40b0-868c-158127a89499)




  It it was done you will get build success shown as below : 

 

Here you will get the target file.

Enter into the path where your target file was located.


     
```bash
cd /target
```
 
Enter the command   ls      
     
 Enter the command pwd to know the path as shown below        

     pwd 



Now enter into the webapps directory .


  

  
     cd /opt/tomcat/webapps

Enter the command ls.

Now  copy the login.war file into webapps

And enter the path where previously you got by using the pwd command.     

     
     cp /opt/JavaApp/tomcat/login.war /opt/tomcat/webapps         
  Enter the command ls to check whether the file is copied or not.
       
  Here you should enter into the bin directory and start the application.

    cd /opt/tomcat/bin/startup.sh
   

 Now your application will start successfully.

Check your application in your browser by giving the ip address with port number 8080.
                                    
You will get the page as shown below : 
                 

                 

![Screenshot 2024-07-17 190713](https://github.com/user-attachments/assets/835b46b6-4415-4953-8951-001e934700ed)











                                                                                 



                                                                                    


