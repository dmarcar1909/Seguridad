# Actividades Unidad 4 Seguridad - Criptografía

Autor: Damián Martín Carrasco

## Parte 1.- CIFRADO SIMÉTRICO GPG

### 1. Crea un documento de texto con cualquier editor o utiliza uno del que dispongas.

Simplemente creamos un documento de texto mediante el uso de echo y lo volcamos en el fichero que vamos a crear.

```bash
echo "damian" > fichero.txt
```

### 2. Cifra este documento con alguna contraseña acordada con el compañero de al lado.

Ahora ciframos el fichero que acabamos de crear.

**gpg -c fichero.txt**

```
gpg: Comando principal de GnuPG, que se utiliza para cifrar y firmar digitalmente datos.

-c: Esta opción le indica a GnuPG que debe realizar una operación de cifrado simétrico,
lo que significa que se utiliza la misma clave para cifrar y descifrar el archivo.
```

Nos pedirá una contraseña de cifrado.

<p align="center">
  <img src="img/U4/pdf1_1.png">
</p>

### 3. Haz llegar por algún medio al compañero de al lado el documento que acabas de cifrar.

He usado scp para enviar el archivo, para ello tenemos que tener instalado previamente openssh-server desde la máquina servidora y openssh-cliente desde la máquina cliente.

Una vez están instalados los paquetes, usando el comando scp se pasa por ssh el documento al cliente y comprobamos que le ha llegado satisfactoriamente.

<p align="center">
  <img src="img/U4/pdf1_2.png">
</p>

### 4. Descifra el documento que te ha hecho llegar tu compañero de al lado.

Ahora en la máquina cliente desciframos el archivo que hemos pasado desde la otra máquina, para ello usamos gpg --decrypt, en este caso solo puse gpg, que como podemos ver adivinará que queremos descrifrar.

<p align="center">
  <img src="img/U4/pdf1_3.png">
</p>

### 5. ¿Con qué algoritmo se ha cifrado el fichero? Vuelve a cifrar el fichero usando el algoritmo AES256. ¿Puedes hacer permanente esta configuración?

Para ver el algoritmo con el que se ha cifrado el fichero podemos hacer uso de file.

```bash
file fichero.txt.gpg
```

Nos aparecerá el algoritmo, en este caso, AES256.

<p align="center">
  <img src="img/U4/pdf1_4.png">
</p>

Para hacer permanente este cambio podemos usar el siguiente comando.

```bash
gpg --cipher-algo AES256 -c fichero.txt
```

En el caso que muestra la captura, estamos diciéndole que encripte el fichero usando específicamente ese algoritmo.

Además podemos editar o crear el archivo de configuración donde declaramos que por defecto se use ese algoritmo.

<p align="center">
  <img src="img/U4/pdf1_5.png">
</p>

### 6. Instala gpg en windows (Gpg4win), repite el ejercicio en Windows. Puedes encriptar un mensaje en linux y desencriptarlo en windows y al contrario.

Tenemos que descargar Gpg4win y una vez lo tengamos instalado abrimos Kleopatra, que deberíamos haber seleccionado durante la instalación.

Lo primero que tenemos que hacer es generar un certificado, y una vez lo tenemos le damos a Firmar/Cifrar, luego deshabilitamos la casilla de firmar como, eso es algo que veremos más tarde.

Le damos a cifrar para mi y ponemos el certificado que hemos generado antes, marcamos la casilla de cifrar con contraseña y abajo seleccionamos el archivo a cifrar, por último le damos a "Cifrar".

<p align="center">
  <img src="img/U4/pdf1_6.png">
</p>

Le ponemos la contraseña que queramos.

<p align="center">
  <img src="img/U4/pdf1_7.png">
</p>

Y vemos que el archivo se ha cifrado correctamente.

<p align="center">
  <img src="img/U4/pdf1_8.png">
</p>

Para pasar los archivos a la máquina de Linux me descargué e instalé winSCP que es fácil de usar.

Una vez te conectas al usuario de la máquina de Linux sale una interfaz donde puedes ver los directorios y archivos de Windows a un lado (izquierda) y de Ubuntu al otro (derecha), basta con arrastrar el archivo que quieres pasar de un lado al otro.

En este caso pasé de Windows10 un archivo a Ubuntu y viceversa.

<p align="center">
  <img src="img/U4/pdf1_9.png">
</p>

Primero desciframos el que le hemos pasado a Ubuntu, para ello usamos el comando `gpg --decrypt`.

Como podemos ver se ha descifrado bien y ahora es legible.

<p align="center">
  <img src="img/U4/pdf1_10.png">
</p>

En Windows10 simplemente tenemos que abrir Kleopatra y darle a Descifrar/Verificar y seleccionar el archivo, cuando le demos podemos ver que se descifra correctamente.

<p align="center">
  <img src="img/U4/pdf1_11.png">
</p>

Lo abrimos y comprobamos que se conservan sus contenidos.

<p align="center">
  <img src="img/U4/pdf1_12.png">
</p>

### 7. openssl es otra herramienta que nos permite cifrar mensajes de forma simétrica, investiga como se realiza este ejercicio utilizando esta herramienta.

En primer lugar ejecuramos el siguiente comando y comprobamos que se ha creado con éxito.

<p align="center">
  <img src="img/U4/pdf1_13.png">
</p>

```
enc: Se utiliza para realizar operaciones de cifrado y descifrado.

-aes-256-cbc: Esta opción especifica el algoritmo de cifrado y el modo de operación. En este caso, se está utilizando AES con una clave de 256 bits en modo CBC (Cipher Block Chaining).

-in ejer7damian.txt: Indica el nombre del archivo de entrada que se va a cifrar. En este caso, el archivo de entrada se llama "ejer7damian.txt".

-out ejer7damian.enc: Indica el nombre del archivo de salida cifrado. En este ejemplo, el archivo cifrado se llamará "ejer7damian.enc".
```

Pasamos el archivo usando scp de nuevo.

Ahora abrimos el Prompt de OpenSSL en Windows10 (lo hemos tenido que descargar e instalar previamente).

Una vez dentro nos vamos hasta donde está el archivo, y una vez allí lanzamos el siguiente comando

```cmd
openssl enc -d -aes-256-cbc -in ejer7damian.enc -out ejer7damian.txt
```

*Aquí están los mismos parámetros que en el de encriptado, con la diferencia que se usa -d para desencriptar*

Y luego lo abrimos y comprobamos que se ha realizado exitosamente.

<p align="center">
  <img src="img/U4/pdf1_14.png">
</p>

De esta manera se podría realizar usando openssl.

## Parte 2.- FIRMA DIGITAL CON GPG

### 1. Selecciona un documento pdf y encríptalo y fírmalo (opción --sign). Envíalo a un compañero, que debe en primer lugar verificar la firma y posteriormente descifrar el documento.

En el Windows10 podemos realizar el encriptado y firma seleccionando las dos casillas y poniéndole una contraseña.

<p align="center">
  <img src="img/U4/pdf2_1.png">
</p>

Vemos que se ha cifrado y firmado correctamente.

<p align="center">
  <img src="img/U4/pdf2_2.png">
</p>

Ahora en el Ubuntu creamos un nuevo fichero para usarlo, tendremos que generar la clave ahora o no podremos firmarlo tal y como se ve en la imagen, así que generamos una clave con `gpg --gen-key`.

<p align="center">
  <img src="img/U4/pdf2_3.png">
</p>

Aquí podemos comprobar el resto de la imagen de como se crea el par de claves.

<p align="center">
  <img src="img/U4/pdf2_4.png">
</p>

Ahora lo firmamos usando el --sign.

Para ello usamos el siguiente comando.

```bash
gpg --output pdf2_ubuntu_damian.txt.gpg --sign pdf2_ubuntu_damian.txt
```

Nos dirá que ya hay un archivo con ese nombre, por lo que podemos sobreescribirlo o darle otro nombre, en este caso le damos otro nombre.

<p align="center">
  <img src="img/U4/pdf2_5.png">
</p>

Usamos la verificación para comprobar que se ha realizado correctamente la firma.

Ahora vamos a exportar el par de claves usando gpg --export

```bash
gpg --export --armor damimc21@gmail.com > clave_publica.asc
```

Y lo enviamos a la otra máquina con scp de nuevo.

<p align="center">
  <img src="img/U4/pdf2_6.png">
</p>

Ahora en la máquina a la que le hemos pasado el par de claves, añadimos el par de claves al llavero, usando gpg --import

```bash
gpg --import clave_publica.asc
```

Y vemos que se importa correctamente

<p align="center">
  <img src="img/U4/pdf2_7.png">
</p>

Ahora desencriptamos, también podemos usar --verify, y nos sale la firma correcta, podemos ver que el fichero tiene su contenido.

<p align="center">
  <img src="img/U4/pdf2_8.png">
</p>

### 2. Realiza el mismo ejercicio pero obteniendo una firma ASCII.

Ya se realizó en el ejercicio anterior usando --armor.

<p align="center">
  <img src="img/U4/pdf2_6.png">
</p>

### 3. Ahora sólo queremos firmar un documento. Firma un documento (opción --detach-sign). A continuación envía el documento original y la firma a un compañero para que verifique que el documento está firmado por tí.

Creamos un nuevo fichero y lo firmamos con --detach-sign.

<p align="center">
  <img src="img/U4/pdf2_9.png">
</p>

Pasamos el archivo a la otra máquina, y verificamos aquí que está firmado.

<p align="center">
  <img src="img/U4/pdf2_10.png">
</p>
