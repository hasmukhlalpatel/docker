# Commands
## Up and running
  ### detached
  -docker-compose up -d
  ### attached
  -docker-compose up 
## Check that the app is running 
docker-compose ps
## Bring the app down
docker-compose down --volumes
docker-compose down

# Push the generated image to the registry
docker-compose push
