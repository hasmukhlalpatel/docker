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

## 2. WordPress MySql

## 3. Mongo - Express

#### Urls
Elastic [http://localhost:8081/](http://localhost:8081/)
#### Commands
$ docker exec -it some-mongo bash

$ docker logs some-mongo

$ docker run -it --link some-mongo:mongo --rm mongo mongo --host mongo test

Run docker stack deploy -c stack.yml mongo (or docker-compose -f stack.yml up

![Try on PWD](https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png)

[<img src="http://www.google.com.au/images/nav_logo7.png">](http://google.com.au/)

[![Foo](http://www.google.com.au/images/nav_logo7.png)](http://google.com.au/)
