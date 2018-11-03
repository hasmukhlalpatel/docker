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

Run docker stack deploy -c stack.yml mongo (or docker-compose -f stack.yml up

[<img src="https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png">](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/hasmukhlalpatel/docker/master/mongo-express/stack.yml)

## NodeJs App
### Commands
```
docker build -t <user name>/nodeJsApp .

docker run -p 49160:8080 -d  <user name>/nodeJsApp
```


