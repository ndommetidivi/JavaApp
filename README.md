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
                    


  Now the project will be cloned into your directory /opt and enter the command 

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


After the build was success enter the command maven install as given below : 


   ```bash
  mvn install
```


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
                 










                                                                                 



                                                                                    


