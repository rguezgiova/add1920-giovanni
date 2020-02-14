# **UT6-A3: Contenedores con Docker**

## 1. Habilitar el acceso a la red externa a los contenedores
Vamos a "YaST" > "Ajustes de red" > "Encaminamiento" y habilitamos el reenvío de Ipv4.

![Habilitar reenvío](img/1.png)

## 2. Instalación y primeras pruebas
### 2.1 Instalación
Abrimos una terminal y lanzamos "zypper in docker".

![Instalación docker](img/2.png)

Ahora iniciamos el servicio y vemos su versión.

![Inicio servicio y versión](img/3.png)

## 2. Creación manual
### 2.1 Crear una imagen manualmente
Vemos las imágenes que tenemos, en este caso todavía no tenemos ninguna.

![Imagenes1](img/4.png)

Buscamos en los repositorios con la etiqueta "debian".

![Busqueda debian](img/5.png)

Nos descargamos la imagen "debian9".

![Descarga debian9](img/6.png)

Vemos todos los contenedores.

![Ver contenedores](img/7.png)

Ahora vemos solo los que están en ejecución.

![Contenedores ejecución1](img/8.png)

Creamoso un contenedor que se llame **con_debian** a partir de la imagen que acabamos de descargar y ejecutamos **/bin/bash**.

![con_debian](img/9.png)

### 2.2 Personalizar el contenedor
Comprobamos que estamos en debian.

![Comprobamos debian](img/10.png)

Actualizamos los repositorios.

![Actualizar repositorios](img/11.png)

Instalamos Nginx.

![Instalar Nginx](img/12.png)

Instalamos el editor Vi.

![Instalar Vi](img/13.png)

Iniciamos el servicio Nginx.

![Iniciar Nginx](img/14.png)

Lanzamos "ps -ef", vemos que no existe, lo intentamos instalar, pero no existe el paquete.

![Lanzamos ps](img/15.png)

Creamos el fichero **holamundo.html** con nuestro nombre.

![Fichero holamundo](img/16.png)

Creamos el siguiente script:

![Fichero script](img/17.png)

### 2.3 Crear una imagen a partir del contenedor
Ahora vamos a crear una nueva imagen, para ello tenemos que saber la ID del contenedor que ya tenemos, hacemos lo siguiente:

![Creación contenedor Nginx](img/18.png)

Ahora paramos el contenedor "con_debian", vemos que se ha parado y lo eliminamos.

![Eliminar con_debian](img/19.png)

## 3. Crear contenedor a partir de nuestra imagen
### 3.1 Crear contenedor con Nginx
Ahora creamos el contenedor con Ngnix instalado.

![Crear contenedor](img/20.png)

### 3.2 Comprobamos
Vemos todos los contenedores.

![Ver contenedores](img/21.png)

Vemos que inicia la máquina

![Arrancando](img/22.png)

Abrimos un navegador y vemos que funciona la página por defecto de Nginx.

![Página nginx](img/23.png)

Ahora vamos a visualizar el fichero html añadiendo lo siguiente:

![fichero personalizado](img/24.png)

### 3.3 Migrar la imágen a otra máquina
Ahora guardamos la imagen con nuestro nombre y se la pasamos a un compañero.

![Guardar imagen](img/25.png)

Ahora importamos la imagen de nuestro compañero.

![Importar imagen](img/26.png)

## 4. Dockerfile
### 4.1 Preparar ficheros
Creamos el directorio **docker25a** en nuestro home con los ficheros **holamundo.html** y **server.sh** creados anteriormente.

![ficheros docker25a](img/27.png)

Ahora creamos el fichero **Dockerfile** con lo siguiente:

![fichero dockerfile](img/28.png)

### 4.2 Crear imagen a partir del Dockerfile
Ahora lanzamos lo siguiente:

![ejecutar dockerfile](img/29.png)

Comprobamos que está nuestra imagen.

![Comprobamos imagen2](img/30.png)

### 4.3 Crear contenedor y comprobar
Ahora crearemos el contenedor con la imagen anterior.

![Crear contenedor2](img/31.png)

Ahora abrimos un navegador y probamos.

![Comprobar página2](img/32.png)

Y comprobamos el fichero **holamundo.html**.

![Comprobar holamundo2](img/33.png)

### 4.4 Usar imágenes ya creadas
Creamos el directorio **docker25b** y dentro creamos el fichero **Dockerfile** con lo siguiente:

![Fichero Dockerfile b](img/34.png)

Creamos la imagen.

![Crear imagen b](img/35.png)

Creamos el contenedor.

![Creamos contenedor b](img/36.png)

Comprobamos en un navegador.

![Comprobar b](img/37.png)

## 5. Limpiar contenedores e imágenes
Ahora borramos todos los contenedores.

![Borrar contenedores](img/38.png)

Y hacemos lo mismo con las imágenes.

![Borrar imágenes](img/39.png)
