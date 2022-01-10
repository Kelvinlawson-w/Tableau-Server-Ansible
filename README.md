# Tableau-Server-Ansible

### These are the instructions to complete the installation of the Tableau Server

Step 1- Build the inventory file with dns names of the servers 

Step 2 - Open up playbook-staging.yml and change the path to the role

Step 3 - Run the playbook to install master node:

```
ansible-playbook playbook-staging.yml -i inventory.yml --limit 'MASTER_HOSTNAME' -u ubuntu --key-file=Tableau-Server-CF.pem -e '{"tableau_server_version":"2021.4.2", "tsm_user":"tsmadmin", "tsm_password":"P@ssw0rd", "master":"true"}'
```

### <u>Required Variables</u>
- MASTER HOSTNAME: Hostname of the Master Node 
- Key-file: Private SSH Key
- tsm_user: TSM Admin Username
- tsm_password: TSM Admin Password  

Step 4 - Complete Changes through GUI and activate license

Step 5 - Generate bootstrap.json file from master node and copy under the files directory of the Ansible role

Step 6 - Run the playbook to install the Worker Node:

```
ansible-playbook playbook-staging.yml -i inventory.yml -u ubuntu --limit 'WORKER_HOSTNAME' --key-file=Tableau-Server-CF.pem -e '{"tableau_server_version":"2021.4.2", "tsm_user":"tsmadmin", "tsm_password":"P@ssw0rd", "worker":"true"}'
```

### <u>Required Variables</u>
- WORKER HOSTNAME: Hostname of the Worker Node 
- Key-file: Private SSH Key
- tsm_user: TSM Admin Username
- tsm_password: TSM Admin Password  
