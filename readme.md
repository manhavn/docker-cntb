# Docker cntb cli

```dockerfile
FROM alpine:latest
RUN apk add wget
RUN wget https://github.com/contabo/cntb/releases/download/v1.4.6/cntb_v1.4.6_linux_amd64.tar.gz
RUN tar -xf cntb_v1.4.6_linux_amd64.tar.gz
RUN install cntb /usr/local/bin/cntb
RUN rm cntb_v1.4.6_linux_amd64.tar.gz cntb
RUN apk del wget
```

```shell
docker build -t manhavn/cntb:v0.0.1 .
docker push manhavn/cntb:v0.0.1
docker run -d -it --name cntb_user_1 -v $(pwd)/cntb_user_1:/root manhavn/cntb:v0.0.1

docker exec cntb_user_1 cntb config set-credentials --oauth2-clientid=____ --oauth2-client-secret=____ --oauth2-user=____ --oauth2-password=____
docker exec cntb_user_1 cntb get instances
```
