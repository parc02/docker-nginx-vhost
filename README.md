# docker-nginx-vhost

### Step 1
- remove all images and containers
```
$ sudo docker rm (container id)
$ sudo docker rmi (image id)
--------------------------------------------------------------------------------
<result>
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
FYI
![image](https://github.com/parc02/docker-nginx-vhost/assets/148880521/7e817524-654c-4ead-aa3f-a4534d7bdc47)
