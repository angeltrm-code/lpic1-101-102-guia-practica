# 03 — Matriz objetivo → comandos (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.
> Conecta cada **objetivo oficial** con los **comandos, archivos y utilidades** que debes reconocer o practicar.

## Cómo leer esta matriz

- **Oficiales (LPI):** comandos, archivos, utilidades o conceptos citados en la página oficial de objetivos.
- **Asociados para practicar:** solo aparecen cuando el objetivo es muy conceptual o la web no lista comandos visibles en el fragmento recuperado.
- **Prioridad:** corresponde a la importancia publicada por LPI para ese objetivo.

---

# EXAMEN 101

## Tema 101: Arquitectura del sistema

### 101.1 Determinar y configurar los ajustes de hardware
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Identificar el hardware fundamental del sistema.
- Activar o desactivar periféricos integrados.
- Distinguir tipos de almacenamiento masivo.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/sys/`
- `/proc/`
- `/dev/`
- `modprobe`
- `lsmod`
- `lspci`
- `lsusb`


### 101.2 Arranque del sistema
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Comprender la secuencia de arranque desde BIOS/UEFI hasta `init`.
- Diferenciar `SysVinit`, `systemd` y conocer `Upstart`.
- Entender el papel del bootloader, el kernel y `initramfs`.

**Comandos, archivos y utilidades oficiales (LPI)**
- `dmesg`
- `journalctl`
- `BIOS`
- `UEFI`
- `bootloader`
- `kernel`
- `initramfs`
- `init`
- `SysVinit`
- `systemd`


### 101.3 Cambiar niveles de ejecución / objetivos de arranque y apagar o reiniciar el sistema
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Cambiar entre niveles de ejecución y objetivos de arranque.
- Usar modo monousuario cuando sea necesario.
- Apagar y reiniciar desde terminal.

**Comandos, archivos y utilidades oficiales (LPI)**
- `systemctl`
- `shutdown`
- `reboot`
- `halt`
- `poweroff`
- `acpid`


---

## Tema 102: Instalación de Linux y gestión de paquetes

### 102.1 Diseño del esquema de particionado del disco duro
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Diseñar particiones según el uso del sistema.
- Separar `/`, `/var`, `/home`, `/boot`, swap y ESP cuando convenga.
- Entender puntos de montaje y LVM a nivel básico.

**Comandos, archivos y utilidades oficiales (LPI)**
- No se mostraban comandos explícitos en la parte recuperada de la web oficial para este objetivo.

**Comandos asociados para practicar**
- `fdisk`
- `gdisk`
- `parted`
- `lsblk`
- `blkid`
- `mount`
- `umount`


### 102.2 Instalar un gestor de arranque
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Instalar y configurar un gestor de arranque.
- Entender GRUB Legacy y GRUB 2.
- Conocer ubicaciones alternativas y opciones de rescate.

**Comandos, archivos y utilidades oficiales (LPI)**
- `menu.lst`
- `grub.cfg`
- `grub.conf`
- `grub-install`
- `grub-mkconfig`
- `MBR`


### 102.3 Gestión de librerías compartidas
**Prioridad LPI:** 1

**Qué conecta este objetivo**
- Identificar dependencias de librerías compartidas.
- Conocer ubicaciones habituales de librerías del sistema.
- Entender cómo se cargan.

**Comandos, archivos y utilidades oficiales (LPI)**
- `ldd`
- `ldconfig`
- `/etc/ld.so.conf`
- `LD_LIBRARY_PATH`


### 102.4 Gestión de paquetes Debian
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Instalar, actualizar y desinstalar paquetes Debian.
- Buscar paquetes por archivo o librería.
- Consultar versión, contenido, dependencias e integridad.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/apt/sources.list`
- `dpkg`
- `dpkg-reconfigure`
- `apt-get`
- `apt-cache`


### 102.5 Gestión de paquetes RPM y YUM
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Instalar, reinstalar, actualizar y eliminar paquetes con RPM/YUM/Zypper.
- Consultar versión, estado, dependencias, integridad y firmas.
- Saber qué archivos aporta un paquete y de qué paquete proviene un archivo.

**Comandos, archivos y utilidades oficiales (LPI)**
- `rpm`
- `rpm2cpio`
- `/etc/yum.conf`
- `/etc/yum.repos.d/`
- `yum`
- `zypper`


### 102.6 Linux como sistema virtualizado
**Prioridad LPI:** 1

**Qué conecta este objetivo**
- Diferenciar máquina virtual, contenedor Linux y contenedor de aplicación.
- Entender elementos comunes de entornos IaaS.
- Saber qué cambia al clonar una máquina o usarla como plantilla.

**Comandos, archivos y utilidades oficiales (LPI)**
- No se mostraban comandos explícitos en la parte recuperada de la web oficial para este objetivo.

**Comandos asociados para practicar**
- `systemd-detect-virt`
- `uname`
- `lsmod`
- `ip`
- `free`
- `lscpu`


---

## Tema 103: Comandos GNU y Unix

### 103.1 Trabajar desde la línea de comandos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Usar la shell Bash para tareas básicas.
- Definir, consultar, exportar y eliminar variables de entorno.
- Usar el historial de comandos.

**Comandos, archivos y utilidades oficiales (LPI)**
- `bash`
- `echo`
- `env`
- `export`
- `pwd`
- `set`
- `unset`
- `type`
- `which`
- `man`
- `uname`
- `history`
- `.bash_history`
- `uso de comillas`


### 103.2 Procesar secuencias de texto usando filtros
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Aplicar filtros a flujos y archivos de texto.
- Usar utilidades clásicas GNU/Unix para transformar salida.

**Comandos, archivos y utilidades oficiales (LPI)**
- `bzcat`
- `cat`
- `cut`
- `head`
- `less`
- `md5sum`
- `nl`
- `od`
- `paste`
- `sed`
- `sha256sum`
- `sha512sum`
- `sort`
- `split`
- `tail`
- `tr`
- `uniq`
- `wc`
- `xzcat`
- `zcat`


### 103.3 Administración básica de archivos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Copiar, mover, eliminar y crear archivos/directorios.
- Trabajar con copias recursivas.
- Usar comodines simples y avanzados.

**Comandos, archivos y utilidades oficiales (LPI)**
- `cp`
- `find`
- `mkdir`
- `mv`
- `ls`
- `rm`
- `rmdir`
- `touch`
- `tar`
- `cpio`
- `dd`
- `file`
- `gzip`
- `gunzip`
- `bzip2`
- `bunzip2`
- `xz`
- `unxz`
- `uso de comodines (*file globbing*)`


### 103.4 Uso de secuencias de texto, tuberías y redireccionamientos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Redireccionar `stdin`, `stdout` y `stderr`.
- Encadenar comandos con tuberías.
- Usar la salida de un comando como entrada o argumento de otro.

**Comandos, archivos y utilidades oficiales (LPI)**
- `tee`
- `xargs`


### 103.5 Crear, supervisar y matar procesos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Ejecutar trabajos en primer y segundo plano.
- Supervisar procesos activos.
- Seleccionar y ordenar procesos.

**Comandos, archivos y utilidades oficiales (LPI)**
- `&`
- `bg`
- `fg`
- `jobs`
- `kill`
- `nohup`
- `ps`
- `top`
- `free`
- `uptime`
- `pgrep`
- `pkill`
- `killall`
- `watch`
- `screen`
- `tmux`


### 103.6 Modificar la prioridad de ejecución de los procesos
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Conocer la prioridad por defecto de un proceso.
- Lanzar procesos con prioridad distinta.
- Modificar la prioridad de procesos ya en ejecución.

**Comandos, archivos y utilidades oficiales (LPI)**
- `nice`
- `ps`
- `renice`
- `top`


### 103.7 Realizar búsquedas en archivos de texto usando expresiones regulares
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Crear expresiones regulares simples.
- Diferenciar BRE y ERE.
- Entender clases, cuantificadores, anclas y caracteres especiales.

**Comandos, archivos y utilidades oficiales (LPI)**
- `grep`
- `egrep`
- `fgrep`
- `sed`
- `regex(7)`


### 103.8 Edición básica de archivos
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Navegar y editar en `vi`.
- Diferenciar modos.
- Insertar, borrar, copiar, pegar y buscar texto.

**Comandos, archivos y utilidades oficiales (LPI)**
- `vi`
- `/`
- `?`
- `h`
- `j`
- `k`
- `l`
- `i`
- `o`
- `a`
- `d`
- `p`
- `y`
- `dd`
- `yy`
- `ZZ`
- `:w!`
- `:q!`
- `EDITOR`


---

## Tema 104: Dispositivos, sistemas de archivos Linux y FHS

### 104.1 Creación de particiones y sistemas de archivos
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Administrar tablas de particiones MBR y GPT.
- Crear sistemas de archivos con `mkfs`.
- Manejar swap.

**Comandos, archivos y utilidades oficiales (LPI)**
- `fdisk`
- `gdisk`
- `parted`
- `mkfs`
- `mkswap`


### 104.2 Mantener la integridad de los sistemas de archivos
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Verificar integridad.
- Supervisar espacio libre e inodos.
- Resolver fallos básicos de filesystem.

**Comandos, archivos y utilidades oficiales (LPI)**
- `du`
- `df`
- `fsck`
- `e2fsck`
- `mke2fs`
- `tune2fs`
- `xfs_repair`
- `xfs_fsr`
- `xfs_db`


### 104.3 Controlar el montaje y desmontaje de los sistemas de archivos
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Montar y desmontar manualmente.
- Configurar montaje en arranque.
- Usar UUIDs y etiquetas.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/fstab`
- `/media/`
- `mount`
- `umount`
- `blkid`
- `lsblk`


### 104.4 Eliminado
**Prioridad LPI:** ?

**Qué conecta este objetivo**
- Revisar el objetivo completo en el documento de objetivos desarrollados.

**Comandos, archivos y utilidades oficiales (LPI)**
- No se mostraban comandos explícitos en la parte recuperada de la web oficial para este objetivo.

**Comandos asociados para practicar**
- `rm`
- `shred`
- `wipefs`


### 104.5 Administración de permisos y propietarios de los archivos
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Administrar permisos en archivos y directorios.
- Usar `suid`, `sgid` y `sticky bit`.
- Controlar la máscara de creación (`umask`).

**Comandos, archivos y utilidades oficiales (LPI)**
- `chmod`
- `umask`
- `chown`
- `chgrp`


### 104.6 Crear y cambiar enlaces duros y simbólicos
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Crear enlaces duros y simbólicos.
- Identificarlos.
- Entender diferencias entre copiar y enlazar.

**Comandos, archivos y utilidades oficiales (LPI)**
- `ln`
- `ls`


### 104.7 Encontrar archivos de sistema y ubicarlos en el lugar correspondiente
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Entender el FHS.
- Conocer ubicaciones típicas de archivos y comandos.
- Localizar binarios, configuraciones y datos.

**Comandos, archivos y utilidades oficiales (LPI)**
- `find`
- `locate`
- `updatedb`
- `whereis`
- `which`
- `type`
- `/etc/updatedb.conf`


---

# EXAMEN 102

## Tema 105: Shells y scripts

### 105.1 Personalizar y usar el entorno de shell
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Configurar variables de entorno al iniciar sesión o al abrir una shell.
- Escribir funciones Bash para tareas repetidas.
- Ajustar el `PATH` correctamente.

**Comandos, archivos y utilidades oficiales (LPI)**
- `.`
- `source`
- `/etc/bash.bashrc`
- `/etc/profile`
- `env`
- `export`
- `set`
- `unset`
- `~/.bash_profile`
- `~/.bash_login`
- `~/.profile`
- `~/.bashrc`
- `~/.bash_logout`
- `function`
- `alias`


### 105.2 Personalización y escritura de scripts sencillos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Usar sintaxis `sh` básica: bucles y condicionales.
- Sustitución de comandos.
- Interpretar códigos de retorno.

**Comandos, archivos y utilidades oficiales (LPI)**
- `for`
- `while`
- `test`
- `if`
- `read`
- `seq`
- `exec`
- `||`
- `&&`


---

## Tema 106: Interfaces de usuario y escritorios

### 106.1 Instalar y configurar X11
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Estructura básica de configuración de X11.
- Autorización y acceso a pantalla.
- Variables y errores de sesión.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/X11/xorg.conf`
- `/etc/X11/xorg.conf.d/`
- `~/.xsession-errors`
- `xhost`
- `xauth`
- `DISPLAY`
- `X`


### 106.2 Escritorios gráficos
**Prioridad LPI:** 1

**Qué conecta este objetivo**
- Conocer los principales escritorios Linux.
- Reconocer protocolos de escritorio remoto.

**Comandos, archivos y utilidades oficiales (LPI)**
- No se mostraban comandos explícitos en la parte recuperada de la web oficial para este objetivo.

**Comandos asociados para practicar**
- `xwininfo`
- `xdpyinfo`
- `echo $DISPLAY`
- `systemctl --user`


### 106.3 Accesibilidad
**Prioridad LPI:** 1

**Qué conecta este objetivo**
- Tener conocimiento general de accesibilidad en el escritorio.
- Reconocer ayudas visuales, de entrada y asistencia.
- Temas de escritorio de alto contraste / impresión grande

**Comandos, archivos y utilidades oficiales (LPI)**
- No se mostraban comandos explícitos en la parte recuperada de la web oficial para este objetivo.

**Comandos asociados para practicar**
- `setxkbmap`
- `xev`
- `locale`
- `localectl`


---

## Tema 107: Tareas administrativas

### 107.1 Administrar cuentas de usuario y de grupo y los archivos de sistema relacionados con ellas
**Prioridad LPI:** 5

**Qué conecta este objetivo**
- Añadir, modificar, eliminar y suspender usuarios y grupos.
- Gestionar bases de datos de cuentas.
- Crear cuentas limitadas o de propósito especial.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/passwd`
- `/etc/shadow`
- `/etc/group`
- `/etc/skel/`
- `chage`
- `getent`
- `groupadd`
- `groupdel`
- `groupmod`
- `passwd`
- `useradd`
- `userdel`
- `usermod`


### 107.2 Automatizar tareas administrativas del sistema mediante la programación de trabajos
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Programar trabajos con `cron`.
- Ejecutar tareas puntuales con `at`.
- Entender temporizadores de `systemd`.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/cron.{d,daily,hourly,monthly,weekly}/`
- `/etc/at.deny`
- `/etc/at.allow`
- `/etc/crontab`
- `/etc/cron.allow`
- `/etc/cron.deny`
- `/var/spool/cron/`
- `crontab`
- `at`
- `atq`
- `atrm`
- `systemctl`
- `systemd-run`


### 107.3 Localización e internacionalización
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Configuración regional y de idioma.
- Zona horaria.
- Uso de `LANG=C` en scripting.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/timezone`
- `/etc/localtime`
- `/usr/share/zoneinfo/`
- `LC_*`
- `LC_ALL`
- `LANG`
- `TZ`
- `/usr/bin/locale`
- `tzselect`
- `timedatectl`
- `date`
- `iconv`
- `UTF-8`
- `ISO-8859`
- `ASCII`
- `Unicode`


---

## Tema 108: Servicios esenciales del sistema

### 108.1 Mantener la hora del sistema
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Ajustar fecha y hora del sistema.
- Sincronizar reloj con NTP.
- Entender UTC y reloj hardware.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/usr/share/zoneinfo/`
- `/etc/timezone`
- `/etc/localtime`
- `/etc/ntp.conf`
- `/etc/chrony.conf`
- `date`
- `hwclock`
- `timedatectl`
- `ntpd`
- `ntpdate`
- `chronyc`
- `pool.ntp.org`


### 108.2 Registros del sistema
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Configurar `rsyslog`.
- Entender prioridades, acciones y subsistemas.
- Consultar y filtrar el journal de `systemd`.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/rsyslog.conf`
- `/var/log/`
- `logger`
- `logrotate`
- `/etc/logrotate.conf`
- `/etc/logrotate.d/`
- `journalctl`
- `systemd-cat`
- `/etc/systemd/journald.conf`
- `/var/log/journal/`


### 108.3 Conceptos básicos del Agente de Transferencia de Correo
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Alias y reenvío básico de correo en host cliente.
- Reconocer los MTA más comunes.

**Comandos, archivos y utilidades oficiales (LPI)**
- `~/.forward`
- `*sendmail emulation layer commands*`
- `newaliases`
- `mail`
- `mailq`
- `postfix`
- `sendmail`
- `exim`


### 108.4 Gestión de la impresión y de las impresoras
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Configuración básica de CUPS.
- Gestión de colas de impresión.
- Resolución de problemas.

**Comandos, archivos y utilidades oficiales (LPI)**
- `utilidades, herramientas y archivos de configuración de CUPS`
- `/etc/cups/`
- `interfaz legacy de lpd (lpr, lprm, lpq)`


---

## Tema 109: Fundamentos de redes

### 109.1 Fundamentos de los protocolos de Internet
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Fundamentos TCP/IP.
- Máscaras y CIDR.
- IPv4 vs IPv6.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/services`
- `IPv4`
- `IPv6`
- `Subnetting`
- `TCP`
- `UDP`
- `ICMP`


### 109.2 Configuración de red persistente
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Configurar red persistente en Linux.
- Entender configuración TCP/IP básica.
- Gestionar Ethernet y Wi-Fi con `NetworkManager`.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/hostname`
- `/etc/hosts`
- `/etc/nsswitch.conf`
- `/etc/resolv.conf`
- `nmcli`
- `hostnamectl`
- `ifup`
- `ifdown`


### 109.3 Resolución de problemas básicos de red
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Diagnóstico básico de conectividad.
- Inspección de IP, sockets y rutas.
- Uso de herramientas clásicas y modernas.

**Comandos, archivos y utilidades oficiales (LPI)**
- `ip`
- `hostname`
- `ss`
- `ping`
- `ping6`
- `traceroute`
- `traceroute6`
- `tracepath`
- `tracepath6`
- `netcat`
- `ifconfig`
- `netstat`
- `route`


### 109.4 Configuración DNS en el lado del cliente
**Prioridad LPI:** 2

**Qué conecta este objetivo**
- Consultar DNS remotos.
- Configurar resolución local.
- Cambiar el orden de resolución de nombres.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/hosts`
- `/etc/resolv.conf`
- `/etc/nsswitch.conf`
- `host`
- `dig`
- `getent`


---

## Tema 110: Seguridad

### 110.1 Tareas de administración de seguridad
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Auditar archivos con `suid/sgid`.
- Cambiar contraseñas y caducidad.
- Detectar puertos abiertos.

**Comandos, archivos y utilidades oficiales (LPI)**
- `find`
- `passwd`
- `fuser`
- `lsof`
- `nmap`
- `chage`
- `netstat`
- `sudo`
- `/etc/sudoers`
- `su`
- `usermod`
- `ulimit`
- `who`
- `w`
- `last`


### 110.2 Configuración de la seguridad del sistema
**Prioridad LPI:** 3

**Qué conecta este objetivo**
- Entender *shadow passwords*.
- Desactivar servicios no usados.
- Comprender el papel de TCP Wrappers.

**Comandos, archivos y utilidades oficiales (LPI)**
- `/etc/nologin`
- `/etc/passwd`
- `/etc/shadow`
- `/etc/xinetd.d/`
- `/etc/xinetd.conf`
- `systemd.socket`
- `/etc/inittab`
- `/etc/init.d/`
- `/etc/hosts.allow`
- `/etc/hosts.deny`


### 110.3 Protección de datos mediante cifrado
**Prioridad LPI:** 4

**Qué conecta este objetivo**
- Uso básico del cliente OpenSSH.
- Claves de host y claves de usuario.
- Uso básico de GnuPG.

**Comandos, archivos y utilidades oficiales (LPI)**
- `ssh`
- `ssh-keygen`
- `ssh-agent`
- `ssh-add`
- `~/.ssh/id_rsa y id_rsa.pub`
- `~/.ssh/id_dsa y id_dsa.pub`
- `~/.ssh/id_ecdsa y id_ecdsa.pub`
- `~/.ssh/id_ed25519 y id_ed25519.pub`
- `/etc/ssh/ssh_host_rsa_key y ssh_host_rsa_key.pub`
- `/etc/ssh/ssh_host_dsa_key y ssh_host_dsa_key.pub`
- `/etc/ssh/ssh_host_ecdsa_key y ssh_host_ecdsa_key.pub`
- `/etc/ssh/ssh_host_ed25519_key y ssh_host_ed25519_key.pub`
- `~/.ssh/authorized_keys`
- `ssh_known_hosts`
- `gpg`
- `gpg-agent`
- `~/.gnupg/`


---

## Siguiente paso recomendado

A partir de esta matriz, los siguientes archivos más útiles del proyecto son:

1. `04_matriz_comando_objetivo.md`
2. `05_rutas_y_ficheros_clave.md`
3. `06_comandos_con_sintaxis_y_ejemplos.md`
