# Docker
![Docker Logo](https://raw.githubusercontent.com/Augusto-Fadanelli/HOW-TO/main/docker/docker-logo.png)

### Links úteis:
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
### Comandos
  * Iniciar serviço docker:
    ````
    $ sudo systemctl start docker.service
    ````
  * Exibir versão do docker:
    ````
    $ sudo docker version
    ````
  * Exibir containers abertos:
    ````
    $ sudo docker ps
    ````
  * Exibir todos os containers que já foram instanciados:
    ````
    $ sudo docker ps -a
    ````
  * Exibir imagens:
    ````
    $ sudo docker images
    ````
  * Iniciar instância do ubuntu (e parâmetros):
    ````
    $ sudo docker run ubuntu
    $ sudo docker run ubuntu echo "Olá Mundo"
    $ sudo docker run ubuntu cat /etc/*release*
    ````
  * Parâmetro sleep:
    ````
    $ sudo docker run -d ubuntu sleep 20
    ````
  * Executar comandos em instância rodando em background:
    ````
    $ sudo docker exec nome_do_container comando
    ````
  * Iniciar container já criado:
    ````
    $ sudo docker container start nome_do_container
    ````
  * Remover um container:
    ````
    $ sudo docker rm nome_do_container
    ````
  * Remover todos os containers inativos:
    ````
    $ sudo docker container prune
    ````
  * Criar container e salvar dados com volumes:
    ````
    $ sudo docker run -it -v "/home/seu_usuario/.docker/ubuntu/:/var/www/" ubuntu
    ````
  * Inspencionar container:
    ````
    $ sudo docker inspect nome_do_container
    ````
  * Iniciar instância docker do MySQL (container temporário):
    ````
    $ sudo docker run --name nome_do_container -e MYSQL_ROOT_PASSWORD=minha_senha -d mysql:versão_tag
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
    $ sudo docker build -f Dockerfile -t nome_de_usuario_docker_hub/mongo:1.0
    $ sudo docker build -t nome_de_usuario_docker_hub/mongo:1.0 .
    ````
  * Fazer login no docker hub
    ````
    $ sudo docker login
    ````
  * Upar imagem para o docker hub
    ````
    $ sudo docker push nome_de_usuario_docker_hub/nome_da_imagem:tag
    ````
  * Baixar imagem do docker hub
    ````
    $ sudo docker pull nome_de_usuario_docker_hub/nome_da_imagem:tag
    ````
  * Iniciar container em arquivo docker-compose.yml:
    ````
    $ sudo docker compose up -d
    ````
  * Fechar container:
    ````
    $ sudo docker stop nome_do_container
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
    $ sudo docker container run -d --name pagina_web -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx
    ````
    * Crie o arquivo `index.html` dentro da pasta html
    * Acesse a página em `http://localhost:8080/`
