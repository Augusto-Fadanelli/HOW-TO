# Zabbix
![]()

### Links úteis
  * [Wiki](https://www.zabbix.com/documentation/current/pt)
  * [Repositório Oficial](https://repo.zabbix.com/)
  * [Download via pacotes](https://www.zabbix.com/download)

### Instalação e Configuração de Servidor Zabbix com Ubuntu Server
  * [Configuração inicial](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04-pt)

  * Locale pt_BR
    ````
    $ less /usr/share/i18n/SUPPORTED
    $ sudo locale-gen pt_BR.UTF-8
    $ sudo update-locale
    ````

  * Requisitos de Software
    * [MySQL](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04-pt):
      ````
      $ sudo apt-get install mysql-server
      ````
      * Acessando o MySQL
        ````
        $ mysql -u root -p
        ````
    * [Apache e PHP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04-pt):
      ````
      $ sudo apt-get install apache2
      $ sudo apt-get install php libapache2-mod-php php-mysql
      ````
      * Ativando UFW:
        ````
        $ sudo ufw enable
        $ sudo ufw default deny
        $ sudo iptables -L
        ````
    * PHP GD:
      ````
      $ sudo apt-get install php-gd
      ````
    * libXML:
      ````
      $ sudo apt-get install libxml2
      `````
    * Extensões PHP:
      ````
      $ sudo apt-get install php-bcmath php-mbstring php-db
      ````
    
  * [Instalação Zabbix](https://www.zabbix.com/download?zabbix=6.0&os_distribution=ubuntu&os_version=20.04_focal&db=mysql&ws=apache)
  
  * Adicionar `/etc/apache2/conf-available/zabbix.conf` em `<IfModule mod_php7.c>` e reiniciar apache2
    ````
    php_value date.timezone America/Belem
    ````
  
  * Pacotes Opcionais
    ````
    OpenIPMI - Monitoramento de dispositivos IPMI
    libssh2 - Verificação direta via ssh
    fping - Monitoramento simples
    libcurl - Monitoramento web
    libik-semel - Envio de alerta via mensageiro
    net-snmp - Monitoramento via SNMP
    ````
  * Source list Zabbix
    ````
    $ cat /etc/apt/sources.list.d/zabbix.list
    ````
  * Ver pacotes Zabbix
    ````
    $ apt-cache search zabbix
    ````
  * Pacotes adicionais
    ````
    zabbix-get
    zabbix-sender
    ````
  * Arquivos de log `/var/log/zabbix/`
    ````
    $ cd /var/log/zabbix/
    $ tail -f zabbix_server.log
    ````
  * Arquivos de configuração `/etc/zabbix/`
    ````
    zabbix_agentd.conf zabbix_server.conf
    ````
  * Arquivos de script externo `/usr/lib/zabbix/`
  
  * Comandos:
    * Mostrar versão do Zabbix Server
      ````
      $ zabbix_server -V
      ````
    * Atualizar o cache de configuração
      ````
      $ sudo zabbix_sever -R config_cache_reload
      ````
    * 

### Servidor Zabbix Proxy com Ubuntu Server
#### Servidor Zabbix Proxy com Ubuntu Server em Raspberry PI 4

### Zabbix Agents
#### Windows

#### Arch Linux
  * Instalação:
    ````
    $ sudo pacman -S zabbix-agent
    ````
  * [Configuração](https://wiki.archlinux.org/title/Zabbix#Agent_setup)
    * Editar o arquivo `/etc/zabbix/zabbix_agentd.conf`
      ````
      Server=<IP of Zabbix server>
      ServerActive=<IP of Zabbix server>
      Hostname=<Nome do Hostname>
      Timeout=30
      ````
    * Iniciar serviço
      ````
      $ sudo systemctl start zabbix-agent
      $ sudo systemctl enable zabbix-agent
      ````
