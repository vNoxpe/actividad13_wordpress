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

# INSTALACIÓN DE DOCKER EN LINUX UBUNTU

1º.- DESINSTALACIÓN DE PAQUETES QUE PUEDEN ENTRAR EN CONFLICTO:

$ for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/5f961ad4-cb48-4d45-ba3c-53e8f68dfeaa)

2º.- INSTALACIÓN USANDO UN REPOSITORIO
Existen diferentes maneras de instalación de docker. Vamos a utilizar la instalación utilizando el repositorio apt.

sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/7c4bf84b-f6bd-482b-8504-9388142c7c39)

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/31a63f93-af76-44cb-bc71-fcafce0cf8fb)

3º.- INSTALACIÓN DEL MOTOR DE DOCKER


sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/34e98036-c709-4c41-8705-405b9753b4a5)


COMPROBACIÓN INSTALACIÓN DOCKER
docker version
![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/1d8b7e0f-230e-43d9-8909-fc66e744c10f)

docker run hello-world
![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/a1ff0532-28d9-4242-9096-621fd1f1229d)

COMPROBACIÓN INSTALACIÓN DOCKER-COMPOSE
docker compose version

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/e1b4cfd9-87e4-4e32-a682-b310e0d7c34a)

# Descarga e instalación WORDPRESS
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
#ejeccutamos el siguiente comando
![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/8f842e9f-40cf-41b3-b56d-bc315109c00c)

-El contenido se ha descomprimido en una carpeta que se llama wordpress. Ahora, movemos el contenido de /tpm/wordpress a /var/www/html.
mv -f /tmp/wordpress/* /var/www/html

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/be401a4a-ff9f-4fd6-b7a6-3899efe75a53)

-Cambio el usuario propietario del documentRoot:
sudo chown -R www-data:www-data /var/www/html

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/c8aa4e6d-7534-4119-8eda-d93c280a7d82)

-Reinicia el servicio Apache2:
sudo systemctl restart apache2

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/2b1d203c-703b-483e-b4af-2ef2c8ba10a4)

-Termina de configurar WordPress a través de un navegador web. Abre un navegador web y escribe la dirección IP del servidor.
http://ip_servidor1/

![image](https://github.com/vNoxpe/actividad13_wordpress/assets/144890599/3a064dc2-0fb9-4390-8e2d-4eca46be39de)

-Una vez que hayas iniciado la sesión, accederás al panel de administración de WordPress. Ahora puedes empezar a personalizar el sitio web
instalando plugins y temas de WordPress. (ver figuras)
