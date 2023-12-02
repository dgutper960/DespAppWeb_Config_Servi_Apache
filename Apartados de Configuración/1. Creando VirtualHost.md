# Pasos para crear un sitio web en nuestro VirtualHost

## Por precaución vamos a copiar el fichero por defecto y lo iremos modificando
- Vamos a /etc/apache2/sites-avalible y copiamos el fichero por defecto a otro
$ cp 000-defautl.conf nuevo.conf
- Entramos al fichero nuevo con nano y ahí editamos:
    - Descomentamos la línea de ServerName y le ponemos el nombre y dominio ej. nuevositio.com
    - Editamos la directiva de DocumentRoot y sustituimos 'html' por nuevositio
    - Ponemos nuevos nombres a los ficheros log de error y acceso:
        - Añadimos nuevositio con barrabaja ej .-
            ErrorLog ${APACHE_LOG_DIR}/error_nuevositio.log
            CustomLog ${APACHE_LOG_DIR}/acces_nuevositio.log combined
    * Si no hacemos esto últmo todos los errores y accesos se guardarán en el mismo fichero y esto resultá ser un caos en el caso de acceder a la información.
    * Para este ejemplo hemos creado nuevositio y nuevositio2

## Sería interesante que los ficheros que vamos a servir sean propiedad de apache
- Vamos a /var/www y creamos el directorio del sitio ($ mkdir nuevositio)
- Los modificamos para que el propietario sea apache, para evitar errores de permisos
    $ chown -R www-data:www-data nuevositio
    - Con $ ls -la verificamos que el directorio sea propiedad de www-data www-data

## Hacemos que el fichero nuevositio forme parte de la configuración de apache2
- Nos movemos a /etc/apache2/sites-enabled:
    - $ a2ensite nuevositio
- Reiniciamos el servicio para que apliquen los cámbios
    - $ systemctl reload apache2

## Debemos tener en cuenta que si entramos al servidor por la ip:
- NOS VA A MOSTRAR LA PÁG POR DEFECTO 000-default
- Esto es debido a que la directiva de ServerName está comentada y ello permite entrar por ip, el los otros sitios esta línea está descomentada y el nombre es requerido.

### Si en este punto vammos a sites-enabled vemos que están los enlaces simbólicos incluido el 000-default
#### Lo podemos quitar de la siguiente forma:
- cd /etc/apache2/sites-enabled
    - $ a2dissite 000-default.conf
#### Si accedemos ahora vemos que entra en el primer sitio que encuentra (orden alfavetico)
#### Con esto en cuenta y como medida de seguridad, podemos crear un index.html que sea el que se muiestra por defecto y evitar que se pueda obtener información con solo tener la ip.
- Nos movemos a la ruta /var/www/html
    - Cambiamos de nomnbre el index original para no borrarlo
    - Ponemos un nuevo id con un mensaje cualquiera (sin mostar información).


