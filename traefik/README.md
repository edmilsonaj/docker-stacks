# Traefik

## Before deploying Traefik, you should create the docker network it will use and tag the node it will run

To create the docker network

`docker network create --driver=overlay traefik-public`

To tag the node, first you will need the node ID

`export NODE_ID=$(docker info -f '{{.Swarm.NodeID}}')`

Then tag the node

`docker node update --label-add traefik-public.traefik-public-certificates=true $NODE_ID`

After that, you can deploy Traefik:

`docker stack deploy -c traefik.yml traefik`

Compose file and tutorial inspired by the one on [Docker Swarm Rocks](https://dockerswarm.rocks/)
