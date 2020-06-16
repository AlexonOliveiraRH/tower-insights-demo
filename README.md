# Deploy "Ansible Linux Automation Workshop" Workshop in RHPDS
Select nearest region and deploy

# Edit ansible.cfg and update location of inventory host file
```
[defaults]
stdout_callback = yaml
connection = smart
timeout = 60
deprecation_warnings = False
host_key_checking = False
retry_files_enabled = False
# Update student1 to student2 etc. if needed
inventory = /home/student1/lab_inventory/hosts
```

# Edit extra_vars.yml and update with needed credentials
You need to make changes to ansible.cfg file if the studentid given is not student1. This can happen if you did not deploy the RHPDS demo yourself.
```
# tower credential
towuser: admin
towpass: <ChangeMe>

# managed nodes credential
machinesshuser: student1
machinesshpass: <ChangeMe>

# insights scm credential
rhnuser: <ChangeMe>
rhnpass: <ChangeMe>

# student number given by rhpds for ssh
studentid: student1

# to unique identify managed host for each deployment
# country: anz
# country: ind
# country: sgp
country: towerinsightsworkshop
```
# Use ansible-vault to protect your extra_vars.yml file
```
$ ansible-vault encrypt extra_vars.yml
```
# Run Ansible Playbook to setup demo
```
$ ansible-playbook setup-aotdemo-tower.yml -e @extra_vars.yml --ask-vault-pass -v
```
