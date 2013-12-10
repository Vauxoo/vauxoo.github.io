=====================================
PostgreSQL - Resolucion de Problemas.
=====================================

El manual anterior está diseñado para que todo funcione con un usuario \*nix llamado `openerp` si
no es así acá algunas soluciones a los problemas.

Caso 1: El usuario \*nix no se llama openerp
--------------------------------------------
.. tip::
    (por ej, lo descargué todo en mi máquina local y mi usuario se llama `pedro`)

**Solución:**

Deberás crear manualmente el usuario PostgreSQL `pedro`::

    $sudo su -c postgres "createuser -s pedro"
    >>Responde las preguntas con el password con No - Si - No

Acabamos de crear un usuario postgres que no es super user, se llama como tu usuario \*nix y puede
crear bases de datos es el ususario que utilizaremos para nuestros desarrollos.

    - **Situación A: Postgres 8.4 (Ubuntu 12.04)**

Editamos el archivo::

    $nano /etc/postgresql/8.4/main/pg_hba.conf

Cambiamos la línea que dice::

    local all all ident

por::

    local all all md5

Reiniciamos PostgreSQL::

    $sudo services postgresql restart

Una vez reiniciado PostgreSQL, ``iniciamos openerp conectandonos con otro ususario diferente al
conectado \*``.

    - **Situación B: Postgres 9.x (Ubuntu 12.04)**

No necesitamos hacer más nada por ahora.

