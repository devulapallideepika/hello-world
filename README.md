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
## Tomcat server
- create ec2 instance.
- install java
- install tomcat
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/3c15f87d-11b2-4607-990a-efabf9cfaab7)
-  In tomcat directory in conf directory add rolenames,username,password
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
- In maven clean install
- In post build actions :
