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
  apt-get update
  apt-get install iputils-ping                  //to install the ping utility
  ping ip-address
```

![Screenshot 2023-11-02 090707](https://github.com/warlock601/Docker/assets/32487715/89c058c8-ca04-4121-91d7-ac07b2c5822b)
<br />
<br />
When we are trying to ping a container within the defualt bridge network, it will look like this:
![Screenshot 2023-11-02 091210](https://github.com/warlock601/Docker/assets/32487715/59d57c40-b36b-494c-89fd-dfebc80ae9ed)
