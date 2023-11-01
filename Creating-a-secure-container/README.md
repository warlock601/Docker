# Creating a Secure Container in Docker.
By default all the containers in the same host will be able to communicate with one another, which makes them vulnerable. So, to avoid this we will create a container in a separate network.<br />
<br />
First we create a new custom network (bridge network) using command:
```bash
  docker network create network_name            
```
Then we create a Docker container in this network by using the command:
```bash
  docker run  -d  --name container_name  --network=network_name  image_name               
```
we can check and list all the networks in our host using:
```bash
  docker network ls
```
Now Login into any other container on this host and then try to ping this new container, it won't be reachable.
```bash
  docker exec -it container_name /bin/bash
  ping ip-address
```

