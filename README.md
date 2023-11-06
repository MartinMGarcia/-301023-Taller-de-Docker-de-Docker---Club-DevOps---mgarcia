# WordPress con mysql usando docker compose

Este archivo .yml define dos servicios: wordpress y db, que se comunican entre sí para implementar un sitio web de WordPress con una base de datos mysql.

## Servicio wordpress

* `image: wordpress`: Esta línea especifica la imagen de docker que se va a usar para el servicio wordpress. En este caso, se usa la imagen oficial de WordPress, que se puede encontrar en [Docker Hub].
* `restart: always`: Esta línea indica que el servicio wordpress se reiniciará automáticamente si se detiene por algún motivo.
* `ports: - 8080:80`: Esta línea expone el puerto 80 del contenedor wordpress al puerto 8080 del host. Esto permite acceder al sitio web de WordPress desde el navegador usando la dirección http://localhost:8080.
* `environment: ...`: Esta sección define las variables de entorno que se pasan al contenedor wordpress. Estas variables configuran la conexión con la base de datos mysql y el nombre de la base de datos que se va a usar para WordPress.
* `volumes: - wordpress:/var/www/html`: Esta línea monta un volumen llamado wordpress en el directorio /var/www/html del contenedor wordpress. Esto permite persistir los archivos del sitio web de WordPress, como los temas, los plugins y los medios.

## Servicio db

* `image: mysql:5.7`: Esta línea especifica la imagen de docker que se va a usar para el servicio db. En este caso, se usa la imagen oficial de mysql versión 5.7, que se puede encontrar en [Docker Hub].
* `restart: always`: Esta línea indica que el servicio db se reiniciará automáticamente si se detiene por algún motivo.
* `environment: ...`: Esta sección define las variables de entorno que se pasan al contenedor db. Estas variables configuran la base de datos que se va a crear para WordPress, el usuario y la contraseña que se van a usar para acceder a ella, y una contraseña aleatoria para el usuario root de mysql.
* `volumes: - db:/var/lib/mysql`: Esta línea monta un volumen llamado db en el directorio /var/lib/mysql del contenedor db. Esto permite persistir los datos de la base de datos mysql.

## Volumenes

* `wordpress:`: Esta línea define un volumen llamado wordpress, que se usa para el servicio wordpress.
* `db:`: Esta línea define un volumen llamado db, que se usa para el servicio db.