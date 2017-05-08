# docker notes  
some of these commands are windows specific, sorry  
### docker machine
start docker machine  
`docker-machine start`  
set docker environment variables  
`@FOR /f "tokens=*" %i IN ('docker-machine env') DO @%i`  
get docker machine ip  
`docker-machine ip`
### docker images
build docker image  
`docker build -t [tagname] .`  
list docker images  
`docker images`  
list all docker images  
`docker images -a`  
remove an image  
`docker rmi IMAGEID`  
remove all images  
`docker images -aq | xargs docker rmi`  
### docker containers
list docker conatiners  
`docker ps`  
list all docker containers  
`docker ps -a`  
stop a container  
`docker stop CONTAINERTAG`  
stop all containers  
`docker ps -aq | xargs docker stop`  
remove a container  
`docker rm CONTAINERTAG`  
remove all containers  
`docker ps -aq | xargs docker rm`  
