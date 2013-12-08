==========================
Iniciar tu entorno OpenERP
==========================

.. warning::

    Todos los ejemplos en éste documento están basados en Ubuntu_ 13.04 o superior, pero
    conceptualmente son replicables en otras plataformas.

.. warning::

    Todos los ejemplos en éste documento son ejecutados como usuario "Sin Privilegios root" cuando
    se requieran los privilegios de un superusuario se mostrará el comando acompñado del comando
    ``sudo``

Instalación desde las fuentes
=============================

El código fuente se encuentra en Launchpad_. Para obtener el código fuente deberás tener instalado
Bazaar_ que es el sistema de control de versiones utilizado por OpenERP para manejar su código
fuente de ésta manera podrás bajar el mismo, básicamente éste sistema te permite llevar un
seguimiento de los cambios en la historia del proyecto y colaborar eficientemente. Deberás crear tu
cuenta en launchpad para ser capaz de colaborar con el proyecto OpenERP en su desarrollo,
reportando errores, proponiendo tus cambios y dando retroalimentación. Por favor revisa los
manuales de éstas dos herramientas para mayor información.

.. tip::

    Si está en un sistema basado en Ubuntu o Debian deberás instalar Bazaar_ con el siguiente comando::
        
        sudo apt-get install bzr bzrtools

Directorio de trabajo
---------------------

Lo primero que haremos es crear el directorio de trabajo donde nuestras fuentes estarán alojadas::

    mkdir source;cd source

Descarga el Script de inicio
----------------------------

Openerp te provee un Script para automatizar las tareas de crear y compartir los repositorios de su
código fuente éste Script lo podemos obtener con el siguiente comando::

  bzr cat -d lp:~openerp-dev/openerp-tools/trunk setup.sh | sh

Éste comando creará dos archivos el el directorio ``source`` creado anteriormente::

  -rw-rw-r--  1 openerp openerp 5465 2012-04-17 11:05 Makefile
  -rw-rw-r--  1 openerp openerp 2902 2012-04-17 11:05 Makefile_helper.py

Te recomendamos leer la ayuda de las opciones disponibles con éste Script ejecutando el siguiente
comando::

  make help

Descarga las fuentes
--------------------

.. warning::
    
    Importante el proceso de descarga dependiendo de tu conexión a internet puede ser de hasta 1
    hora, cuando ejecutes el siguiente comando asegurate de estar conectado a internet y de poseer
    al menos 2 gb de espacio disponible en disco.

Para obtener el código fuente de la última versión estable (en éste caso la versión 7.0) ejecuta el
siguiente comando::

  make init-v70

Ésto creará los siguiente directorios dentro  de ``source`` y descargará la última versión ``trunk``
de OpenERP y ajustará los directorios para trabajar con OpenERP V70::

  drwxrwxr-x  3 openerp openerp 4096 2012-04-17 11:10 addons
  drwxrwxr-x  3 openerp openerp 4096 2012-04-17 11:10 misc
  drwxrwxr-x  3 openerp openerp 4096 2012-04-17 11:10 server
  drwxrwxr-x  3 openerp openerp 4096 2012-04-17 11:10 web

Instalando las dependencias
---------------------------

Algunas dependencias son necesarias para usar OpenERP. Dependiendo de tu entorno, necesitarás
instalar los siguientes paquetes::

  sudo apt-get install graphviz ghostscript postgresql-client \
            python-dateutil python-feedparser python-gdata \
            python-ldap python-libxslt1 python-lxml python-mako \
            python-openid python-psycopg2 python-pybabel python-pychart \
            python-pydot python-pyparsing python-reportlab python-simplejson \
            python-tz python-vatnumber python-vobject python-webdav \
            python-werkzeug python-xlwt python-yaml python-imaging \
            python-matplotlib  python-unittest2 python-mock python-docutils \
            python-jinja2 python-psutil

.. tip::

    Si estás en un entorno donde OpenERP y el servidor de bases de datos Postgres se encuentran en
    la misma máquina deberás instalar PostgreSQL si ya lo tienes instalado omite éste comentario.::
    
        sudo apt-get install postgresql

Iniciamos el usuario de base de datos
-------------------------------------

Para conectarnos a PostgreSQL requerimos contar con un usuario de Bases de Datos lo creamos con el
siguiente comando::

  make db-setup

La salida que te retornará éste comando será::

    psql: FATAL:  role "tuususariolinux" does not exist
    # setup a postgres user
    sudo su - postgres -c "createuser -s $USER"

Si lo ejecutas por segunda vez te debería aparecer::

    # setup a postgres user
    sudo su - postgres -c "createuser -s $USER"
    createuser: creation of new role failed: ERROR:  role "tuusuariolinux" already exists

Si ésto sucede todo está bien el comando ha funcionado correctamente.

Ejecutamos el servidor
----------------------

Con éste comando ponemos a correr el servidor, recordemos que OpenERP es un servicio siempre
corriendo en el sistema por lo que veremos una serie de salidas una vez ejecutemos éste comando::

  make server

Probamos que todo esté en orden
-------------------------------

Para probar que todo está en orden podemos abrir nuestro navegador en el siguiente enlace
http://localhost:8069/ debería aparecerte la ventana de creación de bases de datos.

.. _Launchpad: https://launchpad.net/
.. _Bazaar: http://bazaar.canonical.com/en/
.. _Ubuntu: http://www.ubuntu.com

Opciones de la Línea de comandos
================================

.. program:: openerp-server

Usando el comando abajo destro del directorio ``server`` podemos ver todas las opciones posibles
para correr el servidor OpenERP::

  ./openerp-server --help

Configuraciones
===============

.. _getting_started_configuration-link:

Un archivo de configuración estará disponible una vez arranques el servidor en::

    * ``~/.openerp_serverrc``

Ya estamos listos para comenzar a trabajar.
