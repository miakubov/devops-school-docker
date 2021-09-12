 #Docker Task
 
1 Написать 2 Dockerfile с web сервисом прим. (nginx, apache), передать конфигурацию в контейнер прим. nginx.confб образы должны работать на разных портах.

2 Собрать образы, используя double tagging ,положить собранные образы в локальное registry

3 Написать docker-compose.yaml ,в котором должен быть создан сервис из 2 ранее созданных образов (использовать локальное registry ), с помощью которых можно публиковать статику, образы должны запускаться в разных сетях, но должны использовать 1 хостовой вольюм со статикой на двоих, а также образы должны быть ограничены по ресурсам (memory, cpu)

Итог:  через веб-браузер должна быть доступна статика на 2 опубликованных портах сервиса


* Install Docker Engine on CentOS https://docs.docker.com/engine/install/centos/

* Install Docker-compose https://docs.docker.com/compose/install/

* Pull docker images from dockerhub

**docker pull registry**

**docker pull httpd**

**docker pull nginx**

* Check docker images

**docker image ls**

* Run a local registry https://docs.docker.com/registry/deploying/#run-a-local-registry

**docker run -d -p 5000:5000 --restart=always --name registry registry:2**

  -d, --detach                     Run container in background and print container ID
  
  -p, --publish list               Publish a container s port(s) to the host
  
  --restart string                 Restart policy to apply when a container exits (default "no")
  
  --name string                    Assign a name to the container

* Build docker and tag https://docs.docker.com/engine/reference/commandline/build/

**docker build nginx/ -t localhost:5000/nginx_my:1.21**

**docker build httpd/ -t localhost:5000/httpd_my:2.4**

 --file , -f		Name of the Dockerfile (Default is 'PATH/Dockerfile')
 
 --tag , -t		Name and optionally a tag in the 'name:tag' format

* Push the image to the local registry running at localhost:5000

**docker push localhost:5000/nginx_my:1.21**

**docker push localhost:5000/httpd_my:2.4**


* docker-compose up https://docs.docker.com/compose/reference/up/

**docker-compose up -d**

 -d, --detach               Detached mode: Run containers in the background, print new container names. Incompatible with --abort-on-container-exit.
