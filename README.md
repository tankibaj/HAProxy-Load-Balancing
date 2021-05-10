HAProxy is a free, very fast and reliable solution offering high availability, load balancing, and proxying for TCP and HTTP-based applications. It is particularly suited for very high traffic web sites and powers quite a number of the world's most visited ones.



#### Goal

- Create a HAProxy docker container.
- Multiple webapp docker containers.
- Configure HAProxy as a load balancer with HTTPS support.



#### Prerequisites

- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Manage Docker as a non-root user for Linux](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)



#### Command and Usage

`./lb <command>`

| Command                  | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| `-S, --start, start`     | Run HAProxy and application containers.                      |
| `-D, --destroy, destroy` | Destroy everything related to HAProxy.                       |
| `-s, -status, status`    | HAProxy containers status.                                   |
| `-h, --help, help`       | Display help list.                                           |


#### Test

```bash
❯ curl "http://192.168.0.12"

PAGE: serving HOME
HOST NAME: a32381218105
HOST IP: 172.16.50.11
REMOTE IP: loadBalancer_haproxy.haproxy_public_net
SERVER PORT: 80
REMOTE_PORT: 36658
PROTOCOL: HTTP/1.1
USER AGENT: curl/7.64.1
REQUEST TIME: 1620690060
REQUEST URI: /
HTTP_ACCEPT: */*
```

```bash
❯ curl "http://192.168.0.12/dog"

PAGE: serving DOG
HOST NAME: b121061c2732
HOST IP: 172.16.50.13
REMOTE IP: loadBalancer_haproxy.haproxy_public_net
SERVER PORT: 80
REMOTE_PORT: 54638
PROTOCOL: HTTP/1.1
USER AGENT: curl/7.64.1
REQUEST TIME: 1620690134
REQUEST URI: /dog
HTTP_ACCEPT: */*
```

```bash
❯ curl "http://192.168.0.12/cat"

PAGE: serving CAT
HOST NAME: fe41f0309c77
HOST IP: 172.16.50.15
REMOTE IP: loadBalancer_haproxy.haproxy_public_net
SERVER PORT: 80
REMOTE_PORT: 60008
PROTOCOL: HTTP/1.1
USER AGENT: curl/7.64.1
REQUEST TIME: 1620690163
REQUEST URI: /cat
HTTP_ACCEPT: */*
```

```bash
❯ curl "http://192.168.0.12/bird"

PAGE: serving BIRD
HOST NAME: 084420e573d9
HOST IP: 172.16.50.17
REMOTE IP: loadBalancer_haproxy.haproxy_public_net
SERVER PORT: 80
REMOTE_PORT: 46074
PROTOCOL: HTTP/1.1
USER AGENT: curl/7.64.1
REQUEST TIME: 1620690188
REQUEST URI: /bird
HTTP_ACCEPT: */*
```

