# Alias:
- Permite definir parte de la url dónde los recursos estén en un directorio aparte.

## Se pueden ofrecer recursos que estém en un directorio aparte de DocumentRoot
-  Se crean permisos de acceso para ese directorio.

# Negociación de contenidos
- Se ofrece un contenido según cierta información de la cabecera del cliente.
- Se suele usar para los idiomas.

## Podemos tener html en diferentes idiomas y mostrar el adecuado según la info del head
### 1ª Forma de configuración
1. Se ha definido dentro de la carpeta de contenidos una carpeta llamada internacional
2. En este directorio, se han añadido los ficheros
    - index.html.en
    - index.html.es
    - index.html.var (lo obviaremos por el momento)

3. En el directorio de configuración para el sitio
    $ nano /etc/apache2/sites-avalible/nombreSitio.conf
    - Vamos a la directiva DocumentRoot y añadimos:
        <Directory /var/www/nombreSitio/internacional>
            Options +Multiviews
        </Directory>
4. Reiniciamos el servicio
 - Según la configuración del navegador nos va a mostrar uno de los diferentes HTML

### 2ª Forma de configuración (ficheros tipo mapa)
- Ahora si nos fijaremos en el fichero con extensión .var
    * Si abrimos este fichero lo que vamos a encontrar son indicaciones sobre que fichero se tiene que abrir según la configuración del navegador del cliente.
    ej:
        ````
        URI: index

        URI: index.html.en
        Content-type: text/html
        Content-language: en

        URI: index.html.es
        Content-type: text/html
        Content-language: es
        ````

1. Creamos el fichero mencionado con la configuración de mapa deseada siguiendo el ejemplo
2. En la configuración del sitio establecemos la directiva DocumentRoot correpondiente.
    $ nano /etc/apache2/sites-avalible/nombreSitio.conf
    - Vamos a la directiva DocumentRoot y añadimos:
        <Directory /var/www/nombreSitio/internacional>
            DirectoryIndex index.var
            AddHandler type-map .var
        </Directory>

    * Con AddHandler decimos a apache como tiene que tratar el .var
        - En este caso se indica que el fichero es de tipo mapa.

