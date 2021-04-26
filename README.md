# iaw-practica-Prestashop
Implantación de un sitio PrestaShop en Amazon Web Services (AWS) haciendo uso de contenedores Docker y la herramienta Docker Compose.

> IES Celia Viñas (Almería) - Curso 2020/2021
Módulo: IAW - Implantación de Aplicaciones Web
Ciclo: CFGS Administración de Sistemas Informáticos en Red

**Introducción**
------------
En esta práctica tendremos que realizar la implantación de un sitio PrestaShop en Amazon Web Services (AWS) haciendo uso de contenedores Docker y la herramienta Docker Compose.

**Tareas a realizar**
------------

1. Crear una máquina virtual Amazon EC2. Máquina tipo small con 2GB de RAM:

2. Instalar y configurar Docker y Docker compose en la máquina virtual.

3. Crear un archivo docker-compose.yml para poder desplegar los servicios de PrestaShop, MySQL y phpMyAdmin. Deberá utilizar las imágenes oficiales de Docker Hub.

4. Buscar cuál es la dirección IP pública de su instancia en AWS y comprobar que puede acceder a los servicios de PrestaShop y phpMyAdmin desde una navegador web.


**1.2 Requisitos del archivo docker-compose.yml**
------------
**1.2.1 Networks**

Los servicios definidos en el archivo docker-compose.yml deberán usar dos redes:

    frontend-network
    backend-network

En la red frontend-network estarán los servicios:

    PrestaShop
    phpMyAdmin

Y en la red backend-network sólo estará el servicio:

    MySQL

Sólo los servicios que están en la red frontend-network expondrán sus puertos en el host. Por lo tanto, el servicio de MySQL no deberá estar accesible desde el host.

> (Utilizar dos políticas de seguridad, una front-end y otra back-end)

**1.2.2 Docker restart policies**
Deberá utilizar alguna política de reinicio para que los contenedores se reinicien cada vez que se detengan de forma inesperada.

**1.2.3 Variables de entorno**
Deberá hacer uso de un archivo .env para almacenar todas las variables de entorno que necesite en el archivo docker-compose.yml.

**1.2.4 Orden en el que se inician los servicios**
Deberá indicar el orden en el que se deben iniciar los servicios con la opción depends_on.

https://docs.docker.com/compose/startup-order/


**A tener en cuenta para la instalación de PrestaShop**

La máquina pedirá la dirección y credenciales de la base de datos. Podemos obtener la dirección de mysql para backend siguiendo los pasos indicados al final de presta.sh y las credenciales son las del archivo .env

![](https://i.imgur.com/FoBMSat.png)
Obteniendo dirección mysql

![](https://i.imgur.com/VE8xZC3.png)
Credenciales.

![](https://i.imgur.com/qKtwsoJ.png)
Eliminando install.

docker exec -it <$numero_contenedor> /bin/bash
rm -rf install
![](https://i.imgur.com/goooHo3.png)

Ejemplo de eliminación de install.

**Archivos en el repositorio**
------------
1. **README.md** Documentación.
2. **presta.sh** Ejecutable para instalar docker y docker-compose
3. **docker-compose.yml** Archivo de referencia para docker-compose
4. **.env** Archivo que almacena las variables de entorno.

**Referencias**
------------
- Guía original para la práctica.
https://josejuansanchez.org/iaw/practica-15/index.html



**Editor Markdown**
------------
- Markdown editor.
https://markdown-editor.github.io/