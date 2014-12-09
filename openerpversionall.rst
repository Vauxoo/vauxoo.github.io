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

El código fuente se encuentra en github. Para obtener el código fuente deberás tener instalado
git que es el sistema de control de versiones utilizado por OpenERP para manejar su código
fuente de ésta manera podrás bajar el mismo, básicamente éste sistema te permite llevar un
seguimiento de los cambios en la historia del proyecto y colaborar eficientemente. Deberás crear tu
cuenta en github para ser capaz de colaborar con el proyecto OpenERP en su desarrollo,
reportando errores, proponiendo tus cambios y dando retroalimentación. Por favor revisa los
manuales de éstas dos herramientas para mayor información.

.. tip::

    Si está en un sistema basado en Ubuntu o Debian deberás instalar git con el siguiente comando::
        
        sudo apt-get install git

Directorio de trabajo
---------------------

Lo primero que haremos es crear el directorio de trabajo donde nuestras fuentes estarán alojadas::

    mkdir source;cd source

Descarga las fuentes
--------------------

.. warning::
    
    Importante el proceso de descarga dependiendo de tu conexión a internet puede ser de hasta 1
    hora, cuando ejecutes el siguiente comando asegurate de estar conectado a internet y de poseer
    al menos 2 gb de espacio disponible en disco.

Para obtener el código fuente de la última versión estable (en éste caso la versión 8.0) ejecuta el
siguiente comando::

  git clone https://github.com/odoo/odoo.git -b 8.0

Ésto creará los siguientes `Directorios <https://github.com/odoo/odoo/tree/8.0/>`_

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

.. _Github: https://github.com/
.. _Git: http://git-scm.com/
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
