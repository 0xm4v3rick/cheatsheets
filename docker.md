## Docker cheat sheet
These are frequently used commands for quick reference/personal use **not a complete list**

**Pulling Docker images**  
docker pull _image_\__name_  

**List images**  
docker images  

**Running available Docker image [creates a container]**

docker run --name _image_\__name_ -t _image_\__tag_  

**List container Details [lists running containers]**  
docker ps  

**List container Details [lists all containers]**  
docker ps -a

**List all container IDs**  
docker ps -aq

**Stop a container**  
docker stop *container_id*  
**OR**  
docker stop _container_\__name_  

**Delete a container**  
docker rm *container_id*  
**OR**  
docker rm _container_\__name_  

**Delete all containers**  
docker rm $(docker ps -aq)

**Delete an image**  
docker rmi _image_\__name_  
**OR**  
docker rmi _image_\__id_  

**Build image from Dockerfile [note the dot at the end]**  
docker build -t _image_\__tag_ .  

**Bash shell on active/running container in case of Linux distro **  
**[default user privileges]**  
docker exec -it _container_\__name_ bash  
**[root privileges]**  
docker exec -u 0 -it _container_\__name_ bash

**Copy file from local system into container**  
docker cp _source_\__file_\__path_ _container_\__name_:_destination_\__file_\__path_  
e.g. docker cp /home/user/test hopeful_franklin:/home/user/test

**Copy file from container into local system**  
docker cp _container_\__name_:_source_\__file_\__path_ _destination_\__file_\__path_  
e.g. docker cp hopeful_franklin:/home/user/test /home/user/test

**Docker image run with port mapping [single port] [protocol is required for UDP else optional]**  
docker run -p _host_\__port_:_container_\__port_/_protocol_ _image_\__name_  
e.g. docker run -p 80:80 test  
e.g. docker run -p 161:161/udp test  

**Docker image run with port mapping [multiple port]**  
docker run -p _host_\__port1_:_container_\__port1_ -p _host_\__port2_:_container_\__port2_ _image_\__name_  
e.g. docker run -p 22:22 -p 80:80 test  

**Import image**  
docker save _image_\__name_ -o _filepath.tar_  

**Import container**  
docker import _container_\__id_ -o _filepath.tar_  

**List latest container ID**  
docker ps -q -l  

**Restarting exited container [latest container] [attach will output the docker log on screen]**  
docker start $(docker ps -q -l)  
docker attach $(docker ps -q -l)  
