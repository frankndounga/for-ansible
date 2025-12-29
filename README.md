# serie for testing all day to day ansible modules

I deployed 5 machine on my proxmox server. 
- one manager which is an ubuntu server called node-manager
- 3 node also ubuntu servers node1, 2 and 3.
 - to really test the organisation in the inventory file i decide to put the node1 in the group web and node2 and 3 in the group storage- the last machine is a centos server place in the redhathost group also to test different organistation with groups 

i will test the different ansible module in adhoc mode as well as with playbooks. in the begining sensitive infos as passwords for ssh can be found in the in the inventory file as configuration variables. Something not to do in production of course but as i will also test the ansible-vault feature and those machines are all in my local servers, i will do that.

## create an inventory file and test configuration for group_vars and host_vars

instead of using inventory file in the .ini format i prefer to use it in the .yml format. For me it is more clear an organize and i stay with only one data language as well.
I try var1 i configure . certain as a group variable and others as host variables with the debug module. just in adhoc
ansible all -m debug -a "msg={{ var1 }}" (NB: the inventory is already passed in the ansible.cfg at the root folder)
we can check variable on each host by listing the inventory file with the command ansible-inventory  useful to really see the structure we configure as we made it on different files. options ( --list, --graph, --output) can be use
very useful to see all the configuration tree

## i try a basic playbook to install nginx on debian base hosts and redhat base hosts just to see if everything work well
this is the play.yml file

## As i have a small task to do with the command sed with the /etc/passwd file i will start by using the module user to create multiple users as well as also directly see the syntax for using loops in a playbook. we directly specify the password here but as i sais i am not using ansible vault at the moment. then i hashed the password directly in the playbook.


