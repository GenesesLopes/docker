# docker with docker-compose
creation of work development in docker

* Serviços Disponíveis
  * Apache
  * Nginx
  * Postgresql
  * MySql
  * PhpMyadmin
  * PhhPgadmin
  * PHP - Com composer
  * Angular

<strong>Para usuários do docker toolbox, o projeto deve ser clonado dentro da pasta pessoal do usuário</strong><br>

<strong>Todos os projetos web devem ficar na pasta sites</strong>

* Configurando Dominio Local

  * Windows<br>
    1 - Ir até a pasta <code>C:\Windows\System32\drivers\etc</code>.<br>
    2 - Dar permissão todal ao arquivo hosts para o usuário logado.<br>
    3 - Adicionar a seguinte linha no final do arquivo: <code>127.0.0.1	projeto.local</code>(O dominio fica a seu critério)<br>
    Para usuários do docker toolbox, o IP será o resultado do comando <code>$ docker-machine ip default</code><br>
    4 - Criar um atalho na área de trabalho para projetos futuros (Opcional).<br>
  * Linux/Mac<br>
    1 - Editar o arquivo <code>/etc/hosts</code><br>
    2 - Adicionar a seguinte linha no final do arquivo: <code>127.0.0.1	projeto.local</code>(O dominio fica a seu critério)<br>
  
 *  Baixar VSCode: https://code.visualstudio.com/<br>
 *  Instalar plugin do docker: https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker&ssr=true<br>

* Configuração de VirtualHost nos containers Apache e Nginx

  * Apache<br>
  
    1 - Ir até a pasta <code> apache/sites-avaliable</code> e Editar as diretivas do arquivo sites.conf:<br>
        <code>ServerName projeto.local</code> (Colocar o dominio local criado).<br>
        <code>DocumentRoot /var/www/html/teste</code> e <code>Directory "/var/www/html/teste"</code>, Alterar O final "teste" pelo nome da pasta do seu projeto.<br>
    2 - Acessar o container do apache pelo vscode e digitar o seguinte comando: <code># a2ensite sites.conf</code>.<br>
    3 - Reiniciar o container pelo vscode.<br>
    4 - Caso queira criar mais VirtualHost, crie uma copia do arquivo <code>sites.conf</code> na mesma pasta, renomeie-o de acordo a sua escolha (ex.: projeto.conf) e repita o processo adaptando-se ao novo arquivo criado.<br>
  
  * Nginx <br>
  
    1 - Ir até a pasta <code> nginx</code> e Editar as diretivas do arquivo sites.conf:<br>
      <code>root /var/www/html/teste;</code> Alterar O final "teste" pelo nome da pasta do seu projeto.<br>
      <code>server_name site.dev;</code> (Colocar o dominio local criado).<br>
    2 - Reiniciar o container pelo vscode.<br>
    3 - Caso queira criar mais VirtualHost, crie uma copia do arquivo <code>sites.conf</code> na mesma pasta, renomeie-o de acordo a sua escolha (ex.: projeto.conf) e repita o processo adaptando-se ao novo arquivo criado.<br>

* Criando containers

  * Criando volumes para postgres e mysql<br>
    <code>$ docker create volume data-postgres</code><br>
    <code>$ docker create volume data-mysql</code><br>
  * Editar o arquivo .env de acordo as suas necessidades.<br>
  * Instanciar container com o serguinte comando:
    <code>$ docker-compose up -d serviço1 serviço2 ...</code><br><br>
 A partir de agora a gerência dos containers será através do VScode (iniciar e parar).
  
  
