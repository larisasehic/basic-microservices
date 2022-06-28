# Basic Microservices - Docker

Simple application with node.js and spring-boot composed using Docker (docker-compose).

## Run the app

docker-compose build : 
- Generate Spring-boot-app image. Docker-compose file will execute the back/Dockerfile. I used a multi-stage docker image. Git repo will be cloned (clone stage) and used in builder stage. Final image will be composed in the final stage of the Dockerfile. 
- Generate spring-boot-app image. Docker-compose file will execute front/Dockerfile, git repo will be cloned and final image will be built.

docker-compose up -d: 
- postgres:10-alpine docker image will be downloded from Docker Hub. postgrsql container will be built. 
- spring-boot-app container will be built. 
- node-app container will be built.

### Notes
Application.yml file was modified (location back/application.yml)
