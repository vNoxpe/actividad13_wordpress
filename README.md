# Instalación MANUAL del CMS WORDPRESS:
Paso 1: Instalación otros paquetes php necesarios
apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
Paso 2: Creación y configuración de la base de datos:
6
$mysql –u root –p
MySQL >create database wordpress;
MySQL >use wordpress;
MySQL >create user ‘wordpress’@’localhost’ identified by ‘usuario@1’;
MySQL >grant all privileges on wordpress.* to ‘wordpress’@’localhost’ with grant option;
MySQL >flush privileges;
MySQL>quit;
