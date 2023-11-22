# UNIDAD 3

Autor: Damián Martín Carrasco

## Actividad 1.- Búsqueda de Información

## Actividad 2.- Configuración de Contraseñas Seguras en Windows y Linux

### <p align="center">**Windows Server**</p>

Una vez que estemos dentro de un Windows Server, tendremos que abrir el editor de directivas de seguridad local.

Para ello:

- Abrimos un cuadro de diálogo presionando las teclas `Win + R`

- Ahora escribimos `secpol.msc` y presionamos Enter.

<p align="center">
  <img src="img/U3/A2_WS_1.png" alt="Ejecutar secpol.msc" width="223" height="133">
</p>

A continuación nos dirigimos hacia **"Directivas de cuenta" --> "Directivas de contraseñas"**

Nos aparecerán las directivas y podemos cambiar cualquiera de ellas que queramos, en este ejemplo se puede ver que se cambian tres directivas.

<p align="center">
  <img src="img/U3/A2_WS_2.png" alt="Windows Server directivas" width="471" height="373">
</p>

Aquí una breve explicación de que hace cada una de las directivas:

1. **Almacenamiento de Contraseñas con Cifrado Reversible:**
   - **Función:** Determina si las contraseñas de las cuentas de usuario se almacenan utilizando un cifrado reversible. El cifrado reversible permite recuperar la contraseña original, lo cual es menos seguro.
   - **Configuración:** Se debe configurar como "Deshabilitado" para mejorar la seguridad, ya que el almacenamiento reversible de contraseñas presenta riesgos de seguridad significativos.

2. **Auditoría de Longitud Mínima de Contraseña:**
   - **Función:** Permite auditar eventos relacionados con la longitud mínima de las contraseñas.
   - **Configuración:** Se refiere a la longitud mínima que deben tener las contraseñas. La auditoría puede ayudar a detectar intentos de violación de políticas de contraseñas.

3. **Exigir Historial de Contraseñas:**
   - **Función:** Especifica el número de contraseñas anteriores que deben ser recordadas antes de permitir que un usuario pueda reutilizar una contraseña anterior.
   - **Configuración:** Al exigir un historial de contraseñas, se evita que los usuarios cambien a una contraseña anterior para eludir las políticas de seguridad.

4. **Requisitos de Complejidad de Contraseñas:**
   - **Función:** Obliga a que las contraseñas cumplan con ciertos requisitos de complejidad, como incluir caracteres especiales, números y letras mayúsculas y minúsculas.
   - **Configuración:** Mejora la seguridad al hacer que las contraseñas sean más difíciles de adivinar o de atacar mediante fuerza bruta.

5. **Longitud Mínima de la Contraseña:**
   - **Función:** Especifica la longitud mínima que deben tener las contraseñas.
   - **Configuración:** Establece un estándar mínimo para la longitud de las contraseñas, lo que contribuye a hacerlas más seguras al aumentar la complejidad.

6. **Longitud Máxima de la Contraseña:**
   - **Función:** Limita la longitud máxima que pueden tener las contraseñas.
   - **Configuración:** Aunque es menos común, puede haber situaciones en las que se quiera establecer un límite máximo para evitar abusos o errores.

7. **Vigencia Mínima de la Contraseña:**
   - **Función:** Establece el tiempo mínimo que una contraseña debe estar en uso antes de que el usuario pueda cambiarla.
   - **Configuración:** Ayuda a prevenir cambios frecuentes de contraseñas, lo que podría ser una práctica insegura si se hace con demasiada frecuencia.


Sabiendo esto, podemos cambiar las directivas que queramos adecuándolas a nuestras necesidades.

Después de hacer los cambios podemos cerrar la pestaña, abrimos una consola (cmd) y a continuación ejecutamos el siguiente comando:

```cmd
gpupdate /force
```

Tras esto, ya habremos terminado la configuración básica en las directivas de contraseñas de Windows Server.

<p align="center">
  <img src="img/U3/A2_WS_3.png" alt="cmd gpupdate" width="440" height="219">
</p>

### <p align="center">**Ubuntu Server**</p>


## Actividad 3- Ataques contra contraseñas en Sistemas Windows – FICHERO SAM -

## Actividad 4- Ataques contra contraseñas en Sistemas Windows

## Actividad 5.- Ataques contra contraseñas en Sistemas Linux

## Actividad 6.- Realiza un listado de este tipo de herramientas y analiza la instalación y configuración de 2 congeladores

## Actividad 7: GRUB.

### a) Protege con contraseña el GRUB, para que no se pueda ejecutar secuencia de comandos, como root, en el arranque.

### b) Protege contraseña el arranque de los sistemas operativos.

## Actividad 8: Servidor Radius. Autenticación en redes inalámbricas.

### a) Instala y configura un servidor freeradius con soporte LDAP.

### b) Protege con credenciales de usuario una red inalámbrica, creada con un router Mikrotik.
