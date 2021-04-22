# Hadoop HDFS & MapReduce Multi Node Cluster Setup on AWS EC2 Instances using Ansible Automation

## Let's see the problem Statement :

1. Create Ansible Role to launch 9 AWS EC2 Instances.
2. Dynamically fetch the IPs & create the Inventory to run the further Ansible Roles on those Instances.
3. Create Role to configure Hadoop Name Node (Master), Data Node (Worker), Job Tracker Node, Task Tracker Node & Client Node.
4. Finally configure 1st & 2nd & 3rd Instance as Name Node, Job Tracker & Client Node, also configure other 3 systems as Data Node & another 3 as Task Tracker.

### Video Demonstration : https://bit.ly/3tICiLd

#### How to do this practical on your system :

- Install **Ansible v 2.10** on your local linux system.

- Next clone this repository & go inside the folder **"hadoop-ws"**. This is our workspace & it contain everything.

- In this workspace we need to put two files - **hadoop_instance.pem** file & **cred.yml** file.

- Now this **"hadoop_instance.pem"** file, you need to create on your AWS Account & then download the file in your Workspace - **"hadoop-ws"**.

- Next run `chmod 400 hadoop_instance.pem` to secure your AWS key pair from other user on your linux system.

- Next run `ansible-vault create cred.yml` & it will open the vi editor on your linux system. So here put your AWS access key & secret key in YAML format.

##### This file data should look like

`access_key : ABCDEFGHIJK` <br /> `secret_key : abcdefghijk12345`

- Next go to **"hadoop-ws/roles/ec2/vars/"** folder & edit the **"main.yml"** file. Here you only just need to change the **"subnet_name"** variable with your **"AWS account subnet id"**.

- Note : As I am using AWS default VPC, that's why I haven't mentioned that on my **"hadoop-ws/roles/ec2/tasks/main.yml"** file. But if you want to use your won VPC, then you need to put that extra option here.

#### Finally it's time to Deploy this whole setup, For that run - `ansible-playbook setup.yml --ask-vault-pass` & provide your vault (cred.yml) password & see the magic of Ansible.
