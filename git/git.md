# Git
![Git Logo]()

### Links úteis:
  * [Git - Book](https://git-scm.com/book/en/v2)
  * [Git - ArchWiki](https://wiki.archlinux.org/title/Git)

### Comandos
  * Git Login:
    ````
    $ git config --global user.name  "Nome"
    $ git config --global user.email "nome@example.com"
    ````
  * Deslogar:
    ````
    $ git config --global --unset user.name
    $ git config --global --unset user.email
    $ git config --global --unset credential.helper
    ````
    ou
    ````
    $ git config --global --unset-all
    ````
  * Inicializar repositório:
    ````
    $ mkdir nome_do_repositorio
    $ cd nome_do_repositorio
    $ git init
    ````
  * Clonar um repositório existente:
    ````
    $ git clone url_do_repositório
    ````
  * Clonar com token:
    ````
    $ git clone https://token:x-oauth-basic@github.com/usuario/repositorio.git
    ````
  * Atualizar token:
    ````
    $ git remote remove origin
    $ git remote add origin https://token:x-oauth-basic@github.com/usuario/repositorio.git
    $ git remote -v
    ````
  * Mostrar mudanças a serem comitadas:
    ````
    $ git status
    ````
  * Mostrar mudanças de forma simplificada:
    ````
    $ git status -s
    ````
  * Adicionar arquivos a serem comitados:
    ````
    $ git add nome_do_arquivo
    $ git add nome.*
    ````
  * Ver mudanças:
    ````
    $ git diff
    $ git diff nome_do_arquivo
    ````
  * Commitar:
    ````
    $ git commit -m 'Informações do commit'
    ````
  * Voltar um commit:
    ````
    $ git reset --hard
    ````
  * Ignorar arquivos:
    * `.gitignore` utiliza expressões regulares
    * Linhas em branco ou começando com # são ignoradas
    * Pode negar um padrão iniciando com !
    * Exemplo de `.gitignore`:
      ````
      *.[oa]
      *~
      !lib.a
      ````
