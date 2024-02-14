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
FYI
![image](https://github.com/parc02/docker-nginx-vhost/assets/148880521/7e817524-654c-4ead-aa3f-a4534d7bdc47)

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


