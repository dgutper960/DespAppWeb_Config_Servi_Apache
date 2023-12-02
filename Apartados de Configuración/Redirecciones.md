# Redirecciones
- Permiten dirigir al cliente que busca un contenido que ya no se encuentra en esa dirección.
1. Un sitio se instaura en una dirección
    - Los clientenes acceden con normalidad
2. El sitio cambia de dirección
    - Los clinetes untentan acceder con la dirección antigua y el sitio ya no estña disponible
3. Mediante la rediección se puede mandar de forma automática a esos clientes a la nueva dirección.
    1. El cliente hace una petición al servidor con una dirección obsoleta
    2. El servidor contesta diciendo la nueva petición
    3. El cliente hace una nueva petición con la dirección correcta

## Redirecciones temporales
- Código de estado 302

### Configuración
- Esta es la configuración por defecto si no se indica

#### Rediección a un lugar externo:
1. Vamos al fichero:
    * $ nano /etc/apache2/sites-available/nombre_virtual_host.conf

2. En la directiva DocumentRoot /var/www/nombre_virtual_host:

    Redirect "/nombre_sitio_antiguo" "http://nueva_url.dominio"

#### Rediección a un lugar interno:
1. Vamos al fichero:
    * $ nano /etc/apache2/sites-available/nombre_virtual_host.conf

2. En la directiva DocumentRoot /var/www/nombre_virtual_host:

    Redirect "/nombre_sitio_antiguo" "/nuevo_nombre_sitio"

## Redirecciones permanentes
- cahé, proxy, etc.
- Los buscadores (Google) mantienen la posición de la pág en su indexación si tenemos redirecciones permanentes.
- Código de estado 301

### Configuración
- LA ÚNOCA DIFERENCIA RESPECTO A LA ANTERIRIOR ES LA DE ESPECIFICAR CON LA PALABRA "permanet"

#### Rediección a un lugar externo:
1. Vamos al fichero:
    * $ nano /etc/apache2/sites-available/nombre_virtual_host.conf

2. En la directiva DocumentRoot /var/www/nombre_virtual_host:

    Redirect permanet "/nombre_sitio_antiguo" "http://nueva_url.dominio"

#### Rediección a un lugar interno:
1. Vamos al fichero:
    * $ nano /etc/apache2/sites-available/nombre_virtual_host.conf

2. En la directiva DocumentRoot /var/www/nombre_virtual_host:

    Redirect permanet "/nombre_sitio_antiguo" "/nuevo_nombre_sitio"


