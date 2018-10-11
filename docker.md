# Docker

## Useful containers

Official Redis

* `docker run --rm -p6379:6379 -it redis`

Redis-cli (auto-connects to localhost)

* `docker run -it --rm --entrypoint /bin/sh goodsmileduck/redis-cli`
* `redis-cli -h 172.17.0.1`

Visualise docker image tree (--tree on images is deprecated)
 
* `docker run --rm -v /var/run/docker.sock:/var/run/docker.sock nate/dockviz images -t`

## Debugging a container

Attach an image to another docker container, so that you can use debug tools in the new image.

Sample dockerfile with strace:
```
FROM alpine
RUN apk update && apk add strace
CMD ["strace", "-p", "1"]
```

Build as strace then

```
docker run -t --pid=container:TARGET \
  --net=container:TARGET \
  --cap-add sys_admin \
  --cap-add sys_ptrace \
  strace
```

Target filesystem isn't under / though, access it via /proc/1/root/

