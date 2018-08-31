# Project Description
This project will deploy java-1.8.0-openjdk and apache-tomcat-7.0.90 on a single node of Alibaba Cloud using agentless automation technology Ansible. Ansible using powerful automation language YMAL to excute command on target host or hosts remotely through SSH connection. The ansible scripts for implementation are provided. Those scripts will make the whole deployment process nice and esay.
There are three main roles involved in this project:
- `selinux` is responsible for EPEL repository installation;
- `tomcat` is responsible for installation of java JDK and apache tomcat server as well as the configuration of environment variables;
- `stop-tomcat` is responsible for shuting down tomcat server.

# Operating System
 - Localhost: ubuntu-18.04.1-amd64
 - Targethost:  CentOS 7.3 64

# Implementation Steps
1. Use command `ssh-keygen` to generate your private and public key, use `ssh-copy-id -i` to copy public key to targethost for SSH connection.
2. Install the latest version of Ansible to localhost using `apt-get install ansible`.
3. Download the latest apache tomcat server binaries and copy to your current working directory.
4. Execute the following command for syntax checking of ansible playbook.
   ```
   ansible-playbook -i hosts install.yml --syntax-check
   ```
5. Execute teh following command and then the automation deployment shall begin.
   ```
   ansible-playbook -i hosts install.yml
   ```
   
# Useful notes
- In this project, environment variables like `JAVA_HOME` and `CATALINA_HOME` are specified in `/etc/profile`  
- If you download the different version of apache tomcat server binaries, the script should be changed correspondingly in `roles/tomcat/tasks/main.yml`.
- War files are stored in `roles\tomcat\files\webapps`
