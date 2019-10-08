# Commands
## Up and running
  ### detached
  - docker-compose up -d
  ### attached
  - docker-compose up 
## Check that the app is running 
docker-compose ps
## Bring the app down
docker-compose down --volumes
docker-compose down

# Push the generated image to the registry
docker-compose push

# Run manualy 
docker pull rabbitmq:3-management

docker run -d -p 15672:15672 -p 5672:5672 --name rabbit-test-for-medium rabbitmq:3-management

Test the image by opening “http://localhost:15672/#/” in your browser. The default login is guest guest: you should see the RabbitMQ management GUI.

--https://levelup.gitconnected.com/rabbitmq-with-docker-on-windows-in-30-minutes-172e88bb0808
