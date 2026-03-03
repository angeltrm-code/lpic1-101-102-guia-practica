# Simulacro de Examen LPIC-1 (101)

Este simulacro contiene 25 preguntas de opción múltiple representativas del examen 101, más 3 mini-casos prácticos al final. Trata de contestarlo sin apoyos. Las soluciones están al final del documento.

## Preguntas (1 a 25)

**1. ¿Qué directorio del sistema contiene archivos de dispositivo especiales que representan componentes de hardware?**
A. `/sys`
B. `/proc`
C. `/dev`
D. `/media`

**2. ¿Qué comando usarías para ver los módulos del kernel actualmente cargados en memoria?**
A. `lsmod`
B. `modinfo`
C. `insmod`
D. `showmod`

**3. En un sistema con Systemd, ¿qué comando muestra los mensajes del buffer circular (ring buffer) del kernel generados durante el último arranque?**
A. `dmesg`
B. `journalctl -k -b`
C. Ambas A y B son correctas
D. `tail /var/log/kernel.log`

**4. ¿Qué archivo clásico (en sistemas basados en SysVinit) define el nivel de ejecución (runlevel) por defecto del sistema?**
A. `/etc/runlevel`
B. `/etc/inittab`
C. `/etc/rc.local`
D. `/boot/grub/grub.cfg`

**5. Si necesitas apagar el sistema inmediatamente y cancelar cualquier apagado programado, ¿qué comando(s) es válido?**
A. `shutdown -c`
B. `shutdown -h now`
C. `poweroff`
D. B y C son correctas

**6. ¿Qué comando te permite ver el esquema de particionado y el punto de montaje actual de los discos y dispositivos de bloque?**
A. `blkid`
B. `lsblk`
C. `fdisk -l`
D. `mount -l`

**7. Estás configurando el arranque del sistema. Necesitas actualizar el gestor de arranque GRUB2 después de editar su archivo de configuración `/etc/default/grub`. ¿Qué comando usas normalmente en un sistema derivado de Debian?**
A. `grub-mkconfig -o /boot/grub/grub.cfg`
B. `update-grub`
C. Ambas A y B son válidas
D. `grub-install /dev/sda`

**8. En un sistema RPM (Red Hat, CentOS, Fedora), ¿qué comando usarías para instalar el paquete `htop.rpm` y mostrar una barra de progreso de barras almohadilla (`#`) durante la instalación?**
A. `rpm -i htop.rpm`
B. `rpm -ivh htop.rpm`
C. `yum install htop.rpm`
D. `dpkg -i htop.rpm`

**9. En la familia Debian, ¿qué comando actualiza la lista local de paquetes disponibles desde los repositorios configurados?**
A. `apt-get upgrade`
B. `apt-cache update`
C. `apt update` (o `apt-get update`)
D. `dpkg --update`

**10. Quieres encontrar bibliotecas compartidas instaladas en rutas estándar. ¿Qué comando actualiza la caché (almacenada en `/etc/ld.so.cache`) que usa el sistema para localizarlas?**
A. `ldconfig`
B. `ldd`
C. `update-alternatives`
D. `makelibs`

**11. Estás en la terminal bash. Escribes `ls /etc` y ves la lista de archivos. ¿Cómo puedes ejecutar rápidamente ese mismo comando anterior entero desde el historial de bash?**
A. `!ls`
B. `!!`
C. `Ctrl + P` y enter
D. Todas las anteriores cumplen el propósito general o literal

**12. ¿Qué línea en el archivo `~/.bashrc` crea un alias persistente llamado `ll` para el comando `ls -la`?**
A. `alias ll='ls -la'`
B. `alias 'ls -la' = ll`
C. `export ll='ls -la'`
D. `set alias ll 'ls -la'`

**13. Quieres guardar la salida normal de un comando `find` en `ok.txt` y los errores (como "Permiso denegado") en `errores.txt`. ¿Qué sintaxis es correcta?**
A. `find / -name "*.conf" > ok.txt &> errores.txt`
B. `find / -name "*.conf" 1> ok.txt 2> errores.txt`
C. `find / -name "*.conf" >> ok.txt > errores.txt`
D. `find / -name "*.conf" > ok.txt 1>&2 errores.txt`

**14. ¿Qué comando permite extraer el tercer campo (delimitado por `:`) del archivo `/etc/passwd`?**
A. `cut -d: -f3 /etc/passwd`
B. `awk -F':' '{print $3}' /etc/passwd`
C. Ambas A y B son correctas
D. Ninguna de las anteriores

**15. Usando expresiones regulares convencionales con `grep`, ¿qué patrón encuentra las líneas que terminan en la letra "Z"?**
A. `^Z`
B. `Z$`
C. `*Z`
D. `\Z`

**16. Quieres reemplazar todas las apariciones de `foo` por `bar` en el archivo `test.txt` y mostrar el resultado en pantalla sin modificar el archivo original. ¿Qué comando usarías?**
A. `sed 's/foo/bar/g' test.txt`
B. `sed -i 's/foo/bar/g' test.txt`
C. `awk -replace 'foo' 'bar' test.txt`
D. `tr 'foo' 'bar' < test.txt`

**17. Al editar un archivo con `vi`, ¿qué tecla pulsa el usuario para salir del "modo inserción" y volver al "modo comando" (o normal)?**
A. `Enter`
B. `i`
C. `Esc`
D. `Ctrl + C`

**18. En `vi` o `vim`, ¿cómo guardas los cambios y sales del editor desde el modo normal?**
A. `:wq`
B. `:x`
C. `ZZ` (mayúsculas)
D. Todas las anteriores son válidas

**19. Tienes el permiso octal `754` en un directorio. ¿Qué puede hacer el grupo propietario?**
A. Leer, escribir y ejecutar
B. Leer y ejecutar, pero no escribir
C. Solo leer
D. Solo ejecutar

**20. ¿Qué comando cambia el usuario propietario del archivo `reporte.txt` al usuario `ana` y el grupo propietario al grupo `ventas` de forma simultánea?**
A. `chown ana:ventas reporte.txt`
B. `chmod ana:ventas reporte.txt`
C. `chgrp ana.ventas reporte.txt`
D. `usermod -o ana -g ventas reporte.txt`

**21. ¿Qué flag de `chmod` activa el bit SGID (Set-Group-ID) en un directorio?**
A. `chmod +t`
B. `chmod g+s`
C. `chmod u+s`
D. `chmod o+x`

**22. Creas un enlace simbólico (soft link) y borras el archivo destino original. ¿Qué ocurre con el enlace simbólico?**
A. Se elimina automáticamente
B. Se convierte en un archivo regular vacío
C. Apunta a la nada (enlace roto o "dangling link")
D. Restaura el archivo si lo abres

**23. ¿Cuál es el formato predeterminado del archivo resultante cuando usas `tar` para empaquetar una carpeta sin indicar banderas de compresión como `-z` o `-j`?**
A. Un archivo comprimido en gzip (`.tar.gz`)
B. Un archivo de texto sin formato
C. Un archivo binario no comprimido que agrupa el árbol de directorios
D. Un archivo comprimido bzip2

**24. ¿En qué directorio se guardan tradicionalmente los binarios esenciales estáticos y dinámicos que deben estar disponibles para que el sistema arranque y actúe como rescate, para todos los usuarios?**
A. `/usr/bin`
B. `/sbin`
C. `/bin`
D. `/opt`

**25. ¿Qué comando te muestra dónde se encuentra el binario ejecutable de `ls`, junto con su archivo fuente y la página de manual, si están disponibles?**
A. `whereis ls`
B. `which ls`
C. `locate ls`
D. `find / -name ls`

---

## Mini-casos prácticos

**Caso 1 (Redirección y Procesos):**  
Acabas de escribir un gran guion en shell (`/usr/local/bin/backup.sh`) que va a tardar horas en procesar. Quieres ejecutarlo, mandarlo a segundo plano para poder cerrar la terminal y que no se muera el proceso, y redirigir toda su salida estandar y de error a un archivo log `/var/log/backup_manual.log`.  
*Respuesta (comando completo):* _________________________________________________

**Caso 2 (Gestión de paquetes):**  
Trabajas en un servidor Ubuntu (Debian-based). Quieres ver qué archivos pertenecen al paquete ya instalado llamado `nginx`.  
*Respuesta (comando completo):* _________________________________________________

**Caso 3 (Búsqueda):**  
Necesitas buscar todos los archivos dentro del directorio `/etc` que pesen más de 10 Megabytes y mostrar sus detalles.  
*Respuesta (comando):* _________________________________________________

---
---

## Soluciones Simulacro 101

**Respuestas Test Puntuado (1 punto cada una)**
1. **C** (`/dev` almacena los devices).
2. **A** (`lsmod` la lista; `modinfo` da información detallada de uno; `insmod` lo carga).
3. **C** (Ambos leen del buffer. `dmesg` es tradicional, `journalctl -k` es la forma systemd).
4. **B** (`/etc/inittab` contiene `id:3:initdefault:` en SysV).
5. **D** (Ambos `shutdown -h now` y `poweroff` cierran el sistema en el acto).
6. **B** (`lsblk` muestra la estructura de bloques en forma de árbol con montajes).
7. **C** (`update-grub` es un script envoltorio de `grub-mkconfig` muy popular en Debian/Ubuntu).
8. **B** (`-i` instala, `-v` verboso, `-h` muestra marcas hash).
9. **C** (`update` descarga la info de los repos, no instala nada. `upgrade` actualiza binarios).
10. **A** (`ldconfig` reconstruye `/etc/ld.so.cache`).
11. **D** (`!!` o usar las flechas / bash history funcionan; `!ls` ejecuta el último comando que empezó por ls).
12. **A** (Esa es la sintaxis correcta bash).
13. **B** (Descriptor 1 a ok.txt, 2 a errores.txt. C es append. D rompe la sintaxis).
14. **C** (Ambas herramientas de procesamiento sirven para extraer campos por delimitador).
15. **B** (`$` ancla el patrón al final de la línea).
16. **A** (Sin `-i` los cambios salen por stdout; con `-i` altera el archivo).
17. **C** (`Esc` vuelve al modo comando normal).
18. **D** (Las tres formas guardan cambios y salen exitosamente).
19. **B** (Octal 5 equivale a lectura=4 + ejecución=1).
20. **A** (Sintaxis estándar `usuario:grupo`).
21. **B** (`g+s` pone la 's' en el set del grupo).
22. **C** (El inodo original se pierde. El enlace se queda apuntando a un path vacío).
23. **C** (Sin `-z`, `-j` o `-J`, `tar` solo une, no comprime).
24. **C** (`/bin` aloja los comandos base para todos. `/sbin` es de superusuario. En FHS modernos a veces apuntan a `/usr/bin`).
25. **A** (`whereis` busca binario, manual y fuentes en rutas hardcodeadas. `which` solo busca el binario).

**Soluciones sugeridas Mini-casos (1 punto cada uno)**
* C1: `nohup /usr/local/bin/backup.sh > /var/log/backup_manual.log 2>&1 &` (o similar que use `nohup` y `&`).
* C2: `dpkg -L nginx` (La bandera `-L` lista los ficheros instalados por un paquete).
* C3: `find /etc -size +10M -ls` (o `find /etc -type f -size +10M -exec ls -lh {} \;` o equivalentes funcionales).
