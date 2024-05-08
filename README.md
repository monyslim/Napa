# nodeJS-image-upload

Simple NodeJS Express Program get files as input from user and upload it to the server. 

To install necessary packages and start the server: 
    
    npm install && npm start
    On you terminal type cp .env-example .env to create an .env file for you



## - PLEASE NOTE
- 1. Create the 'napa-network' network first: 
```sh
    docker network create napa-network
```

- 2. The command for **running mongodb**
``` sh
    docker run -d --network napa-network \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    -e MONGO_INITDB_DATABASE=napa
    --name mongodb \
    mongo:5.0
```
- 3. The command for **running mongo-express**
```sh
    docker run -d -p 8081:8081 --network napa-network \
    -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
    -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
    -e ME_CONFIG_MONGODB_SERVER=mongodb \
    -e ME_CONFIG_MONGODB_URL:mongodb://admin:password@mongo:27017 mongo-express
    --name mongo-expresso \
    mongo-express
```

Remember that you need to also run the built image for the application: 
```sh
    docker run -d -p 3000:3000 --network napa-network \
    --name napa-app \
    <name of image>
```



