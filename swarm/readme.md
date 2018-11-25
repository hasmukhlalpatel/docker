# commands
## Deploy the stack to the swarm
 docker stack deploy --compose-file docker-compose.yml stackdemo
 ## remove 
 docker stack rm stackdemo
 ## remove registry
 docker service rm registry
 
 #Docekr swarm
 ## inti
 docker swarm init --advertise-addr {IP addr}
 ## join
 docker swarm join --token SWMTKN{your token}
 ## leave
 docker swarm leave --force
