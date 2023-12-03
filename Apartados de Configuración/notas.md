## Instrucciones Configuración Servidor 
### Ditribuidos distintintos ficheros de configuración

### fichero /etc/apache2/conf-available
- Configuración adicional
- Hacia donde se crean enlaces simbólicos desde conf-enabled
    - comando $ a2enconf/a2disconf _nombre_fichero_-> crea/elimina los enlaces simbólicos.
- Se permite tener configuraciones que no están acttivas.

##### para que la configuracin forme parte del servidor debemos tener un enlace simbólico desde conf-enabled al fichero en available
- De esta forma podemos tener configuraciones que estén acttivas y otras que estén inactivas

## Directiva Dyctory en fichero /etc/apache2.conf
- Indica el directorio donde vamos a tener todos nuestras páginas web.
- Podemos elegir entre dos dierectorios predefinidos (comentando y descomentando).

### fichero ports.conf
- Controla el puerto 

### fichero envars 
- Declara distintas variables de entorno


##### Cada cambio requiere un reinicio del servicio

# PRINCIPALES DIRECTIVAS
#### Las vemos en el fichero /etc/apache2.conf
(se requiere revisra la documentación oficial de cada una)
## Timeout
- Tiempo que el servidor espera para recibir o enviar una respuesta (300seg).

## KeepAlive
- Avitva las conexiones persistentes.

## MaxKeepAliveRequests
- Indica el número de peticiones y respuestas en una conexión presistente.

## KeepAliveTimeout
- Tiempo de espera en una conexión persistente.
- Importante para el rendimiento (módulos de multiprocesamiento).

## User
- Usuario de Apache para trabajar.

## Group
- Grupo de Apache para trabajar.

## LogLevel
- Nivel de información en los ficheros log.

## LogFormat
- Formato de la información que se guarda en los ficheros log.

## Directory o DirectoryMatch
- Establece las opciones de un directorio y todos sus directorios.

## Files o FilesMatch
-  Establece un contexto para un fichero o conjunto de ficheros.

## ErrorLog
- Establece el fichero dónde se guardan los mensajes de error.



# FUNCIONAMIENTO BÁSICO DE UN SITIO WEB ######

#### Podemos entender un sitio web como un directorio que va a contener todos los recursos que va a servir nuestro servidor.

#### Cada sitio web necesita una dirección y un puerto.
- Podríamos pensar que necessitamos distintos servidores web para cada uno de nuestros sitios web.

## Apache2 dispone de Virtual Hosting
- Podemos tener distintintos sitios web en la misma máquia.
- Con una misma direccion IP y un mismo puerto, cambiando el nombre con el que se accede al servidor, este es capaz de servir distintos sitios web.
- Por defecto, tenemos un sitio web de ejemplo.

#### Las distintas configuraciones de nuestros servidios virtuales:
- Un servicio virtual por cada sitio web.
- Serán guardados en etc/apache2/sites-available/_nombre_sitio.conf_
- Tenemos un fichero por defecto y su correspondiente enlace simbólico.

#### Dentro del la configuración del sitio virtual:
- Vamos a encontrar la directiva DocumentRoot que va a indicar el directorio que va a contener los recursos del sitio -> **DocumentRoot /var/www/html**.

- Tendrá las mismas opciones que se pusieron en el fichero de configuración que afectava a todos sus hijos.

#### El sitio virtual guardará las sig variables de entorno:
- ErrorLog ${APACHE_LOG_DIR} en el fichero -> /error.log (guarda los errores)
- CustomLog ${APACHE_LOG_DIR}/acces.log combined (registro desde dónde se hacen peticioes al servidor).

### Cada vez que creamos un virtual host su DocumentRoot va a apuntar a un dirctorio dento del directorio establecido en la directiva de configuración principal.

# VEMOS LAS CONFIGURACIONES ESTABLECIDAS DE LA SIG MANERA:
- Dentro de /etc/apache2/sites-enabled -> ls -la
- Vemos los enlaces simbólicos que definen las configuraciones establecidas
- Al ser un enlace simbólico lo podemos editar desde sites-enabled (nano _fichero_)
- Podemos ver en él la directiva DocumentRoot (directorio para recursos del servidor)
- Podemos ver las variables de entorno antes mencionadas.

## Si vamos a la ruta indicada en DocumentRoot (/var/www/html)
- Vemos un fichero index.html
- Cada vez que vamos al servidor, vemos esa página index.html


# CONFIGURACION DE VIRTUAL HOST

## Dentro de /etc/apache2/sites-avalalble/_nombre_sitio.conf
### Encontramos la directiva VirtualHost
- 1er Parametro indica las direcciones ip que tienen acceso. (* = todas)
- 2º Parametro indica el puerto por el que se accede. (defalut = 80)
## Directivas del VirtualHost
- #ServerName: www.example.com
    - Imprescindible en acceso por nombre, para diferenciar entre sitios.
    - Por defecto comentada, cuando solo hay un sitio no es necesaria.

