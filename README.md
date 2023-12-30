## Ansible-Automate Project

## Ansible Configuration Management - Automate Project 7 to 10

**Steps**

**Install and configure ansible on ubuntu ec2 instance**

-  I spined up an ubuntu ec2 instance for my ansible and jekings server.

-  I updated it and Installed jenkins and ansible. I installed jenkins using a script i called **jenk.sh** that contains jenkins installation code. while ansible was installed using the comand **sudo apt install jenkinks -y** 

-  Using **systemctl status Jenkins** command, I confirmed that jenkins was successfully installed and using **ansible --version,** command, I also confirmed that ansible was installed successfully as shown bellow. i didnt forget to open port 8080 to allow access for jenkins. 


 ![Alt text](<images/Unsaved Image 2.jpg>)


![Alt text](<images/Unsaved Image 4.jpg>)

-  In github, i created a repository call **ansible-config-mgt**, I cloned it down to my system using **VScode**

4.  Configure Jenkins build job to archive  repository content every time its changed. I achieved this by following these steps bellow. 

- I Created a new Freestyle project called **ansible** in Jenkins and pointed it to my 'ansible-config-mgt' repository  

![Alt text](<images/Unsaved Image 5.jpg>)


-  Configured a webhook in GitHub and set the webhook to trigger ansible build.

![Alt text](<images/Unsaved Image 6.jpg>)

![Alt text](<images/Unsaved Image 7.jpg>)

- I tested my webhook to be sure it triggers and jenkins achives my artifact to this folder ls /**var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/**

- The buld was successful and saved in the above folder.

![Alt text](<images/Unsaved Image 8.jpg>)

![Alt text](<images/Unsaved Image 9.jpg>)



## Begin ansible development

1.  i created a new branch which i will be working on. I called the branch **pro11**. I created it using this command , **git checkout -b pro11**. this command also switched to the new branch automatically .

- I created inventory folder and playbooks folder.
withing the playbooks folder, i created common.yml file . and witin inventory folder, i created uat.yml, dev.yml,staging.yml and prod.yml as shown bellow 

  ![Alt text](<images/Unsaved Image 10.jpg>)


  ## Step 4 - Set up an Ansible Inventory

-  i set up ssh agent for my jenkins-ansible server to be able to communicate to other servers privately. i ran the following code while on my download folder that contains my pem keys. 

-  eval `ssh-agent -s`
-  ssh-add rel8.pem 
-  ssh-add 1
-  Then i loged in to my jenkins-ansible server using ssh -A ubuntu@44.202.161.203 (public ip of the instance)



![Alt text](<images/Unsaved Image 11.jpg>)

![Alt text](<images/Unsaved Image 12.jpg>)

-  I spined up 4 Rhel8 instances for NFS,web1, web2, and Db, and tested that i caould connect to them using ssh ec2-user@their ip address. it was successful as shown bellow. I also spined up another ubuntu instance which is going to be the load balancer

  ![Alt text](<images/Unsaved Image 13.jpg>)


  -  I updatad the inventory/dev folder with the ip addresses of my 5 servers acording to the group they belong.

 ![Alt text](<images/Unsaved Image 14.jpg>)




- I also updated the file common.yml with the playbook task. as shown bellow 


![Alt text](<images/Unsaved Image 15.jpg>)

-  I updated my repo with the codes and pull request 

![Alt text](<images/Unsaved Image 16.jpg>)

-  I set up my vscode to connect to my instance so i can start running my playbook. 
  
   ![Alt text](<images/Unsaved Image17.jpg>)

   -  I ran my first playbook and i was a success as shown bellow:


![Alt text](<images/Unsaved Image 18.jpg>)

 -  Using ssh ec2-user@172-31-38-51, i ssh into my nfs server and confirmed that wireshark was successfully installed 

 ![Alt text](<images/Unsaved Image 19.jpg>)


 ## PROJECT COMPLED


