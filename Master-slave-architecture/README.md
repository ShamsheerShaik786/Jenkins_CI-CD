**MAster Slave Architecture of Jenkins**
This is used distribute the work load to additional linux servers called as slaves.This is used when we want to run multiple jobs on jenkins parallelly.

**Setup & Installations**
1 Create a 2 Ubuntu linux Servers and name them as Master and Slave

2 Install the same version of java as present in the master
  sudo apt-get update
  sudo apt-get install -y openjdk-17-jdk

3 Setup passwordless SSH betwen Master and slave
  a) Connect to Master using git bash and login as jenkins user
     sudo su - jenkins
  b) Generate the ssh keys
     ssh-keygen
  c) Copy the ssh keys
     copy the public_key 
  d) Connect to slave using git bash
  e) got to cd .ssh folder paste the public_key in Authorized_key
  f) restart the server 
     sudo service ssh restart
4 Downlaod the slave.jar file
  wget http://private_ip_of_jenkinsserver:8080/jnlpJars/slave.jar

5 Give execute permissions to the slave.jar
  chmod u+x slave.jar

6 Create an empty folder that will be the workspace of jenkins
  mkdir workspace

7 Open the dashboard of Jenkins 

8 Click on Manage Jenkins--->Click on plugins ---> Available plugins ---> Install the "Command agent launcher"

9 Click on Manage Jenkins--->Click on Manage Nodes

10 Click on New node---->Enter some node name as Slave1

11 Select Permanant Agent--->OK
![Screenshot (138)](https://github.com/user-attachments/assets/ec19a607-954a-4130-a815-8c236720aa04)

12  Enter remote root directory as /home/ubuntu/workspace
![Screenshot (139)](https://github.com/user-attachments/assets/d351e923-efcd-4a93-ba7a-875932421dd5)

13 Labels: myslave (This label is associated with a job in jenkins and then that job will run on that slave)

14  Go to Launch Method and select "Launch agent via execution of command on the controller"

15 15 Click on Save
![Screenshot (140)](https://github.com/user-attachments/assets/635c5a62-005d-4429-91cd-7a6ace698ec5)

16 Intially Slave node will be in offlne to bring back to online, Go to the dashboard of Jenkins --> Manage jenkins ---> Script Approval---> Approve the command
![Screenshot (141)](https://github.com/user-attachments/assets/e1e65dc8-b71a-4cd9-9ffe-82c5e764743c)

17 click on the "mark this node temporary offline"
![Screenshot (142)](https://github.com/user-attachments/assets/18940b9e-949f-4a62-8919-642d3fb2eef5)

18 Relaunch the agent
![Screenshot (143)](https://github.com/user-attachments/assets/be178b1d-5125-450f-b1b0-34ae3b208701)

19 Go to the dashboard of Jenkins
![image](https://github.com/user-attachments/assets/4ce419bf-69e0-4e21-9401-0509b3acd01b)

20 Go to the job that we want to run on slave---->Click on Configure

21 Go to General section ---> Check restrict where this project can be run ---> Enter slave label as myslave
![Screenshot (145)](https://github.com/user-attachments/assets/5fcf8bdb-eaed-4821-a37d-a9f3359ebdbd)

22 Run the jobs and verfiy if the Job is running on configured Node or not 

23 Job1 running on Master or Built-in node 
![Screenshot (146)](https://github.com/user-attachments/assets/68cfc98b-cb01-491b-a4f5-135cbb76bd82)
![Screenshot (148)](https://github.com/user-attachments/assets/473ea715-5e0a-4655-95ad-f8391262677b)

24 Job2 is running on Slave Node 
![Screenshot (147)](https://github.com/user-attachments/assets/047d3c80-037c-4509-b5a5-3f24d187daa8)
![Screenshot (149)](https://github.com/user-attachments/assets/b7ef750f-163e-443b-8aaf-26a0f9e344bc)


