## File Browser con Docker Compose

### Introduccion
FileBrowser es un navegador de archivos muy potente a traves de un interfaz web que permite crear, compartir, subir archivos y carpetas a tu red local.

### Instalación
Para instalar vamos a usar la imagen de hurlenko

### Puertos
* 8080 por defecto 
* 8200 desde el navegador

### Volumenes
El contenedor utiliza dos volumenes: 
1. data donde vamos a exponer lo que queremos compartir de nuestra máquina
2. config donde vamos a guardar la base de datos que utiliza filebrowser

### Creación del Contenedor
El archivo docker-compose.yml quedaría así:

```docker

version: "3"

services:

  filebrowser:
    image: hurlenko/filebrowser:latest
    environment:
      - UID=1000
      - GID=1000
      - TZ=Europe/Madrid
    ports:
      - "8200:8080"
    volumes:
      - /home/user/data:/data
      - ./fb-config:/config
```

### Usuario por defecto
El usuario y contraseña por defecto son admin

Para acceder IP:8200
