# Prerequisites
- Ansible 2.10
- Ansible Azure [extension](https://galaxy.ansible.com/azure/azcollection)
- Ansible MySQL [extension](https://galaxy.ansible.com/community/mysql)
# Setup 
## Install Python3 requirements using pip
```user@localhost:~/Project-Endava# pip3 install -r requirements.txt```
## Complete the infrastructure setup
```user@localhost:~/Project-Endava# ansible-playbook playbooks/infrastructure-init.yaml```
- The following will be asked when starting the script:
- These will be the passwords for the services that are to be created 
```Enter the Web App server's administrator password```
```Enter the DB server's administrator password```
## Add the newly created services to your Ansible hosts file
```user@localhost:~/Project-Endava# vim /etc/ansible/hosts```
## Deploy the MySQL DB 
```user@localhost:~/Project-Endava# ansible-playbook playbooks/mysql-setup.yaml```
- Here you need to provie the previously defined MySQL server's password
## Deploy the Python web app
```user@localhost:~/Project-Endava# ansible-playbook playbooks/webapp-setup.yaml```
- Here you need to provie the previously defined Web app server's password
- Here you need to provie the previously provided MySQL (during the execution of infrastructure-setup.yaml) server's hostname (URL)
- Here you need to provide the previously defined MySQL server's admin password
## Verify by visiting the IP address of your Azure VM:
[Example](https://imgur.com/a/mWlR40w)
# Installing Monitoring system
## Create a NetData account
From this [link](https://www.netdata.cloud/)
## Edit the ./netdata/vars/main.yml file
And replace "claim_token" and "claim_rooms" with the data from your NetData account
## Edit the ./ansible-quickstart/hosts file
And add the IP address of the host that's to be monitored, along with the SSH Key and the SSH username
## Run the NetData playbook
```ansible-playbook -i hosts ./ansible-quickstart/tasks/main.yml```
## Verify the setup
[Example](https://imgur.com/a/RuEDwGR)

