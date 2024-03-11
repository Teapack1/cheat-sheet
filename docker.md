# Docker


### Infos

- Run container:<br>
`docker start homeassistant`

- Stop container:<br>
`docker stop homeassistant`

- Remove container:<br>
`docker rm homeassistant`


- This command shows all containers:<br>
`docker ps -a`

- Go inside the container:<br>
`docker exec -it homeassistant bash`


- By default, docker-compose up starts all the services (and any linked services) defined in the docker-compose.yml file. With -d, you free up the terminal while the containers run in the background.:<br>
`docker compose up -d`
