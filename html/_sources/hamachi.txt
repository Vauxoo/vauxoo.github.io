=========================
Cómo trabajar con hamachi
=========================

Hamachi es un servicio para la creación de redes VPN.

En Linux.
---------

Todos los comandos acá indicados son ejecutados en una consola sin privilegios de root, es lo que significa el hecho de que comienzan con el símbolo "$".

Este símbolo no va incluído en ningún comando es solo para referencia.

Descargalo::

    $ wget -c https://secure.logmein.com/labs/logmein-hamachi_2.1.0.81-1_amd64.deb

Instala la dependencia::

    $ sudo apt-get install lsb-core

Instala el paquete::

    $ sudo dpkg -i logmein-hamachi*.deb

Haz login contra el servidor VPN::

    $ sudo hamachi login

Agrega tu nick, para poder indentificar tu máquina en la red::

    $ sudo hamachi set-nick [TU-NOMBRE-DE-EQUIPO]

Solicita acceso al usuario hamachi que administra la red, en
el caso durante el proceso de desarrollo es con la cuenta de Nhomar::

    $ sudo hamachi attach-net nhomar@gmail.com

Envía un correo a nhomar@vauxoo.com para asegurarte que te apruebe.


En Windows 7.
-------------

TODO

En Windows XP.
--------------

TODO

En Windows Server.
------------------

TODO
