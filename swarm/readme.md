# commands
## Setup Docekr swarm
### inti
```
 docker swarm init --advertise-addr {IP addr}
```
### join
```
 docker swarm join --token SWMTKN{your token}
```

### get token to join as manager
```
docker swarm join-token manager
```

### get token to join as worker
```
docker swarm join-token worker
```

### leave
```
 docker swarm leave --force
```

### node list
```
docker node ls
```

# Commands
## Test the app with Compose
```
- docker-compose up
- docker-compose up -d
```
## Check that the app is running with docker-compose ps
```
docker-compose ps
```
## Bring the app down
```
docker-compose down --volumes
```

## Set up a Docker registry
1. Start the registry as a service on your swarm:
```
 docker service create --name registry --publish published=5000,target=5000 registry:2
```
2. Check its status with docker service ls:
```
 docker service ls
```

## Push the generated image to the registry
```
docker-compose push
```

## Deploy the stack to the swarm
1. Create the stack with docker stack deploy:
```
  docker stack deploy --compose-file docker-compose.yml stackdemo
```
2. Check that it’s running with docker stack services stackdemo:
```
  docker stack services stackdemo
```
3. Bring the stack down with docker stack rm:
```
  docker stack rm stackdemo
```
4. Bring the registry down with docker service rm:
```
  docker service rm registry
```
5. if you’re just testing things out on a local machine and want to bring your Docker Engine out of swarm mode, use docker swarm leave:
```
  docker swarm leave --force
```


