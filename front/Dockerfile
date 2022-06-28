#cloning git repo
FROM ubuntu as clone

#install git
RUN apt-get update && \
     apt-get install -y git

RUN cd /home/ && \
    git clone https://github.com/kkenan/basic-microservices.git

FROM node:9.9.0-alpine

RUN mkdir -p /home/basic-microservices/node-app

WORKDIR /home/basic-microservices/node-app

# copy from node-app to current workdir
COPY --from=clone /home/basic-microservices/node-app/ .

# install project dependencies npm version 5.6.0
RUN npm install npm@5.6.0
# copy project files and folders to the current working directory node-app
COPY . .
#App will listen on port 8081 per readme.md
EXPOSE 8081
#Run node.js app
ENTRYPOINT ["node","index.js"]