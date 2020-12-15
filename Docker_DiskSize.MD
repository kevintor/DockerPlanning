There is a size limit to the Docker container known as base device size. The default value is 10GB. This value can be changed to allow the container to have more size using 
>dockerd --storage-opt dm.basesize=50G.

This will give the container a rootFS size of 50GB.

Follwoing is the commend to perment change default docker disk size. 

1. Please run the next set of commands in all of your CentOS machines:

>sudo service docker stop
>OR
>sudo systemctl stop docker

2. Create/edit the following file:
>/etc/docker/daemon.json
>with the following content:
>{
>        "storage-driver": "devicemapper",
>        "storage-opts": [
>                "dm.basesize=40G"
>        ]
>}

3. Remove the default setting
   
>sudo rm -rf /var/lib/docker

4. Restart docekr servcce

>sudo service docker start
>OR
>sudo systemctl start docker
