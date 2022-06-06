## How to ssh between containers (encryption, signing, and ssh)

- Generate ssh keys
```
ssh-keygen -t rsa
cat /home/rawda/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 400 ~/.ssh/authorized_keys
```

- Run 2 containers with Ubuntu:20.04 
- - We will create container1 and contianer 2
```
docker run -it --name container1 ubuntu:20.04
docker run -it --name container2 ubuntu:20.04
```

- install vim (to allow editing some file) for each container
```
apt-get update
apt-get install apt-file
apt-file update
apt-get install vim 
```

- Install ssh server on each container
```
apt-get update
apt-get openssh-server
vi /etc/ssh/sshd_config --> change Port 22 to Port 2222 
sudo service ssh
```

- Add your public key in the authorized_keys file for each container
```
mkdir ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 400 ~/.ssh/authorized_keys
vi ~/.ssh/authorized_keys --->  add public key
```

- get container IPs
```
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container1
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container2
```

- ssh to the container using their IPs 
for example IPs: 172.17.0.4, 172.17.0.5
```
ssh-copy-id root@172.17.0.4
ssh root@172.17.0.4
ssh-copy-id root@172.17.0.5
ssh root@172.17.0.5
```

- ssh to the first container, then ssh to the second container from the first, (ssh-agents)
```
eval `ssh-agent`
ssh-add
ssh -A root@172.17.0.4
ssh root@172.17.0.5
```


