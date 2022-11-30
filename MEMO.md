# memo

## container

- run container
  - `docker container run --publish 8080:80 nginx:1.21`
- list container
  - `docker container ls`
- stop container
  - `docker container stop ubuntu`
- remove container
  - `docker container rm ubuntu`
- remove container force
  - `docker container rm -f ubuntu`
- interactive mode
  - `docker container run -it ubuntu:20.04`
- auto delete if container is stopped
  - `docker container run --rm -it ubuntu:20.04`
- set name of container
  - `docker container run --name ubuntu ubuntu:20.04`
- run background
  - `docker container run -d -it --name ubuntu ubuntu:20.04`
- run command
  - `docker container exec ubuntu echo 'hello world' > /root/hello.txt`
- run command with bash
  - `docker container exec -it ubuntu bash`

## image

- list image
  - `docker image ls`
- with tag
  - `docker container run --name ubuntu --rm ubuntu:22.04 cat /etc/lsb-release`
- latest
  - `docker container run --name ubuntu --rm ubuntu:latest cat /etc/lsb-release`
- no tag
  - `docker container run --name ubuntu --rm ubuntu cat /etc/lsb-release`
- build
  - `docker image build --tag my-ubuntu:date .`
- run built image
  - `docker container run --name my-ubuntu --rm -it my-ubuntu:date vi`