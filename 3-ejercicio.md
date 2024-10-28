## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp

´´´
docker network create net-wp
´´´

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: C:\Users\USUARIO\Desktop\ejercicio3\bd

### ¿Qué contiene la carpeta db del host?
# Hasta el momento esta coarpeta está vacía.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

´´´
docker run -d --name srv-bdd -v C:\Users\USUARIO\Desktop\ejercicio3\bd:/var/lib/mysql --env-file=variablesEntornoMysql.txt mysql:8
´´´

´´´
docker network connect net-wp srv-bdd
´´´

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# Ahora la carpeta contiene toda la configuración de mysql; es decir, tiene todos los archivos necesarios para que el servidor funcione. 

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: C:\Users\USUARIO\Desktop\ejercicio3\www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

´´´
docker run -d --name wordpress-container -v C:\Users\USUARIO\Desktop\ejercicio3\www:/var/www/html --env-file=variablesEntornoWp.txt -p 9500:80 wordpress
´´´

´´´
docker network connect net-wp wordpress-container
´´´

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# Al eliminar y crear nuevamente el contenedor se puede ver claramente que las configuraciones no se eliminaron, la entrada y la personalización de la página web persiste.



