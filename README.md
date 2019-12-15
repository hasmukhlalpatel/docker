# docker  compose files
## 1. Elasticsearch Kibana
### Linux requires following settings:
```
    resolve low virtua lmemory issue.
    $ sudo osysctl -w vm.max_map_count=262144
``` 
#### Urls
Elastic [http://localhost:9200/](http://localhost:9200/)

Kiban   [http://localhost:5601/](http://localhost:5601/)

[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/elasticsearch-kibana/docker-compose-hub.yml)

## 2. WordPress MySql

[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/WordPress/docker-compose.yml)

## 3. Mongo - Express

#### Urls
Express [http://localhost:8081/](http://localhost:8081/)
#### Commands
$ docker exec -it some-mongo bash

$ docker logs some-mongo

$ docker run -it --link some-mongo:mongo --rm mongo mongo --host mongo test

Run docker stack deploy -c stack.yml mongo or docker-compose -f stack.yml up

[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/mongo-express/stack.yml)

## 3. RabbitMQ
[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/rabbitmq/docker-compose.yml)

## 4. Orchard CMS - orchardcore-cms
[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/orchardcms/stack.yaml)


## NodeJs App

# docker swarm setup commands
## Setup Docekr swarm
### init
```
 docker swarm init --advertise-addr {IP addr}
```
### join
```
 docker swarm join --token SWMTKN{your token}
```
### leave
```
 docker swarm leave --force
```

# Docker compose Commands
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

## Deploy a service to the swarm
### Run the following command:
```
docker service create --replicas 1 --name helloworld alpine ping docker.com

docker service create \
  --name my-web \
  --publish published=8080,target=80 \
  --replicas 2 \
  nginx

docker service create --name nginx --publish published=80,target=80 nginx

docker service create --name dns-cache -p 53:53 dns-cache 

docker service create --name dns-cache \
  --publish published=53,target=53 \
  --publish published=53,target=53,protocol=udp \
  dns-cache
  
 docker service create --name dns-cache \
  -p 53:53 \
  -p 53:53/udp \
  dns-cache
```
### Inspect
```
docker service inspect --format="{{json .Endpoint.Spec.Ports}}" helloworld
```

### To see the list of running services:
```
docker service ls
```
### To change the desired scale of the service running in the swarm::
```
docker service scale <SERVICE-ID>=<NUMBER-OF-TASKS>
```
#### Example
```
docker service scale helloworld=5
```
### To see the service status
```
docker service ps <SERVICE-ID>
```
#### Example
```
docker service ps helloworld
```

## Apply rolling updates to a service
```
docker service create \
  --replicas 3 \
  --name redis \
  --update-delay 10s \
  redis:3.0.6
  
  Or
  
  docker service update --image redis:3.0.7 redis
  
  Or
  
  docker service update redis
```
### Inspect the redis service:
```
docker service inspect --pretty redis
```

## Drain a node on the swarm
```
docker node ls

docker node update --availability drain worker1

docker node update --availability active worker1

docker node inspect --pretty worker
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

