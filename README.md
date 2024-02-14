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
FYI https://github.com/parc02/docker-nginx-vhost/issues/2#issue-2133476326
### Step 3
- copy local default.conf into (lb) docker container -> lb:/etc/nginx/conf.d
```
sudo docker cp default.conf lb:/etc/nginx/conf.d
```
- move local default.config to lb folder and make serv-a, serv-b folder

### Step 4
- make index.html file to serv-a serv-b folder & copy to docker container
```
$sudo docker cp serv-a/index.html serv-a:/usr/share/nginx/html
$sudo docker cp serv-b/index.html serv-b:/usr/share/nginx/html
$tree
.
├── README.md
├── lb
│   └── config
│       └── default.conf
├── serv-a
│   └── index.html
└── serv-b
    └── index.html
```

### Step 5
- install ping in container(docker)
```
$ apt update
$apt install iputils-ping
$apt install telnet
```


### Step 6
```
$sudo docker network ls

NETWORK ID     NAME      DRIVER    SCOPE
438ec9964d9e   bridge    bridge    local
a5597bd84d88   host      host      local
ed1a5e80b850   none      null      local
```


# Docker inspection
- https://github.com/parc02/docker-nginx-vhost/issues/4#issue-2133493480

# Dockerfile
- https://github.com/parc02/docker-nginx-vhost/issues/6#issue-2133716937
