# TABABAJERMOS CON LA CONFIGURACIÓN DE ACCESO

## Vamos a trabajar con accesos desde inferfaces internas y externas:
-  Crearemos un VirtualHost llamado interna
-  Crearemos un VirtualHost llamado externa
* Creamos y configuramos ambos siguendo las instrucciones anteriores de modo que tengamos los respectivos enlaces simbólicos en sites-enabled.

## Una vez terminada la configuración detallada en estas instrucciones:
- En este caso la selección de acceso será la procedencia de la petición y no el nombre del ServerName
### Cuando accedamos por la red interna me va a mostrar su correspondiente sitio
### Cuando accedamos por la red externa me va a mostrar su correspondiente sitio


## Entramos al fichero de configuración del VirtualHost
- cd /etc/apache2/sites-available/interna.conf
    - En el parametro de VirtualHost ponemos la ip a la que se le mostrará este sitio
- cd /etc/apache2/sites-available/externa.conf
    - En el parametro de VirtualHost ponemos la ip a la que se le mostrará este sitio

## Si quisiera cambiar la escucha del puerto debemos ir al archivo ports.conf
- $ nano /etc/apache2/ports.conf
    - Editamos el puerto por el que escucha nuestro servidor

#### Para esta configuración se recomienda deahabilitar el 000-default
- El motivo es que no se discrimina por nombre

#### Para acceder a diferentes puertos se debe especificar añadiendo dos puntos tras la ip y el num de puerto.









