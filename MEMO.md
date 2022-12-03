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

## volume

- mount volume
  - `docker volume create --name docker-practice-db-volume`
- check volume
  - `docker volume ls`
- run with --volume
  - `docker container run --name db --rm -d --platform linux/amd64 --env MYSQL_ROOT_PASSWORD=rootpassword --env MYSQL_USER=hoge --env MYSQL_PASSWORD=password --env MYSQL_DATABASE=event --volume docker-practice-db-volume:/var/lib/mysql docker-practice:db`
- run with --mount
  - `docker container run --name db --rm -d --platform linux/amd64 --env MYSQL_ROOT_PASSWORD=rootpassword --env MYSQL_USER=hoge --env MYSQL_PASSWORD=password --env MYSQL_DATABASE=event --mount type=volume,src=docker-practice-db-volume,dst=/var/lib/mysql docker-practice:db`
- inspect volume
  - `docker volume inspect docker-practice-db-volume`
- rm volume
  - `docker volume rm docker-practice-db-volume`

## bind

- bind with --volume
  - `docker container run --name app --rm -d -it --volume $(pwd)/src:/src docker-practice:app php -S 0.0.0.0:8000 -t /src`
- bind with --mount
  - `docker container run --name app --rm -d -it --mount type=bind,src=$(pwd)/src,dst=/src docker-practice:app php -S 0.0.0.0:8000 -t /src`
- bind with init
  - `docker container run --name db --rm -d --platform linux/amd64 --env MYSQL_ROOT_PASSWORD=rootpassword --env MYSQL_USER=hoge --env MYSQL_PASSWORD=password --env MYSQL_DATABASE=event --mount type=volume,src=docker-practice-db-volume,dst=/var/lib/mysql --mount type=bind,src=$(pwd)/docker/db/init.sql,dst=/docker-entrypoint-initdb.d/init.sql docker-practice:db`
