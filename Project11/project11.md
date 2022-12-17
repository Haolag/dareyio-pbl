# Project 11
![alt text](./images/bastion.png)

## Updaate jenkins server tag

![alt text](./images/EC2%20intances.PNG)

## Create a new Repo on Github

![alt text](./images/Github%20repo.PNG)

## sudo apt update

## sudo apt install ansible

![alt text](./images/anible%20installed.PNG)

Create a new Freestyle project ansible in Jenkins and point it to your ‘ansible-config-mgt’ repository.

![alt text](./images/ansible%20version.PNG)

## Configure Webhook in GitHub and set webhook to trigger ansible build.

![alt text](./images/webhook%20setting.PNG)


## Configure a Post-build job to save all (**) files, like i did it in Project 9.

![alt text](./images/postbuild%20jenkins%20setting.PNG)

## Test my setup by making some change in README.MD file in master branch and make sure that builds starts automatically and Jenkins saves the files (build artifacts) in following folder
ls /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/


![alt text](./images/jnkins%20jobs%20archive.PNG)


## BEGIN ANSIBLE DEVELOPMENT

In my ansible-config-mgt GitHub repository, created a new branch that will be used for development of a new feature.

on Vs code press, ctrl,shift ,P

Git clone

Choose clone from Github and choose the ansible repository we just created.

Make sure Git for windows installed, if not download and install on ur PC

load new terminal, pick gitbash as terminal type, will ask you to navigate to folder where ansible is located that was just cloned.

Create a new branch

![alt text](./images/inventory%20and%20playbook%20files.PNG)

## Create a directory and name it playbooks – it will be used to store all your playbook files.

mkdir playbooks

![alt text](./images/inventory%20and%20playbook%20files.PNG)


## Create a directory and name it inventory – it will be used to keep your hosts organised.

![alt text](./images/dev%20inventory.PNG)

## Within the inventory folder, create an inventory file (.yml) for each environment (Development, Staging Testing and Production) dev, staging, uat, and prod respectively.

![alt text](./images/dev%20inventory.PNG)


## Lets add SSH agents

Install Open SSH with instructions in link below

https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse


Open powershell

![alt text](./images/ssh%20key%20added.PNG)

## Test if you can login to NFS and other servers via ansible on terminal without pem key

![alt text](./images/ssh%20key%20added.PNG)


## Go to ansible project on vs code

Update dev.yml

[nfs]
172.31.82.179 ansible_ssh_user='ec2-user'

[webservers]
172.31.92.195 ansible_ssh_user='ec2-user'
172.31.82.66 ansible_ssh_user='ec2-user'

[db]
172.31.89.191 ansible_ssh_user='ec2-user' 

[lb]
172.31.19.152 ansible_ssh_user='ubuntu'

Update common.yml

Commit your code into GitHub:

use git commands to add, commit and push your branch to GitHub.
git status

git add <selected files>

git commit -m "commit message"
Create a Pull request (PR)

Wear a hat of another developer for a second, and act as a reviewer.

If the reviewer is happy with your new feature development, merge the code to the master branch.

Head back on your terminal, checkout from the feature branch into the master, and pull down the latest changes.

![alt text](./images/common%20file.PNG)


## Check jenkins

![alt text](./images/jnkins%20jobs%20archive.PNG)


Once your code changes appear in master branch – Jenkins will do its job and save all the files (build artifacts) to /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/ directory on Jenkins-Ansible server.


## ANSIBLE TEST


Connect to ansible /jenkins server

![alt text](./images/build1.PNG)
![alt text](./images/build2%20triggered.PNG)
![alt text](./images/build%20artifact.PNG)
![alt text](./images/build%20artifact1.PNG)
![alt text](./images/build4%20artifacts.PNG)


## Confirm wireshark install on the servers.


![alt text](./images/wireshake%20confirmed.PNG)



## Go back to git terminal

git checkout project-11

Run the commands

Update the playbook

Sync with github

Run the playbook

ansible-playbook -i /var/lib/jenkins/jobs/ansible/builds/10/archive/inventory/dev.yml /var/lib/jenkins/jobs/ansible/builds/10/archive/playbooks/common.yml 


Success

Check if it worked on NFS server

![alt text](./images/2nd%20task.PNG)
![alt text](./images/task2.PNG)
![alt text](./images/final%20result.PNG)

![alt text](./images//jenkins_ansible.png)
