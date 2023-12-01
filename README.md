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
## DEPLOY ON DOCKER CONTAINER USING JENKINS
- create ec2 instance
##  Jenkins Installation :
- install jenkins
   - prerequisite :
     - Java
       
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/8616cd81-2994-4fcf-ad46-6b557131af1b)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/a72ea4e8-0b30-4e8d-b6d4-5541c4624351)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/63ddfb46-ea61-4bdb-a306-518e0b419ec6)

- To know the administrator password sudo cat /var/lib/jenkins/secrets/initialAdminPassword
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/a5db80e7-3151-4c50-aea6-53c73bb3eaaf)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/0fe0194c-f645-4b0e-9037-8b981cd0fed3)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/d8829a84-24b9-4f03-9b47-b2ffe21f9591)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/b02082cc-7bdc-401f-9d30-370023fa85a4)

## Maven installation:
- Install maven
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/9c77987d-c746-41fb-aa01-2002d6db460e)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/62339eb5-7993-41ee-a344-297d42d3621a)

- Add the java and maven path in bash-profile
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/54ddfeb2-b892-43cb-a0b8-e5841c880834)

## Docker installation :
- "sudo apt install docker.io" is the command to install docker
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/cba0c1d6-11aa-4405-accf-b7a68b6b5a37)

- changing the password authentication in sshd_config
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/7e7d9c67-0dcf-4a6d-8ee0-dc9c990bcd31)

- Grant Jenkins user and Ubuntu user permission to docker deamon.
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/1af20229-66b5-4132-85ca-6d8386fb3689)

# In jenkins :
- install maven integration plugin
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/98e420e6-1477-49f5-a746-e8b94186d3a9)

- install publish over ssh plugin
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/aad6bb68-75c8-4f0c-9974-7d4232b1b2ca)

# integrate jenkins with Docker-host :
- install publish over ssh
- SSH Servers :
     - Hostname : ( docker-host ip)
     - username : ubuntu
     - password : xxxxxxxxxxxxx
# Jenkins job:
- create a job
- Given github <URL>
- given branch
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/dbcf3e54-ae7e-4a1c-bf90-bbf63e4e4e81)

- In Build :
    - Root pom : pom.xml
    - goals and options : clean install package
- In post build :
     -  Send build artifacts over SSH
     -  SSH Server Name : docker-host
     -  Source files    : webapp/target/*.war
     -  Remove prefix   : webapp/target
     - Remote directory : //opt/docker
       
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/f0aae401-2753-41f2-9b24-ccadc961a82d)
 
- save and build the job.
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/6bb75bf2-3238-4dd9-8d03-adc90e9ec8bd)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/9c3ec851-7899-4da5-a77b-aa846e7566a0)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/e7e967b9-4ca4-4854-9b3c-bb27da333021)

- webapp artifact is sended to docker-host through ssh
- build the docker image
- Image is created based on Dockerfile
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/fca4e927-997e-478e-a88f-3fadde87e8ef)

- create a container
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/0233ef7e-2235-4c23-872d-2bd1537a1cb7)

- Allow the security inbound rule with port 8081
- Access the application through browser with http:// <ip address>:port no/webapps
  
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/b1ff72b1-1280-41ba-bfa7-46a13996003f)

![image](https://github.com/devulapallideepika/hello-world/assets/129947829/389e5e96-6143-4a2b-9ad8-a58743b7efcd)

****************************************************************************************************************************************************************************************
****************************************************************************************************************************************************************************************
## DEPLOY ON CONTAINER USING ANSIBLE:
- Create an ec2 instance
## Install Jenkins
- install java
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/2aa3382f-1db8-4516-989d-ba303dd3683b)
- install jenkins
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/6b31660d-fa39-44fa-b78b-f426e084b039)
- Access the jenkins on default port 8080
- allow the security inbound rule 8080
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/0d5b5991-74a6-4c40-8d75-13f5609ad987)
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/72fd5a6f-19c7-43ca-8f56-93b558ca938a)
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/dc4df128-9d52-4b1a-a425-f2697c99a28d)
- Install necessary plugins along with maven integration and publish over ssh plugins
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/3940a03e-1dcc-4eda-ab44-facfea44478f)
- Install maven
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/e328141c-a868-4ec7-9d21-5698f7bb768b)
- maven and java path given in bash-profile
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/721e9dc4-ae11-4967-b862-64abe9217668)
## Install Ansible
- commands to install ansible
- $ sudo apt update
- $ sudo apt install software-properties-common
- $ sudo add-apt-repository --yes --update ppa:ansible/ansible
- $ sudo apt install ansible
- create user & passwd
   - useradd username
   - passwd  password
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/d6c98085-8a33-445a-b136-4ef6d4f94d5d)
- Add user in /etc/sudoers file 
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/96587986-7c78-44a7-8381-7f69ab36a73b)
- Enable password authentication
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/a07d2a98-fc19-4df4-8a1a-6cb3aa8e63cb)
- create public key and private key using "ssh-keygen" command
- copy the keys using "ssh-copy-id <target server ip>"
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/f1109546-9fae-4b12-b7c8-19d781ae79b3)
 
## Install Docker :
- command to install docker
- $ sudo apt install docker.io
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/3ad0b7e7-2beb-4586-ad3d-89421e5be2d1)
## integrate jenkins and ansible :
- install publish over ssh plugin
- Manage Jenkins > Configure System > Publish Over SSH > SSH Servers
  - SSH Servers : name : ansible-host
  - Hostname:<ServerIP>
  - username: ansadmin
  - Advanced > choose Use password authentication, or use a different key
  - password: *******
## Jenkins job :
- create a job enter new item
- source code management :
       - Repository : Git <URL>
       - Branch     : main
- Build:
       - Root POM : pom.xml
       - Goals and options : clean install package
- Post-build Actions
       - Send build artifacts over SSH
       - SSH Server Name: ansible-server
       - Transfers > Transfer set
           - Source files : webapp/target/*.war
           - Remove prefix: webapp/target
           - Remote directory: //opt//docker
- save and run the job
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/b6c5607a-4ba5-49e7-9739-d2c048bb880f)
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/8fcbfb72-a2cb-436d-a77a-56a8c62ad7ee)
![image](https://github.com/devulapallideepika/hello-world/assets/129947829/f2807992-8c59-4de5-88c3-6f2f246ff6a3)

  








   

