# Docker
![Docker Logo](https://raw.githubusercontent.com/Augusto-Fadanelli/HOW-TO/main/docker/docker-logo.png)

### Links úteis:
  * [Docker Documentation](https://docs.docker.com/)
  * [Docker Hub](https://hub.docker.com/)
  * [Docker MySQL](https://hub.docker.com/_/mysql)
  * [Apostila](http://files.cod3r.com.br/apostila-docker.pdf)

### Instalação
  * Arch Linux
    ````
    $ sudo pacman -S docker docker-compose
    $ sudo systemctl start docker.service
    $ sudo docker run hello-world
    ````
    
  * *Obs:. Para usar o docker com usuário não root, adicione seu usuário ao grupo docker, faça login novamente e reinicie o serviço docker.*
    
### Comandos
  * Iniciar serviço docker:
    ````
    $ sudo systemctl start docker.service
    ````
  * Exibir versão do docker:
    ````
    $ docker version
    ````
  * Exibir containers abertos:
    ````
    $ docker ps
    ````
  * Exibir todos os containers que já foram instanciados:
    ````
    $ docker ps -a
    ````
  * Exibir imagens:
    ````
    $ docker images
    ````
  * Iniciar instância do ubuntu (e parâmetros):
    ````
    $ docker run ubuntu
    $ docker run ubuntu echo "Olá Mundo"
    $ docker run ubuntu cat /etc/*release*
    ````
  * Iniciar instância ubuntu com nome ubuntu-teste, salvar `/home` do container ubuntu em `ubuntu-teste/` e usar tty:
    ````
    $ docker container run --name ubuntu-teste -v $(pwd)/ubuntu-teste:/home -it ubuntu
    ````
  * Usar tty no container ubuntu já criado:
    ````
    $ docker container start ubuntu-teste
    $ docker container attach ubuntu-teste
    ````
  * Executar bash em container iniciado:
    ````
    $ docker container exec -ti nome_do_container /bin/bash
    ````
  * Parâmetro sleep:
    ````
    $ docker run -d ubuntu sleep 20
    ````
  * Executar comandos em instância rodando em background:
    ````
    $ docker exec nome_do_container comando
    ````
  * Iniciar container já criado:
    ````
    $ docker container start nome_do_container
    ````
  * Remover um container:
    ````
    $ docker rm nome_do_container
    ````
  * Remover todos os containers inativos:
    ````
    $ docker container prune
    ````
  * Remover imagem:
    ````
    $ docker image rmi id_da_imagem
    ````
  * Criar container e salvar dados com volumes:
    ````
    $ docker run -it -v "/home/seu_usuario/.docker/ubuntu/:/var/www/" ubuntu
    ````
  * Inspencionar container:
    ````
    $ docker inspect nome_do_container
    ````
  * Iniciar instância docker do MySQL (container temporário):
    ````
    $ docker run --name nome_do_container -e MYSQL_ROOT_PASSWORD=minha_senha -d mysql:versão_tag
    ````
  * Exemplo de `Dockerfile`
    ````
    FROM alpine:3.9
    MAINTAINER Insight Data Science Lab
    RUN apk add --no-cache mongodb
    VOLUME /data/db
    EXPOSE 27017
    CMD [ "mongod", "--bind_ip", "0.0.0.0" ]
    ````
  * Criar imagem docker file
    ````
    $ docker build -f Dockerfile -t nome_de_usuario_docker_hub/mongo:1.0
    $ docker build -t nome_de_usuario_docker_hub/mongo:1.0 .
    ````
  * Fazer login no docker hub
    ````
    $ docker login
    ````
  * Upar imagem para o docker hub
    ````
    $ docker push nome_de_usuario_docker_hub/nome_da_imagem:tag
    ````
  * Baixar imagem do docker hub
    ````
    $ docker pull nome_de_usuario_docker_hub/nome_da_imagem:tag
    ````
  * Iniciar container em arquivo docker-compose.yml:
    ````
    $ docker compose up -d
    ````
  * Fechar container:
    ````
    $ docker stop nome_do_container
    ````
  * Exemplo de arquivo compose.yml para MySQL:
    ````
    version: '3.1'
     services:
       db:
        container_name: mysql_curso
        hostname: mysql_curso
        image: mysql
        restart: always
        command:
          - --default-authentication-plugin=mysql_native_password
          - --character-set-server=utf8mb4
          - --collation-server=utf8mb4_unicode_ci
          - --innodb_force_recovery=0
          - --default_time_zone=America/Sao_Paulo
        volumes:
          - ~/.MySQLDBData/mysqlonly/mysql_curso:/var/lib/mysql
        ports:
          - 3306:3306
        environment:
          MYSQL_ROOT_PASSWORD: 1234
          MYSQL_DATABASE: base_de_dados
          MYSQL_USER: user
          MYSQL_PASSWORD: 1234
    ````
  * Criar container de servidor Nginx para página html
    ````
    $ docker container run -d --name pagina_web -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx
    ````
    * Crie o arquivo `index.html` dentro da pasta html
    * Acesse a página em `http://localhost:8080/`
