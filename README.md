# docker_aliases
A list of nice bash functions to save time while using docker.

Add this content on your ~/.bash_profile, ~/.zshrc.local or similar:

dockerstop() { docker stop $(docker ps -a -q) }
dockerrm() { docker rm $(docker ps -a -q) }
dockerrmi() { docker rmi $(docker images -q) -f }
dockerclean() { dockerstop; dockerrm; dockerrmi;}
dockerexec() {docker exec -it $(docker ps -qa -f "name=$1_1") $2 }

## What each command does?

### dockerstop
Well, stops all containers.

### dockerrm
**Yellow Alert**: This will destroy all containers.

### dockerrmi
**Red Alert**: This will delete all images located on you docker.

### dockerclean
**Double Red Alert**: This will stop all containers, then will destroy all containers and remove all images stored on you docker.

### dockerexec <name of container> <shell>
This is cool, helps you get a shell in a container.
Ex: dockerexec mysql_container_1 bash
Where $1 is the name of the container and the $2 is the shell

Credits to **https://github.com/DiSiqueira**
