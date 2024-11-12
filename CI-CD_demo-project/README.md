# CI-CD Demo Project
**prerequisites**
1. Create a 3 ubuntu Servers and Name them as Jenkins Master, QA Server and Prod Server
2. Install Java, Maven, Git on Jenkins Server and Setup the Jenkins
3. Install tomcat10, tomcat10-admin on QA and Prod Server and configure the tomcat-users.xml file

![image](https://github.com/user-attachments/assets/5672f469-0e73-4eb2-b2f6-d109a2703aec)

**Continuous Download**
1 Open the dashboard of Jenkins
2 Click on New item---->Enter the item name as Development
3 Select Free style project-->OK
4 Go to Source code Management
5 Click on Git
6 Enter the GitHub URL where developers have uploaded the code
https://github.com/ShamsheerShaik786/maven-demo-project.git
![image](https://github.com/user-attachments/assets/9df2d20f-419a-4ba7-b25f-c83a9c1fcb36)
7 Click on Apply--->Save
8 Run the Build

**Continuous Build**
1 Open the dashboard of Jenkins
2 Go to the Development job--->Click on Configure
3 Go to Build section
4 Click on Add build step
5 Click on Top level maven targets
6 Enter the maven goal: package
![image](https://github.com/user-attachments/assets/a1cdd2b4-0c76-48e5-a019-f8cc8be18086)
7 Click on Apply--->Save
8 Run the Build

**Continuous Deployment**
1 Open the dashboard of Jenkins
2 Go to Manage Jenkins
3 Click on Manage Plugins
4 Click on Available section
5 Search for Deploy to container plugin
6 Install it
7 Go to the dashboard of Jenkins
8 Go to the Development job--->Click on configure
9 Go to Post build actions
10 Click on Add post build action
11 Click on Deploy war/ear to container
   war/ear file: **/*.war
   ![image](https://github.com/user-attachments/assets/0fcdaa06-de5d-4f25-a76b-4e26ef00049a)
   Context path: testapp   (This is the name that testers will enter in browser to access the application)
   Click on Add container
   Select tomcat9
   Enter tomcat9 credentials 
   Tomcat url: private_ip_qaserver:8080
![image](https://github.com/user-attachments/assets/7e411c10-d0fe-450a-82cd-f73e0ce31abe)
12 Click on Apply---->Save
**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of QA Server:8080/context path of QA Server
![image](https://github.com/user-attachments/assets/6ce17ffd-6045-4bcd-b4cc-56bf97750a54)
![image](https://github.com/user-attachments/assets/feb69a6b-a7e7-42ca-be75-42ed7d659c78)

**Continuous Testing**
1 Open the dashboard of Jenkins
2 Click on New item
3 Enter some item name (Testing)
4 Select Free style project
5 Enter the github url where testers have uploaded the selenium scripts
  https://github.com/ShamsheerShaik786/Functional-Testing.git
6 Go to Build section
7 Click on Add  build step
8 Click on Execute shell
  java -jar path/testing.jar
![image](https://github.com/user-attachments/assets/ad3d6a5d-b2e4-4f48-8127-54e3145ae8e6)
9 Apply--->Save
10 Run the build

**Linking the Development job with the Testing job**
1 Open the dashboard of Jenkins
2 Go to the dvelopment job
3 Click on configure
4 Go to Post build actions
5 Click on Add post buuild actions
6 Click on Build another job
7 Enter the job the Testing
![image](https://github.com/user-attachments/assets/7ac8f09e-1ef9-4559-9dfd-a6384e4148f3)
8 Apply--->Save
  This is called as upstream/downstream configuration

**Copying artifacts from Development job to Testing job**
1 Open the dashboard of Jenkins
2 Click on Manage Jenkins--->Manage plugins
3 Go to Avaialbale section--->Search for "Copy Artifact" plugin
4 Click on Install without restart
5 Go to the dashboard of Jenkins
6 Go to the Development job--->Click on Configure
7 Go to Post build actions
8 Click on Add post build actions
9 Click on Archive the artifacts
10 Enter files to be archived as **\*.war
11 Click on Apply--->>Save
12 Go to the dashboard of jenkins
13 Go to the Testing job---->Click on configure
14 Go to Build section
15 Click on Add build step
15 Click on Copy artifacts from other project
16 Enter project name as "Development"
![image](https://github.com/user-attachments/assets/0dfd47c4-7c43-4e9f-b471-789b351c60be)


**Continuous Delivery**
1 Open the dashboard of jenkins
2 Go to Testing job--->Configure
3 Go to Post build actions
4 Click on Add post build action
5 Click on Deploy war/ear to container
  war/ear files: **/*.war
  contextpath: prodapp
  Click on Add container
  Select tomcat9
  Enter username and password of tomcat9
  Romcat url: private_ip_of_prodserver:8080
![image](https://github.com/user-attachments/assets/3458868f-05b1-4176-938e-17853dc989ed)
6 Apply---->Save

**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of Prod Server:8080/context path of Prod Server
![Screenshot (125)](https://github.com/user-attachments/assets/a15a3ce4-c8d7-40ed-9eeb-8006639c151b)
![Screenshot (126)](https://github.com/user-attachments/assets/45d02b96-23ff-4083-abf3-1a17f01819f7)





# CI-CD Demo Project
**prerequisites**
1. Create a 3 ubuntu Servers and Name them as Jenkins Master, QA Server and Prod Server
2. Install Java, Maven, Git on Jenkins Server and Setup the Jenkins
3. Install tomcat10, tomcat10-admin on QA and Prod Server and configure the tomcat-users.xml file

![image](https://github.com/user-attachments/assets/5672f469-0e73-4eb2-b2f6-d109a2703aec)

**Continuous Download**
1 Open the dashboard of Jenkins
2 Click on New item---->Enter the item name as Development
3 Select Free style project-->OK
4 Go to Source code Management
5 Click on Git
6 Enter the GitHub URL where developers have uploaded the code
https://github.com/ShamsheerShaik786/maven-demo-project.git
![image](https://github.com/user-attachments/assets/9df2d20f-419a-4ba7-b25f-c83a9c1fcb36)
7 Click on Apply--->Save
8 Run the Build

**Continuous Build**
1 Open the dashboard of Jenkins
2 Go to the Development job--->Click on Configure
3 Go to Build section
4 Click on Add build step
5 Click on Top level maven targets
6 Enter the maven goal: package
![image](https://github.com/user-attachments/assets/a1cdd2b4-0c76-48e5-a019-f8cc8be18086)
7 Click on Apply--->Save
8 Run the Build

**Continuous Deployment**
1 Open the dashboard of Jenkins
2 Go to Manage Jenkins
3 Click on Manage Plugins
4 Click on Available section
5 Search for Deploy to container plugin
6 Install it
7 Go to the dashboard of Jenkins
8 Go to the Development job--->Click on configure
9 Go to Post build actions
10 Click on Add post build action
11 Click on Deploy war/ear to container
   war/ear file: **/*.war
   ![image](https://github.com/user-attachments/assets/0fcdaa06-de5d-4f25-a76b-4e26ef00049a)
   Context path: testapp   (This is the name that testers will enter in browser to access the application)
   Click on Add container
   Select tomcat9
   Enter tomcat9 credentials 
   Tomcat url: private_ip_qaserver:8080
![image](https://github.com/user-attachments/assets/7e411c10-d0fe-450a-82cd-f73e0ce31abe)
12 Click on Apply---->Save
**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of QA Server:8080/context path of QA Server
![image](https://github.com/user-attachments/assets/6ce17ffd-6045-4bcd-b4cc-56bf97750a54)
![image](https://github.com/user-attachments/assets/feb69a6b-a7e7-42ca-be75-42ed7d659c78)

**Continuous Testing**
1 Open the dashboard of Jenkins
2 Click on New item
3 Enter some item name (Testing)
4 Select Free style project
5 Enter the github url where testers have uploaded the selenium scripts
  https://github.com/ShamsheerShaik786/Functional-Testing.git
6 Go to Build section
7 Click on Add  build step
8 Click on Execute shell
  java -jar path/testing.jar
![image](https://github.com/user-attachments/assets/ad3d6a5d-b2e4-4f48-8127-54e3145ae8e6)
9 Apply--->Save
10 Run the build

**Linking the Development job with the Testing job**
1 Open the dashboard of Jenkins
2 Go to the dvelopment job
3 Click on configure
4 Go to Post build actions
5 Click on Add post buuild actions
6 Click on Build another job
7 Enter the job the Testing
![image](https://github.com/user-attachments/assets/7ac8f09e-1ef9-4559-9dfd-a6384e4148f3)
8 Apply--->Save
  This is called as upstream/downstream configuration

**Copying artifacts from Development job to Testing job**
1 Open the dashboard of Jenkins
2 Click on Manage Jenkins--->Manage plugins
3 Go to Avaialbale section--->Search for "Copy Artifact" plugin
4 Click on Install without restart
5 Go to the dashboard of Jenkins
6 Go to the Development job--->Click on Configure
7 Go to Post build actions
8 Click on Add post build actions
9 Click on Archive the artifacts
10 Enter files to be archived as **\*.war
11 Click on Apply--->>Save
12 Go to the dashboard of jenkins
13 Go to the Testing job---->Click on configure
14 Go to Build section
15 Click on Add build step
15 Click on Copy artifacts from other project
16 Enter project name as "Development"
![image](https://github.com/user-attachments/assets/0dfd47c4-7c43-4e9f-b471-789b351c60be)


**Continuous Delivery**
1 Open the dashboard of jenkins
2 Go to Testing job--->Configure
3 Go to Post build actions
4 Click on Add post build action
5 Click on Deploy war/ear to container
  war/ear files: **/*.war
  contextpath: prodapp
  Click on Add container
  Select tomcat9
  Enter username and password of tomcat9
  Romcat url: private_ip_of_prodserver:8080
![image](https://github.com/user-attachments/assets/3458868f-05b1-4176-938e-17853dc989ed)
6 Apply---->Save

**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of Prod Server:8080/context path of Prod Server
![Screenshot (125)](https://github.com/user-attachments/assets/a15a3ce4-c8d7-40ed-9eeb-8006639c151b)
![Screenshot (126)](https://github.com/user-attachments/assets/45d02b96-23ff-4083-abf3-1a17f01819f7)





# CI-CD Demo Project
**prerequisites**
1. Create a 3 ubuntu Servers and Name them as Jenkins Master, QA Server and Prod Server
2. Install Java, Maven, Git on Jenkins Server and Setup the Jenkins
3. Install tomcat10, tomcat10-admin on QA and Prod Server and configure the tomcat-users.xml file

![image](https://github.com/user-attachments/assets/5672f469-0e73-4eb2-b2f6-d109a2703aec)

**Continuous Download**
1 Open the dashboard of Jenkins
2 Click on New item---->Enter the item name as Development
3 Select Free style project-->OK
4 Go to Source code Management
5 Click on Git
6 Enter the GitHub URL where developers have uploaded the code
https://github.com/ShamsheerShaik786/maven-demo-project.git
![image](https://github.com/user-attachments/assets/9df2d20f-419a-4ba7-b25f-c83a9c1fcb36)
7 Click on Apply--->Save
8 Run the Build

**Continuous Build**
1 Open the dashboard of Jenkins
2 Go to the Development job--->Click on Configure
3 Go to Build section
4 Click on Add build step
5 Click on Top level maven targets
6 Enter the maven goal: package
![image](https://github.com/user-attachments/assets/a1cdd2b4-0c76-48e5-a019-f8cc8be18086)
7 Click on Apply--->Save
8 Run the Build

**Continuous Deployment**
1 Open the dashboard of Jenkins
2 Go to Manage Jenkins
3 Click on Manage Plugins
4 Click on Available section
5 Search for Deploy to container plugin
6 Install it
7 Go to the dashboard of Jenkins
8 Go to the Development job--->Click on configure
9 Go to Post build actions
10 Click on Add post build action
11 Click on Deploy war/ear to container
   war/ear file: **/*.war
   ![image](https://github.com/user-attachments/assets/0fcdaa06-de5d-4f25-a76b-4e26ef00049a)
   Context path: testapp   (This is the name that testers will enter in browser to access the application)
   Click on Add container
   Select tomcat9
   Enter tomcat9 credentials 
   Tomcat url: private_ip_qaserver:8080
![image](https://github.com/user-attachments/assets/7e411c10-d0fe-450a-82cd-f73e0ce31abe)
12 Click on Apply---->Save
**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of QA Server:8080/context path of QA Server
![image](https://github.com/user-attachments/assets/6ce17ffd-6045-4bcd-b4cc-56bf97750a54)
![image](https://github.com/user-attachments/assets/feb69a6b-a7e7-42ca-be75-42ed7d659c78)

**Continuous Testing**
1 Open the dashboard of Jenkins
2 Click on New item
3 Enter some item name (Testing)
4 Select Free style project
5 Enter the github url where testers have uploaded the selenium scripts
  https://github.com/ShamsheerShaik786/Functional-Testing.git
6 Go to Build section
7 Click on Add  build step
8 Click on Execute shell
  java -jar path/testing.jar
![image](https://github.com/user-attachments/assets/ad3d6a5d-b2e4-4f48-8127-54e3145ae8e6)
9 Apply--->Save
10 Run the build

**Linking the Development job with the Testing job**
1 Open the dashboard of Jenkins
2 Go to the dvelopment job
3 Click on configure
4 Go to Post build actions
5 Click on Add post buuild actions
6 Click on Build another job
7 Enter the job the Testing
![image](https://github.com/user-attachments/assets/7ac8f09e-1ef9-4559-9dfd-a6384e4148f3)
8 Apply--->Save
  This is called as upstream/downstream configuration

**Copying artifacts from Development job to Testing job**
1 Open the dashboard of Jenkins
2 Click on Manage Jenkins--->Manage plugins
3 Go to Avaialbale section--->Search for "Copy Artifact" plugin
4 Click on Install without restart
5 Go to the dashboard of Jenkins
6 Go to the Development job--->Click on Configure
7 Go to Post build actions
8 Click on Add post build actions
9 Click on Archive the artifacts
10 Enter files to be archived as **\*.war
11 Click on Apply--->>Save
12 Go to the dashboard of jenkins
13 Go to the Testing job---->Click on configure
14 Go to Build section
15 Click on Add build step
15 Click on Copy artifacts from other project
16 Enter project name as "Development"
![image](https://github.com/user-attachments/assets/0dfd47c4-7c43-4e9f-b471-789b351c60be)


**Continuous Delivery**
1 Open the dashboard of jenkins
2 Go to Testing job--->Configure
3 Go to Post build actions
4 Click on Add post build action
5 Click on Deploy war/ear to container
  war/ear files: **/*.war
  contextpath: prodapp
  Click on Add container
  Select tomcat9
  Enter username and password of tomcat9
  Romcat url: private_ip_of_prodserver:8080
![image](https://github.com/user-attachments/assets/3458868f-05b1-4176-938e-17853dc989ed)
6 Apply---->Save

**To access the Deploed Application on QA Server(tomcat)**
1. Public_IP of Prod Server:8080/context path of Prod Server
![Screenshot (125)](https://github.com/user-attachments/assets/a15a3ce4-c8d7-40ed-9eeb-8006639c151b)
![Screenshot (126)](https://github.com/user-attachments/assets/45d02b96-23ff-4083-abf3-1a17f01819f7)






