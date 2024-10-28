# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)

´´´
docker run -d -p 80:80 --name srv-web -v C:\Users\USUARIO\Desktop\nginx\html:/usr/share/nginx/html nginx:alpine
´´´

### ¿Qué sucede al ingresar al servidor de nginx?
# La página muestra un error 403 Forbidden, el cual es un error que arroja el servidor provocado por una petición del navegador del usuario que es considerada errónea.

### ¿Qué pasa con el archivo index.html del contenedor?
# El archivo index.html no existe, por ende al realizar una petición desde el cliente (navegador), el servidor no lo va a encontrar.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# Añadiendo el archivo index.html en el directorio especificado del host, ahora al intentar acceder al servidor muestra el archivo descargado.

### Eliminar el contenedor

´´´
docker stop srv-web
´´´
´´´
docker rm srv-web
´´´

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
# Ahora muestra sin problemas el archivo index.html, pues los directorios son los mismos y no se han eliminado estos.

### ¿Qué hace el comando pwd?
# El comando pwd muestra por consola la ruta desde donde se está trabajando actualmente.
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

