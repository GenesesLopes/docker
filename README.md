# docker with docker-compose

<p align="center">
<img width="250" height="200" src="https://i.pinimg.com/originals/f5/5e/80/f55e8059ea945abfd6804b887dd4a0af.gif">
</p>
creation of work development in docker

- Serviços Disponíveis
  - Apache - Com Php
  - Nginx
  - Postgresql
  - MySql
  - PhpMyadmin
  - PhpPgadmin
  - PHP - Com composer
  - Angular
  - React
  - Mongodb
  - Mongo Express
  - Redis

#### :warning: Para usuários do docker toolbox, o projeto deve ser clonado dentro da pasta pessoal do usuário

#### :warning: Todos os projetos web devem ficar na pasta `sites`.

#### :warning: Caso utilizar o autocomplete do terminal (ZSH), alterar configuração de extensão do docker em 
```bash
arquivo/preferencias/configurações/extensões/Docker
```
Altere o campo "Docker › Attach Shell Command: Linux Container" de 
```bash
/bin/sh -c "[ -e /bin/bash ] && /bin/bash || /bin/sh
```
para 
```bash
/bin/sh -c "[ -e /bin/bash ] && /bin/bash || /bin/zsh 2> /dev/null || /bin/sh 
```

#### :warning: Caso esteja tendo o aviso/erro no Vscode: `PHP › Validate: Executable Path` basta seguir esse passo a passo:
- [Corrigir Php Validate VSCODE](https://gist.github.com/tuliocll/16952e8635eee21e6f3d59083ae6d3b8)

# Iniciando :tada:

### instalando docker, git e vscode.

#### Windows:

- [Docker Hub](https://docs.docker.com/docker-for-windows/install/)
- [Git](https://git-scm.com/download/win)
- [Visual Studio Code](https://code.visualstudio.com/download)
- [Extensão do Docker pro Vscode](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker&ssr=true)

#### Linux:

- [Docker](https://tuliocalil.blogspot.com/2019/09/instalar-docker-e-docker-compose-no.html)
- [Git](https://git-scm.com/download/linux)
- [Visual Studio Code](https://code.visualstudio.com/download)
- [Extensão do Docker pro Vscode](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker&ssr=true)

# Clonar repositorio :arrows_clockwise:

Escolha um local para clonar o repositorio e faça o clone;

#### Windows:

- Abra o programa Git Bash (instalado junto com o git)
- Use o comando `cd` para navegar pelas pastas (Ex: `cd Documentos/`)
- Clone o repositorio com o comando: `git clone https://github.com/GenesesLopes/docker.git`
- Navegue até a pasta que acabou de clonar: `cd docker`

#### Linux:

- Abra o terminal
- Navegue até a pasta onde deseja clonar o repo (exemplo):

```bash
  cd Documentos
```

- Clone o repositorio:

```bash
  git clone https://github.com/GenesesLopes/docker.git
```

- Navegue até a pasta que acabou de clonar:

```bash
  cd docker
```

# Subindo Containers :arrow_up:

- Para subir o container desejado, basta executar o comando (Windows, ou Linux):

```sh
docker-compose up -d nomeDoContainer
```

- O exemplo aseguir irá subir o container do apache (o container do apache já tem o php incluso, não precisa subi-lo):

```sh
docker-compose up -d apache
```

- Containers disponiveis; `apache`, `postgres`, `mysql`, `nginx`, `react`, `phpmyadmin`, `phppgadmin`, `redis`, `angular`, `mongo`, `php(puro)`, `mongoexpress`.

# Configurações: :pencil:

- Configurando Dominio Local

  - Windows<br>
    1 - Ir até a pasta <code>C:\Windows\System32\drivers\etc</code>.<br>
    2 - Dar permissão todal ao arquivo hosts para o usuário logado.<br>
    3 - Adicionar a seguinte linha no final do arquivo: <code>127.0.0.1 projeto.local</code>(O dominio fica a seu critério)<br>
    Para usuários do docker toolbox, o IP será o resultado do comando <code>\$ docker-machine ip default</code><br>
    4 - Criar um atalho na área de trabalho para projetos futuros (Opcional).<br>
  - Linux/Mac<br>
    1 - Editar o arquivo <code>/etc/hosts</code><br>
    2 - Adicionar a seguinte linha no final do arquivo: <code>127.0.0.1 projeto.local</code>(O dominio fica a seu critério)<br>

* Criando containers

  - Criando volumes para postgres e mysql (Obs.: Comandos apenas se tiver erro de criação de volumes para bases de dados)<br>
    <code>$ docker create volume data-postgres</code><br>
    <code>$ docker create volume data-mysql</code><br>
  - Editar o arquivo <code>.env</code> de acordo as suas necessidades.<br>
  - Instanciar container com o serguinte comando:
    <code>\$ docker-compose up -d serviço1 serviço2 ...</code><br><br>

* Configuração de VirtualHost nos containers Apache e Nginx

  - Apache<br>

    1 - Ir até a pasta <code> apache/sites-avaliable</code> e Editar as diretivas do arquivo sites.conf:<br>
    <code>ServerName projeto.local</code> (Colocar o dominio local criado).<br>
    <code>DocumentRoot /var/www/html/teste</code> e <code>Directory "/var/www/html/teste"</code>, Alterar O final "teste" pelo nome da pasta do seu projeto.<br>
    2 - Acessar o container do apache pelo vscode e digitar o seguinte comando: <code># a2ensite sites.conf</code>.<br>
    3 - Reiniciar o container pelo vscode.<br>
    4 - Caso queira criar mais VirtualHost, crie uma copia do arquivo <code>sites.conf</code> na mesma pasta, renomeie-o de acordo a sua escolha (ex.: projeto.conf) e repita o processo adaptando-se ao novo arquivo criado.<br>

  - Nginx <br>

    1 - Ir até a pasta <code> nginx</code> e Editar as diretivas do arquivo sites.conf:<br>
    <code>root /var/www/html/teste;</code> Alterar O final "teste" pelo nome da pasta do seu projeto.<br>
    <code>server_name site.dev;</code> (Colocar o dominio local criado).<br>
    2 - Reiniciar o container pelo vscode.<br>
    3 - Caso queira criar mais VirtualHost, crie uma copia do arquivo <code>sites.conf</code> na mesma pasta, renomeie-o de acordo a sua escolha (ex.: projeto.conf) e repita o processo adaptando-se ao novo arquivo criado.<br>

:warning: A partir de agora a gerência dos containers será através do VScode (`iniciar` e `parar`).
