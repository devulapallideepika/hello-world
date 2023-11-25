## Deploying Application on Tomcat server
## Jenkins server
- create ec2 instance 
- Installing  java it is prerequisite for jenkins
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/26d073d3-0e2a-4b80-a378-437c7a6eda34)

- Install git with "sudo apt install git" command
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/d49f7d09-5c21-47c5-ae4d-79218b26c100)

- Install maven
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/b499a6ff-1837-412d-94c9-abd1a239c062)

- In vim  bash - profile add the path of maven ,java
  - M2_HOME=/opt/maven
  - M2=/opt/maven/bin
  - JAVA_HOME=/usr/lib/jvm/java-11-openjdk-11.0.19.0.7-1.amzn2.0.1.x86_64
  - PATH=$PATH:$HOME/bin:$JAVA_HOME:$M2_HOME:$M2
    
 ![image](https://github.com/devulapallideepika/hello-world/assets/129947829/a8617dd2-408e-46d5-bf96-58aaf77bf0c4)

- Install jenkins
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/5c420a91-0f77-416e-b2ed-d52c37ed12fb)

- To get jenkins administrator password use command "sudo cat /var/lib/jenkins/secrets/initialAdminPassword"
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/b4677159-db38-47b6-bedb-dcc7ed56c4f6)

- Allow the security group inbound rule with 8080 port as jenkins by default runs on 8080
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/4a234bbb-91d4-433f-b21e-b17bd140dc5f)

- install plugins along with maven integration plugin
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/cf435187-7ee0-4fae-a0b5-f7133fe26155)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/9a9c26c3-0e42-47f4-86ef-d392b1aa9308)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/db437533-6f5c-4a79-88f2-26bf91c392a7)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/0fdc4b61-22db-4a43-ac31-ef92b8f044b1)

## Tomcat server
- create ec2 instance.
- install java
- install tomcat
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/3c15f87d-11b2-4607-990a-efabf9cfaab7)

- now application is accessible on port 8080. but tomcat application doesnt allow to login from browser. changing a default parameter in context.xml , comment () Value ClassName field on files which are under webapp directory. After that restart tomcat services to effect these changes.
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/ec85a8a4-511e-410a-ade8-74888b283d87)

-  In tomcat directory in conf directory in tomcat-users.xml file add rolenames,username,password
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/60c5ae31-8e08-466c-b2bc-0d86c281e31a)

- start the tomcat server
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/1ca5e0a4-c2d5-4f82-8c92-0d36dc736571)

-Access the tomcat with http:ip address:8080

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/7bf6786e-2c42-4bd3-a768-f6a5cf1d9769)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/1605b6d1-2e22-44b0-83d4-66817cf988d2)

- Install deploy to container plugin in jenkins
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/47a86d8d-088d-4ad9-8598-d6a563f5b18e)

- Given tomcat deployer username & password credentials in jenkins
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/52b672ba-4be4-45f7-8732-7dc24205a8b2)

# In jenkins
- Given path of java, git, maven in jenkins
- create a job
- Given git URL and branch
- Build:
   - Root POM : pom.xml
   - Goals and options : clean install
- In post build actions : 
   - Deploy war/ear to container
     - WAR/EAR files : **/*.war
     - Containers : Tomcat 8.x
     - Credentials: deployer (user created on above)
     - Tomcat URL : http://<PUBLIC_IP>:8080
       
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/885a7a7f-b5d0-49a2-a929-3225b610425f)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/a4fefa17-ae4e-4ca6-82d5-6518653ab7fd)

- save and run the job.
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/0d17f606-5693-4a06-b88a-7ccba21fe971)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/e7040e81-165e-4158-8463-22ab6aac6de2)

- webapp is deployed on tomcat server.
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/e331f9b6-6ec6-4d3e-9ed2-98c17ccd2e27)

- Access the application on browser http://<public_ip>:8080/webapp
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/216eb573-69f0-4595-89d7-064d3a19a09f)

*******************************************************************************************************************************************************************************************
*******************************************************************************************************************************************************************************************
*******************************************************************************************************************************************************************************************
## DEPLOY ON DOCKER
- create ec2 instance
- 
