Instalação do Ansible e Docker
=========================
## 1. Configurações inicias para dar privilegios especificos no linux
##### Obs: user é o nome de usuráio do local host, ubuntu é a estação de trabalho.
#### Acesse o arquivo sudoers:  

>$ sudo visudo

#### Localize *User privilege specification* embaixo e escreva o comando abaixo:

user  ALL=(ALL:ALL) NOPASSWD: ALL

## 2. Instalando o SSH:

>$ sudo apt-get install openssh-server

#### Abra o arquivo do SSH:

>$ sudo gedit etc/ssh/sshd_config

#### Altere o seguinte comando *#PermitRootLogin prohibit-password* para:

>PermitRootLogin yes

#### Reinicie o SSH server:

>$ service ssh restart

#### Crie um chave SSH:

>$ ssh-keygen

#### Faça copia da chave SSH:

>$ cp -p ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys

## 3. Instalando o Ansible...

#### Crie um repositorio Ansible:

>$ sudo apt-add-repository ppa:ansible/ansible

#### Confirme < ENTER >.

#### Faça uma atualização:

>$ sudo apt-get update

#### Instale o Ansible:

>$ sudo apt-get install ansible

#### Verifique a versão do Ansible:

>$ ansible --version

>$ sudo apt-get update

#### Instalando Docker

>$ sudo apt-get install \ apt-transport-https \ ca-certificates \ curl \ software-properties-common

> tecle Y para continuar

>$ curl -fsSl https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -ok

chave de identificação como assinatura digital

>$ sudo apt-key fingerprint 0EFCD88

criando um repositorio dos pacotes Docker

>$ sudo add-apt-repository \ "deb [arch=amd64] https//download.docker.com/linux/unbuntu \ $(lsb_release -cs) \ stable"

>$ sudo apt-get update

Instalação do Docker

>$ sudo apt-get install docker-ce

### Ferramentas Ansible e Docker instalados com sucesso!
## Usando containers Dockers
### Instalando mysql
#### MySQL

>$ sudo docker run --name banco -e MYSQL_ROOT_PASSWORD=senha123 -d mysql:5.6
##### name: nome do banco de dados de sua escolha
##### MYSQL_ROOT_PASSWORD: senha do dados de sua escolha
##### mysql versao 5.6

### Instalando wordpress
#### setando o banco de dados que o wordpress irá utilizar

>$ sudo docekr run --name site --link banco:mysql -p 80:80 -d wodpress
name: nome de sua escolha 
link: qual banco de dados e sua porta 80:80

##### Pronto! instalação concluida.

## Rodando uma plyabook ansible com containers Docker
### crie um diretorio para os arquivos
>$ mkdir wordpress
>$ cd wordpress
>wordpress$ touch hosts
>wordpress$ touch playbook.yml

#### agora no arquivo hosts e playbook copie e cole os codigos que estão disponibilizados nesse repositório github!

















