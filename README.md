# Instalación MANUAL del CMS WORDPRESS:
Paso 1: Instalación otros paquetes php necesarios
apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/34ddc99a-4aa9-43fe-bf3e-c13c2624dec3)

Paso 2: Creación y configuración de la base de datos:
$mysql –u root –p
MySQL >create database wordpress;
MySQL >use wordpress;
MySQL >create user ‘wordpress’@’localhost’ identified by ‘usuario@1’;
MySQL >grant all privileges on wordpress.* to ‘wordpress’@’localhost’ with grant option;
MySQL >flush privileges;
MySQL>quit;
![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/8986ce31-4401-43d8-9685-de1d65ccc871)
Paso 3: Configuración APACHE 2
- Vamos a utilizar el sitio por defecto: 000-default.conf
-Editamos 000-default.comf y añadimos las siguientes directivas:
<VirtualHost *:80>
 ServerAdmin webmaster@localhost
 DocumentRoot /var/www/html
 DirectoryIndex index.html index.php
 <Directory /var/www/html/>
 AllowOverride All
 </Directory>
</VirtualHost>

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/696ad9a2-2923-4709-807d-aae611708c5e)

-Ahora, se activa el mod_rewrite para utilizar la función de permalink o enlace permanente de WordPress:
-Tendrás que reiniciar el servidor web Apache utilizando el siguiente comando:

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/451c88f9-0492-4cfa-8cbf-5e763e039322)

Paso 4: Descarga e instalación WORDPRESS
Una vez completados todos los preparativos, es el momento de instalar WordPress. Hay dos métodos: configurar WordPress a través de una
interfaz web o editar manualmente el archivo wp-config.php. Nosotros lo vamos a hacer a través de la interfaz web.
-Instala el paquete wget en tu MV. Esto será útil para descargar los archivos de WordPress. Ejecuta este comando en la línea de comandos:
#apt install wget -y

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/44794136-b6d5-4df7-a016-e7e82a3bae6a)

-A continuación, utiliza el comando wget seguido del enlace de descarga de WordPress:
wget https://es.wordpress.org/latest-es_ES.zip -P /tmp
Nota: La opción -P /tmp descarga el comprimido en/tmp

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/9249e278-b0ed-4454-b7ce-850385bde625)

-Una vez que hayas descargado el archivo comprimido, instala la utilidad de descompresión unzip utilizando estos comandos:
#apt install unzip -y

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/641b5678-4f23-444f-b7e9-437a44431b3f)

-El contenido se ha descomprimido en una carpeta que se llama wordpress. Ahora, movemos el contenido de /tpm/wordpress a /var/www/html.
mv -f /tmp/wordpress/* /var/www/html
-Cambio el usuario propietario del documentRoot:
sudo chown -R www-data:www-data /var/www/html
-Reinicia el servicio Apache2:
sudo systemctl restart apache2
-Termina de configurar WordPress a través de un navegador web. Abre un navegador web y escribe la dirección IP del servidor.
http://ip_servidor1/
-Una vez que hayas iniciado la sesión, accederás al panel de administración de WordPress. Ahora puedes empezar a personalizar el sitio web
instalando plugins y temas de WordPress. (ver figuras)
