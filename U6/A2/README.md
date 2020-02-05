# **UT6-A2: Salt-Stack**

## 1. Preparativos
| Config   | MV1           | MV2          |
| -------- | ------------- | ------------ |
| Alias    | Master        | Minion       |
| Hostname | master25g     | minion25g    |
| SO       | OpenSUSE      | OpenSUSE     |
| IP       | 172.19.25.31  | 172.19.25.32 |

## 2. Master: instalar y configurar
Vamos a la máquina 1 y lanzamos **"zypper install salt-master"** para instalar la herramienta de "servidor".

![Instalación server](img/1.png)

Modificamos **/etc/salt/master** para configurar nuestro Master.

![Configuracion server](img/2.png)

Ahora **activamos** el servicio en el arranque del sistema y lo **iniciamos**.

![Activacion server](img/3.png)

 Por último **comprobamos** los "Minions" aceptados, vemos que no tenemos ninguno todavía.

![Comprobacion1](img/4.png)

## 3. Minion

### 3.1 Instalación y configuración
Ahora en la máquina 2 lanzamos **"zypper install salt-minion"** para instalar la herramienta de "cliente".

![Instalación cliente](img/5.png)

Vamos a **/etc/salt/minion** y configuramos el Master.

![Configuración cliente](img/6.png)

Ahora **activamos** el servicio en el arranque y lo **activamos** como hicimos en el servidor.

![Activación cliente](img/7.png)

Comprobamos que no tenemos el servicio apache2 instalado.

![Apache2](img/8.png)

### 3.2 Aceptación desde el Master
Volvemos a la máquina 1 y lanzamos "salt-key -L" y vemos que tenemos la petición del Minion.

![Petición](img/9.png)

Aceptamos la petición y lo comprobammos.

![Aceptada](img/10.png)

### 3.3 Comprobamos conectividad
Ahora desde el master lanzamos los siguientes comandos para las comprobaciones.

![Comprobacion2](img/11.png)

![Comprobacion3](img/12.png)

## 4. Salt States
### 4.1 Preparar el directorio para los estados
Creamos los directorios **/srv/salt/base** y **/srv/salt/devel**.

Y creamos el fichero **roots.conf** en **/etc/salt/master.d**.

![Creación fichero roots](img/13.png)

Reiniciamos el servicio.

![Reiniciar servicio](img/14.png)

### 4.2 Crear un nuevo estado
Ahora creamos el fichero **init.sls** en la ruta **/srv/salt/base/apache** y añadimos lo siguiente.

![Estado apache](img/15.png)

### 4.3 Asociar Minions a estados
Creamos el fuchero **top.sls** en **/srv/salt/base** y definimos lo siguiente:

![Fichero top](img/16.png)

### 4.4 Comprobar estados definidos
Ahora lanzamos lo siguiente para consultar los estados:

![Comprobacion4](img/17.png)

### 4.5 Aplicar nuevo estado
Ahora lanzamos los dos siguientes comandos para ver que no hay errores en las definiciones:

![Comprobacion5](img/18.png)

![Comprobacion6](img/19.2.png)

Por último aplicamos el estado.

![Aplicar apache](img/20.png)

## 5. Crear más estados
### 5.1 Crear estado "users"
Creamos el directorio **/srv/aslt//base/users** y dentro el fichero **init.sls**.

![Fichero users](img/19.png)

Y aplicamos el estado.

![Users1](img/22.png)

![Users2](img/22.1.png)

![Users3](img/22.2.png)

### 5.2 Crear estado "directories"
Creamos el directorio **/srv/aslt//base/directories** y dentro el fichero **init.sls**.

![Fichero directories](img/23.png)

Aplicamos el estado.

![Aplicar directories](img/24.png)

## 6. Añadir Minion de otro SO
Ahora vamos a una máquina 3 con SO Windows.

En la instalación nos pedirá la IP del Master y el hostname del Minion.

![Configuracion](img/25.png)

Por último vamos al Master y aceptamos al Minion.

![Aceptar Minion2](img/26.png)
