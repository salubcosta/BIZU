Atualização de pacotes

$ sudo apt-get update 

Instalar servidor MariaDB

$ sudo apt-get install mariadb-server

Depois pode fazer o login para corrigir a questão de user e senha:

$ sudo mysql -u root 

Mudar o banco de dados:

> use mysql

> UPDATE user SET plugin='' WHERE User='root';

> FLUSH PRIVILEGES;

Depois basta executar o comando quit para sair do servidor. Para configurar a senha com segurança basta digitar como usuário root: <code>sudo mysql_secure_installation </code>

Pronto. 

Para testar execute no terminal:<code> mysql -u root -p</code>

Agora podemos criar um usuário para administra a base

> create user 'salumao'@'%' identified by '123456';

Depois basta dar privilégios para o usuário

> grant all privileges on *.* to 'salumao'@'%' with grant option;

e salvar as configurações: <code>flush privileges;</code>

Agora para liberar o acesso de fora basta editar o arquivo 50.server.cnf:

$ sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

Alteraro valor de 127.0.0.1 Em bind-address para = *

Agora pode restartar o servidor:

$ sudo systemctl restart mysql

Agora sim, para finalizar a basta instalar com o workbench:

$ sudo apt install mysql-workbench

Pronto. Fim!
