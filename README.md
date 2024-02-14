# docker-nginx-vhost

### Step 1
- remove all images and containers
```
$ sudo docker rm (container id)
$ sudo docker rmi (image id)
--------------------------------------------------------------------------------
<results>
$ sudo docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
$ sudo docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
### Step 2
```
$ docker run -itd -p 8002:80 --name serv-a nginx
$ docker run -itd -p 8003:80 --name serv-a nginx
$ docker run -itd -p 8001:80 --name lb nginx:latest
```
