Buenas pessoal, tudo tranquilo?

Hoje trago pra vocês a instalação, provisionamento e ajustes finos do samba4 DC. Vou utilizar um repositório não oficial, mas que é bastante utilizado e difundido na lista oficial do samba.

[https://lists.samba.org/](https://lists.samba.org/)

Hands on!!!

## 1\. Instalação e Atualização da Distro base

Distro (debian 10)

Atualizando:

<pre>apt update && apt full-upgrade</pre>

### 1.1 Modificar o arquivo /etc/hosts

<pre>127.0.0.1             localhost
172.16.1.7            DC1.samdom.dominio.intra    DC1</pre>

### 1.2 Modificar o arquivo /etc/hostname

Configure um nome de hostname:

<pre>DC1</pre>

Fonte: [https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller#Preparing_the_Installation](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller#Preparing_the_Installation)

Reinicie o servidor.

## 2\. Instalação do pacote samba4

<pre>apt install apt-transport-https
wget -O - http://apt.van-belle.nl/louis-van-belle.gpg-key.asc | apt-key add -
echo "# AptVanBelle repo" > /etc/apt/sources.list.d/van-belle.list
echo "deb http://apt.van-belle.nl/debian buster-samba413 main contrib non-free" | tee -a /etc/apt/sources.list.d/van-belle.list
apt-get update
apt-get install -t o=AptVanBelle samba winbin</pre>

Fonte: http://apt.van-belle.nl/

## 3\. Provisionando

### 3.1 Parâmetros que podem ser usados

Para conhecer todos os parâmetros pode-se utilizar o comando:

<pre>samba-tool domain provision --help</pre>

### 3.2 Comando para o provisionamento

Para provisionar execute o comando abaixo.

<pre>samba-tool domain provision --use-rfc2307 --interactive</pre>

[https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller)
