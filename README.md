# Snipe-It - Docker Compose files
Snipe-IT is a IT asset management tool.

This repo includes 3 docker-compose files. For production environments, it's recommended to use an external SMTP server.

To ensure the Snipe-It service starts properly, the Docker Compose configuration checks the status of the database service before initiating Snipe-It. This is done by defining service dependencies  with `depends_on` and using health checks to verify the database service is ready. These checks prevent the Snipe-It service from starting too early, which could result in a '500 Error' if the database isn't fully operational.

## The Docker-compose files:  
1. No mails (docker-compose.local.yml)
2. Logging with Mailhog (docker-compose.mailhog.yml)
3. Mails with SMTP server (docker-compose.smtp.yml)

## Setup 
**API Key**  
Before lauching the containers with the docker-compose command you need to create a API Key.   

```
docker run --rm snipe/snipe-it
```
This will output something like:  
```
Please re-run this container with an environment variable $APP_KEY
An example APP_KEY you could use is:
base64:MES/9XABxAy/AXROkMJwW/kF374Y/Ck61Lc4BvWlrDs=
```
Replace the environment value `GENERATED_KEY` behind `APP_KEY=` with the generated value `base64:MES/9XABxAy/AXROkMJwW/kF374Y/Ck61Lc4BvWlrDs=`

# Running the containers
And now, you can start the containers:  

```
docker compose -f <docker-compose.xyz.yml> up
```

Snipe-It should be available at:
`http://localhost:8888`


# Links
https://snipe-it.readme.io/docs/docker  
https://snipe-it.readme.io/docs/configuration  
https://github.com/snipe/snipe-it/tree/master   


# License
MIT
