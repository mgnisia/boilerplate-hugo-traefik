# Boilerplate for Hugo Deployment

This repo contains the basic layout for the deployment of a [hugo](https://github.com/gohugoio/hugo) website with [traefik](https://github.com/containous/traefik) and [docker](https://www.docker.com/). The `site` folder contains your hugo website and the necessary files. The main idea for this repository is based on the docker image of [jojomi](https://hub.docker.com/r/jojomi/hugo). 

Modifications to the setup of `jojomi` are:

- replacing `nginx` with the speed version `pagespeed/nginx-pagespeed`
- replacing the target directory from `/var/www` to ``

## Assumptions:

- You have installed `docker-compose`, you can install it via [setup](https://docs.docker.com/compose/install/)
- Traefik is already running in a different process/container
- you defined an external network for all you `traefik` related containers, if you need to create one just run `docker create yournetwork`
- in the `config.toml` **no** base url is defined, if you define it there you have to comment out the line in the `docker-compose` file

## Deployment

1. Put you hugo website into the `site` folder
2. Create a corresponding folder for the deploy, in the docker-compose file you replace the folder location `/home/username/folder_for_deployment`
3. Set you network
4. Define the Host rule
5. run `docker-compose up -d`
6. You should now your `hugo` website :slush:
