---
published: true
---
error:
```
eight@eight-PC ~/Downloads/New folder (7)
$ docker search nextcloud -f is-official=true
Warning: failed to get default registry endpoint from daemon (error during connect: Get https://192.168.99.100:2376/v1.37/info: dial tcp 192.168.99.100:2376: connectex: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.). Using system default: https://index.docker.io/v1/
error during connect: Get https://192.168.99.100:2376/v1.37/images/search?filters=%7B%22is-official%22%3A%7B%22true%22%3Atrue%7D%7D&limit=25&term=nextcloud: dial tcp 192.168.99.100:2376: connectex: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
eight@eight-PC ~/Downloads/New folder (7)
$ docker pull nextcloud
Using default tag: latest
Warning: failed to get default registry endpoint from daemon (error during connect: Get https://192.168.99.100:2376/v1.37/info: dial tcp 192.168.99.100:2376: connectex: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.). Using system default: https://index.docker.io/v1/
error during connect: Post https://192.168.99.100:2376/v1.37/images/create?fromImage=nextcloud&tag=latest: dial tcp 192.168.99.100:2376: connectex: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
```

A:

your docker CLI cannot work without daemon. Run the Docker daemon (you probably have an icon on your desktop) and once it reports that it is ready, try again your commands.

ref:
https://stackoverflow.com/questions/43058226/docker-warning-failed-to-get-default-registry-endpoint-from-daemon