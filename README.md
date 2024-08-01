# About
- forked from weslambert/velociraptor-docker. Thank you for the contribution. 
- Enable API for use in automated workflow

# velociraptor-docker
Run [Velocidex Velociraptor](https://github.com/Velocidex/velociraptor) server with Docker

#### Install

- Ensure [docker-compose](https://docs.docker.com/compose/install/) is installed on the host
- `git clone https://github.com/ilostab/velociraptor-docker`
- `cd velociraptor-docker`
- Change credential and IP values in `.env` as desired
- `docker-compose build --no-cache`
- `docker-compose up` (or `docker-compose up -d` for detached)
- Access the Velociraptor GUI via https://\<hostip\>:8889 
  - Default u/p is `admin/admin`
  - This can be changed by running:
  `docker exec -it velociraptor ./velociraptor --config server.config.yaml user add admin password --role administrator` or in GUI. 
- Access the Velociraptor API with:
  `velociraptor --api_config api.config.yaml query "SELECT * FROM info()" --format jsonl | jq`
  - Or access it using python as shown here: https://docs.velociraptor.app/docs/server_automation/server_api/ 

#### Notes:
Linux, Mac, and Windows binaries are located in `/velociraptor/clients`, which should be mapped to the host in the `./velociraptor` directory if using `docker-compose`.  There should also be versions of each automatically repacked based on the server configuration.

Once started, edit `server.config.yaml` in `/velociraptor`, then run `docker-compose down/up` for the server to reflect the changes
