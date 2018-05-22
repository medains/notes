# Docker

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

