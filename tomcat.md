Cambiar el adaptador de red de las dos máquinas a adaptador puente y comprobar el ping entre las
máquinas y el 8.8.8.8.

nmap -sV ip_red/mascara_red
nmap -A ip_maquina/mascara_maquina
msfconsole
search tomcat_mgr_login
use auxiliary/scanner/http/tomcat_mgr_login
show options --> Centrarse en RHOSTS(víctima) y RPORT
set rhosts 192.168.1.144
run
set user_as_pass true
set username tomcat
run


-Cambiar el adaptador de red a adaptador puente:
Configurar las máquinas virtuales para que utilicen un adaptador de red en modo puente. 
Esto permite que las máquinas virtuales se conecten directamente a la red física y obtengan direcciones IP 
de la red local.

-Comprobar el ping entre las máquinas y 8.8.8.8:

Ejecutar el comando ping desde cada máquina virtual para verificar la conectividad a Internet al intentar 
comunicarse con la dirección IP 8.8.8.8 (servidores de Google). Para verificar si las máquinas pueden enviar 
paquetes a través de la red.

-Realizar un escaneo de servicios en la red:
Se utiliza el comando nmap para realizar un escaneo de servicios en la red local o en una máquina específica. 
El objetivo es identificar qué servicios están ejecutándose en las máquinas, sus versiones, los protocolos 
utilizados, los puertos abiertos y su disponibilidad.

-Comando msfconsole:
msfconsole es la interfaz de línea de comandos de Metasploit.

-Búsqueda de un módulo específico:
Usamos el comando search para buscar un módulo relacionado con la autenticación en el servicio Tomcat.

-Selección de un módulo y configuración de opciones:
Comando "use" se utiliza para seleccionar un módulo específico después de encontrarlo. 
Luego, se utiliza show options para ver las opciones disponibles y configurarlas según sea necesario. 
En este caso, se centra en las opciones RHOSTS (la máquina objetivo) y RPORT (el puerto en el que se encuentra 
el servicio Tomcat).

Configuración de parámetros y ejecución:
Se establecen los valores de RHOSTS, user_as_pass, y username utilizando los comandos set. Luego, se ejecuta el 
módulo con el comando run. Este proceso intenta realizar una autenticación en el servicio Tomcat utilizando el 
nombre de usuario "tomcat" como contraseña.