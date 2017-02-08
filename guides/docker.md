# docker notes
start docker machine  
`docker-machine start`  
set docker environment variables  
`@FOR /f "tokens=*" %i IN ('docker-machine env') DO @%i`  
get docker machine ip  
`docker-machine ip`  
build docker image  
`docker build -t [tagname] .`  
list docker images  
`docker images`  
