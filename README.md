# dockerfiles-centos-ssh

# Building & Running

Copy the sources to your docker host and build the container:

	# docker build --rm -t <username>/ssh:centos7 .

To run:

	# docker run -d -p 22 <username>/ssh:centos7
# docker run -d -p 22 --network=bridge root/ssh:centos7

Check ip: 
ip a 

-- find docker keyword 

Get the port that the container is listening on:

```
# docker ps
CONTAINER ID        IMAGE                 COMMAND             CREATED             STATUS              PORTS                   NAMES
8c82a9287b23        <username>/ssh:centos7   /usr/sbin/sshd -D   4 seconds ago       Up 2 seconds        0.0.0.0:49154->22/tcp   mad_mccarthy        
```

To test, use the port that was just located:

	# ssh -p xxxx user@localhost 

	#ssh -p 49154 user@127.17.0.2


	 ssh -p 32776 user@127.17.0.2
	 ssh -p 32776 user@172.17.0.2
     password: newpass


Create pem file: 
cd ~/.ssh
mv id_rsa id_rsa.pem 
ssh-copy-id -i id_rsa.pub  user@172.17.0.2
ssh -i /home/cuongta/Mess/id_rsa.pem user@172.17.0.2


#Ansible with playbook
ansible-playbook -i hosts -b -e ansible/vars.yml deploy_django_project_force.yml