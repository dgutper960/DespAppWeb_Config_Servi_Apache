# OPCIONES DE DIRECTORIORIOS

## Directiva: Options
### All
- Todas las opciones (excepto MultiViews)

### FollowSyLinks
- El sitio web ofrece ver directorios mediante enlaces simbólicos
- Puede probocar problemas de seguridad.

### Indexes
- Definimos los nombres de ficeros que se buscan por defecto (como index.html)
- Si no existe ninguno muestra un cod de error.

### MultiViews
- Ofrece versiones de los recursos dependiendo de diferenrtes opciones (idiomas)

### SymLinksfOwnerMatch
- Solamente permite seguir recursos de un enlace sibólico si ambos tienen los mismos propietarios.

### ExecCGI
- Permite que el usuario introduzca scripts en el servidor.

# TRABAJAMOS CON LAS CONFIGURACIONES
## Vamos al directorio /etc/apache2/ y entramos en el fichero de configuración principal
- $ nano /etc/apache2/apache2.conf
### Directory /var/www/ -> y todos sus subdirectorios
- Vemos las opciones que están habilitadas por defecto

### En /etc/apache2/mods-available/

# Opción por defecto Indexes
- Encontramos el fichero dir.conf
    - Indica la lista de nombres de fichero que se buscan por defecto
- Si no se encuentran coincidencias, el servidor muestra una lista con todos los ficheros del sitio. Esta opción debería deshabilitarse por seguridad.

## Deshabilitando mostrar lista de ficheros del sitio si no se encuentra uno de indexes
- Nos movemos a /etc/apache2/sites-available/
- Entramos en la configuracion del sitio que queramos
    - $ nano _mysitio.conf_
- Despues de la línea "DocumentRoot" creamos un Directory para sobreescribir las opciones
    <Directory /var/www/mysitio>
        Options -Indexes
    </Directory>
    - Con esto eliminamos sólo esa opción (mantiene las anteriores)
* -> Si hiciesemos esto otro:
    <Directory /var/www/mysitio>
        Options Indexes
    </Directory>
* Sobreescribe la configuracion anterior y deja sólo esa opción
* -> Si hiciesemos esto otro:
    <Directory /var/www/mysitio>
        Options Indexes +
    </Directory>
* Mantenemos las anteriores y añadimos Indexes

# Opcion por defecto FollowSyLinks
- Permite seguir enlaces simbólicos de fuera del servidor
## Para desactivar esta opción
- Hacemos como antes y eliminamos la opcion FollowSyLinks
## También activamos la opción SymLinksfOwnerMatch
* Si quisieramos hacer este cámbio en la configuración principal:
- Nos vamos a /etc/apache2/apache2.conf
- Comentamos y añadimos las líneas de las opciones swgún interese
