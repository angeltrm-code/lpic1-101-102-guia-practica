# 01 — Objetivos desarrollados con comandos y utilidades oficiales (LPIC-1 101 y 102)

> Documento de estudio basado en la página oficial de objetivos de **LPIC-1 (exámenes 101-500 y 102-500, versión 5.0)** de Linux Professional Institute.
>
> En cada objetivo encontrarás:
> - qué debes saber,
> - qué se espera en el examen,
> - comandos, archivos y utilidades citados por LPI en la web oficial.

---

## Cómo usar este documento

- **Lee primero la descripción** para entender el alcance real del objetivo.
- **Memoriza los comandos/archivos** que LPI nombra explícitamente.
- **Practica en terminal** cada objetivo con ejemplos propios.
- **Prioriza por importancia**: cuanto mayor sea la ponderación, más peso suele tener en el examen.

---

# EXAMEN 101

## Tema 101: Arquitectura del sistema

### 101.1 Determinar y configurar los ajustes de hardware
**Importancia:** 2

**Qué debes dominar**
- Identificar el hardware fundamental del sistema.
- Activar o desactivar periféricos integrados.
- Distinguir tipos de almacenamiento masivo.
- Revisar recursos de hardware de los dispositivos.
- Entender de forma conceptual `sysfs`, `udev` y `dbus`.

**Qué debes practicar**
- Consultar información de buses PCI y USB.
- Ver módulos cargados y cargar módulos cuando sea necesario.
- Relacionar hardware detectado con `/sys`, `/proc` y `/dev`.

**Comandos, archivos y utilidades citados por LPI**
- `/sys/`
- `/proc/`
- `/dev/`
- `modprobe`
- `lsmod`
- `lspci`
- `lsusb`

---

### 101.2 Arranque del sistema
**Importancia:** 3

**Qué debes dominar**
- Comprender la secuencia de arranque desde BIOS/UEFI hasta `init`.
- Diferenciar `SysVinit`, `systemd` y conocer `Upstart`.
- Entender el papel del bootloader, el kernel y `initramfs`.
- Revisar eventos de arranque en los registros.

**Qué debes practicar**
- Interpretar mensajes de arranque.
- Revisar el journal y la salida del kernel.
- Entender qué ocurre en cada fase del boot.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 101.3 Cambiar niveles de ejecución / objetivos de arranque y apagar o reiniciar el sistema
**Importancia:** 3

**Qué debes dominar**
- Cambiar entre niveles de ejecución y objetivos de arranque.
- Usar modo monousuario cuando sea necesario.
- Apagar y reiniciar desde terminal.
- Alertar a usuarios antes de operaciones críticas.
- Finalizar procesos de forma correcta.
- Conocer `acpid`.

**Qué debes practicar**
- Diferenciar `runlevels` clásicos y `targets` de `systemd`.
- Ejecutar apagados y reinicios controlados.
- Entender qué servicios afectan al apagado.

**Comandos y términos clave para repasar**
- `systemctl`
- `shutdown`
- `reboot`
- `halt`
- `poweroff`
- `acpid`

> Nota: en la página oficial visible en esta revisión aparecen las áreas de conocimiento de este objetivo, pero la lista parcial de utilidades no se mostraba completa en el fragmento recuperado.

---

## Tema 102: Instalación de Linux y gestión de paquetes

### 102.1 Diseño del esquema de particionado del disco duro
**Importancia:** 2

**Qué debes dominar**
- Diseñar particiones según el uso del sistema.
- Separar `/`, `/var`, `/home`, `/boot`, swap y ESP cuando convenga.
- Entender puntos de montaje y LVM a nivel básico.

**Qué debes practicar**
- Decidir particionado para servidor, escritorio o VM.
- Distinguir cuándo separar `/var`, `/home` o `/boot`.

**Archivos, términos y utilidades citados por LPI**
- Sistema de archivos `/` (raíz)
- Sistema de archivos `/var`
- Sistema de archivos `/home`
- Sistema de archivos `/boot`
- Partición del sistema EFI (ESP)
- Espacio de intercambio (`swap`)
- Puntos de montaje
- Particiones

---

### 102.2 Instalar un gestor de arranque
**Importancia:** 2

**Qué debes dominar**
- Instalar y configurar un gestor de arranque.
- Entender GRUB Legacy y GRUB 2.
- Conocer ubicaciones alternativas y opciones de rescate.
- Interactuar con el gestor de arranque.

**Qué debes practicar**
- Regenerar configuración de GRUB.
- Instalar el cargador en disco correcto.
- Identificar MBR y configuración principal.

**Comandos, archivos y utilidades citados por LPI**
- `menu.lst`, `grub.cfg`, `grub.conf`
- `grub-install`
- `grub-mkconfig`
- `MBR`

---

### 102.3 Gestión de librerías compartidas
**Importancia:** 1

**Qué debes dominar**
- Identificar dependencias de librerías compartidas.
- Conocer ubicaciones habituales de librerías del sistema.
- Entender cómo se cargan.

**Qué debes practicar**
- Inspeccionar dependencias de ejecutables.
- Actualizar la caché de librerías.
- Revisar la ruta de búsqueda de librerías.

**Comandos, archivos y utilidades citados por LPI**
- `ldd`
- `ldconfig`
- `/etc/ld.so.conf`
- `LD_LIBRARY_PATH`

---

### 102.4 Gestión de paquetes Debian
**Importancia:** 3

**Qué debes dominar**
- Instalar, actualizar y desinstalar paquetes Debian.
- Buscar paquetes por archivo o librería.
- Consultar versión, contenido, dependencias e integridad.
- Entender el uso de `apt`.

**Qué debes practicar**
- Revisar repositorios.
- Consultar paquetes instalados y no instalados.
- Reconfigurar paquetes.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/apt/sources.list`
- `dpkg`
- `dpkg-reconfigure`
- `apt-get`
- `apt-cache`

---

### 102.5 Gestión de paquetes RPM y YUM
**Importancia:** 3

**Qué debes dominar**
- Instalar, reinstalar, actualizar y eliminar paquetes con RPM/YUM/Zypper.
- Consultar versión, estado, dependencias, integridad y firmas.
- Saber qué archivos aporta un paquete y de qué paquete proviene un archivo.
- Conocer `dnf`.

**Qué debes practicar**
- Consultas RPM locales.
- Gestión de repositorios y configuración YUM.
- Diferencias básicas entre `yum`, `dnf` y `zypper`.

**Comandos, archivos y utilidades citados por LPI**
- `rpm`
- `rpm2cpio`
- `/etc/yum.conf`
- `/etc/yum.repos.d/`
- `yum`
- `zypper`

---

### 102.6 Linux como sistema virtualizado
**Importancia:** 1

**Qué debes dominar**
- Diferenciar máquina virtual, contenedor Linux y contenedor de aplicación.
- Entender elementos comunes de entornos IaaS.
- Saber qué cambia al clonar una máquina o usarla como plantilla.
- Entender el papel de imágenes de sistema y `cloud-init`.

**Qué debes practicar**
- Identificar elementos que deben regenerarse tras un clonado.
- Reconocer drivers de integración de huésped y claves de host SSH.

**Archivos, términos y utilidades citados por LPI**
- Máquina virtual
- Contenedor Linux
- Contenedor de aplicaciones
- Controladores de la máquina huésped
- Llaves de host SSH
- ID de D-Bus
- `cloud-init`

---

## Tema 103: Comandos GNU y Unix

### 103.1 Trabajar desde la línea de comandos
**Importancia:** 4

**Qué debes dominar**
- Usar la shell Bash para tareas básicas.
- Definir, consultar, exportar y eliminar variables de entorno.
- Usar el historial de comandos.
- Ejecutar comandos dentro y fuera del `PATH`.

**Qué debes practicar**
- Variables y entorno de shell.
- Historial y expansión básica.
- Manuales del sistema.
- Comillas simples y dobles.

**Comandos, archivos y utilidades citados por LPI**
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
- uso de comillas

---

### 103.2 Procesar secuencias de texto usando filtros
**Importancia:** 2

**Qué debes dominar**
- Aplicar filtros a flujos y archivos de texto.
- Usar utilidades clásicas GNU/Unix para transformar salida.

**Qué debes practicar**
- Ordenación, recorte, unión y recuento de texto.
- Lectura de ficheros comprimidos sin descomprimirlos explícitamente.
- Hashes básicos de integridad.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 103.3 Administración básica de archivos
**Importancia:** 4

**Qué debes dominar**
- Copiar, mover, eliminar y crear archivos/directorios.
- Trabajar con copias recursivas.
- Usar comodines simples y avanzados.
- Localizar archivos con `find`.
- Usar `tar`, `cpio` y `dd`.

**Qué debes practicar**
- Compresión y descompresión.
- Identificación de tipo de archivo.
- Operaciones de copia y borrado seguras.

**Comandos, archivos y utilidades citados por LPI**
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
- uso de comodines (*file globbing*)

---

### 103.4 Uso de secuencias de texto, tuberías y redireccionamientos
**Importancia:** 4

**Qué debes dominar**
- Redireccionar `stdin`, `stdout` y `stderr`.
- Encadenar comandos con tuberías.
- Usar la salida de un comando como entrada o argumento de otro.
- Guardar salida simultáneamente en pantalla y archivo.

**Qué debes practicar**
- `>`, `>>`, `2>`, `2>&1`, `|`.
- Construcción de pipelines útiles.
- Tuberías con sustitución de argumentos.

**Comandos, archivos y utilidades citados por LPI**
- `tee`
- `xargs`

---

### 103.5 Crear, supervisar y matar procesos
**Importancia:** 4

**Qué debes dominar**
- Ejecutar trabajos en primer y segundo plano.
- Supervisar procesos activos.
- Seleccionar y ordenar procesos.
- Enviar señales.
- Mantener procesos tras cerrar sesión.

**Qué debes practicar**
- Control de jobs.
- Filtrado por PID o nombre.
- Monitorización de memoria y carga.
- Uso de multiplexores de terminal.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 103.6 Modificar la prioridad de ejecución de los procesos
**Importancia:** 2

**Qué debes dominar**
- Conocer la prioridad por defecto de un proceso.
- Lanzar procesos con prioridad distinta.
- Modificar la prioridad de procesos ya en ejecución.

**Qué debes practicar**
- Diferenciar *nice value* y prioridad observada.
- Cambiar prioridad al crear o después de crear el proceso.

**Comandos, archivos y utilidades citados por LPI**
- `nice`
- `ps`
- `renice`
- `top`

---

### 103.7 Realizar búsquedas en archivos de texto usando expresiones regulares
**Importancia:** 3

**Qué debes dominar**
- Crear expresiones regulares simples.
- Diferenciar BRE y ERE.
- Entender clases, cuantificadores, anclas y caracteres especiales.
- Buscar y reemplazar texto con regex.

**Qué debes practicar**
- Búsquedas con `grep`.
- Filtros con regex extendidas.
- Sustituciones con `sed`.

**Comandos, archivos y utilidades citados por LPI**
- `grep`
- `egrep`
- `fgrep`
- `sed`
- `regex(7)`

---

### 103.8 Edición básica de archivos
**Importancia:** 3

**Qué debes dominar**
- Navegar y editar en `vi`.
- Diferenciar modos.
- Insertar, borrar, copiar, pegar y buscar texto.
- Conocer `vim`, `nano`, `Emacs` y el editor por defecto.

**Qué debes practicar**
- Movimiento básico.
- Guardar/salir con y sin cambios.
- Búsqueda y sustitución básica.

**Comandos, archivos y utilidades citados por LPI**
- `vi`
- `/`, `?`
- `h`, `j`, `k`, `l`
- `i`, `o`, `a`
- `d`, `p`, `y`, `dd`, `yy`
- `ZZ`, `:w!`, `:q!`
- `EDITOR`

---

## Tema 104: Dispositivos, sistemas de archivos Linux y FHS

### 104.1 Creación de particiones y sistemas de archivos
**Importancia:** 2

**Qué debes dominar**
- Administrar tablas de particiones MBR y GPT.
- Crear sistemas de archivos con `mkfs`.
- Manejar swap.
- Conocer ext2/ext3/ext4, XFS, VFAT, exFAT y Btrfs a nivel básico.

**Qué debes practicar**
- Crear particiones.
- Formatear particiones.
- Crear y activar swap.

**Comandos, archivos y utilidades citados por LPI**
- `fdisk`
- `gdisk`
- `parted`
- `mkfs`
- `mkswap`

---

### 104.2 Mantener la integridad de los sistemas de archivos
**Importancia:** 2

**Qué debes dominar**
- Verificar integridad.
- Supervisar espacio libre e inodos.
- Resolver fallos básicos de filesystem.
- Conocer mantenimiento en ext* y XFS.

**Qué debes practicar**
- Revisiones de espacio.
- Reparación de sistemas de archivos.
- Herramientas específicas para ext y XFS.

**Comandos, archivos y utilidades citados por LPI**
- `du`
- `df`
- `fsck`
- `e2fsck`
- `mke2fs`
- `tune2fs`
- `xfs_repair`
- `xfs_fsr`
- `xfs_db`

---

### 104.3 Controlar el montaje y desmontaje de los sistemas de archivos
**Importancia:** 3

**Qué debes dominar**
- Montar y desmontar manualmente.
- Configurar montaje en arranque.
- Usar UUIDs y etiquetas.
- Entender unidades de montaje de `systemd`.

**Qué debes practicar**
- Edición de `/etc/fstab`.
- Montajes temporales y permanentes.
- Identificación de dispositivos y UUIDs.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/fstab`
- `/media/`
- `mount`
- `umount`
- `blkid`
- `lsblk`

---

### 104.4 Eliminado
**Estado en la web oficial:** aparece como eliminado.

**Cómo interpretarlo**
- No lo estudies como objetivo independiente.
- El examen concentra el contenido útil del tema 104 en los demás objetivos activos.

---

### 104.5 Administración de permisos y propietarios de los archivos
**Importancia:** 3

**Qué debes dominar**
- Administrar permisos en archivos y directorios.
- Usar `suid`, `sgid` y `sticky bit`.
- Controlar la máscara de creación (`umask`).
- Gestionar acceso por grupo.

**Qué debes practicar**
- Modos octales y simbólicos.
- Cambios de propietario y grupo.
- Efecto de `umask` sobre nuevos archivos.

**Comandos, archivos y utilidades citados por LPI**
- `chmod`
- `umask`
- `chown`
- `chgrp`

---

### 104.6 Crear y cambiar enlaces duros y simbólicos
**Importancia:** 2

**Qué debes dominar**
- Crear enlaces duros y simbólicos.
- Identificarlos.
- Entender diferencias entre copiar y enlazar.

**Qué debes practicar**
- Creación de enlaces.
- Interpretación de `ls -l`.
- Casos prácticos de administración con enlaces.

**Comandos, archivos y utilidades citados por LPI**
- `ln`
- `ls`

---

### 104.7 Encontrar archivos de sistema y ubicarlos en el lugar correspondiente
**Importancia:** 2

**Qué debes dominar**
- Entender el FHS.
- Conocer ubicaciones típicas de archivos y comandos.
- Localizar binarios, configuraciones y datos.

**Qué debes practicar**
- Búsquedas por nombre y ubicación.
- Diferenciar `find`, `locate`, `which`, `whereis`, `type`.

**Comandos, archivos y utilidades citados por LPI**
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
**Importancia:** 4

**Qué debes dominar**
- Configurar variables de entorno al iniciar sesión o al abrir una shell.
- Escribir funciones Bash para tareas repetidas.
- Ajustar el `PATH` correctamente.
- Mantener el esqueleto para nuevas cuentas.

**Qué debes practicar**
- Diferencias entre perfiles globales y de usuario.
- Archivos que se cargan en login shell y non-login shell.
- Alias, funciones y exportación de variables.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 105.2 Personalización y escritura de scripts sencillos
**Importancia:** 4

**Qué debes dominar**
- Usar sintaxis `sh` básica: bucles y condicionales.
- Sustitución de comandos.
- Interpretar códigos de retorno.
- Encadenar comandos.
- Usar `shebang` correctamente.
- Gestionar permisos y ubicación de scripts.

**Qué debes practicar**
- Scripts con `if`, `for`, `while`.
- Lectura de entrada y control de flujo.
- Condiciones con `&&` y `||`.

**Comandos, archivos y utilidades citados por LPI**
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
**Importancia:** 2

**Qué debes dominar**
- Estructura básica de configuración de X11.
- Autorización y acceso a pantalla.
- Variables y errores de sesión.

**Qué debes practicar**
- Identificar ficheros de configuración.
- Entender `DISPLAY`, `xhost` y `xauth`.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/X11/xorg.conf`
- `/etc/X11/xorg.conf.d/`
- `~/.xsession-errors`
- `xhost`
- `xauth`
- `DISPLAY`
- `X`

---

### 106.2 Escritorios gráficos
**Importancia:** 1

**Qué debes dominar**
- Conocer los principales escritorios Linux.
- Reconocer protocolos de escritorio remoto.

**Qué debes practicar**
- Distinguir entorno de escritorio de protocolo remoto.
- Relacionar X11 con XDMCP/VNC/RDP/Spice.

**Comandos, términos y utilidades citados por LPI**
- `KDE`
- `Gnome`
- `Xfce`
- `X11`
- `XDMCP`
- `VNC`
- `Spice`
- `RDP`

---

### 106.3 Accesibilidad
**Importancia:** 1

**Qué debes dominar**
- Tener conocimiento general de accesibilidad en el escritorio.
- Reconocer ayudas visuales, de entrada y asistencia.

**Términos y utilidades citados por LPI**
- Temas de escritorio de alto contraste / impresión grande
- Lector de pantalla
- Pantalla braille
- Lupa de pantalla
- Teclado en pantalla
- Teclas pegajosas / de repetición
- Teclas lentas / de rebote / de conmutación
- Teclas de ratón
- Gestos
- Reconocimiento de voz

---

## Tema 107: Tareas administrativas

### 107.1 Administrar cuentas de usuario y de grupo y los archivos de sistema relacionados con ellas
**Importancia:** 5

**Qué debes dominar**
- Añadir, modificar, eliminar y suspender usuarios y grupos.
- Gestionar bases de datos de cuentas.
- Crear cuentas limitadas o de propósito especial.

**Qué debes practicar**
- Altas y bajas de usuarios.
- Contraseñas y expiración.
- Consultas de cuentas con `getent`.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 107.2 Automatizar tareas administrativas del sistema mediante la programación de trabajos
**Importancia:** 4

**Qué debes dominar**
- Programar trabajos con `cron`.
- Ejecutar tareas puntuales con `at`.
- Entender temporizadores de `systemd`.
- Configurar permisos de acceso a cron/at.

**Qué debes practicar**
- Crontabs de usuario y sistema.
- Cola de trabajos `at`.
- Temporizadores simples con `systemd-run`.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 107.3 Localización e internacionalización
**Importancia:** 3

**Qué debes dominar**
- Configuración regional y de idioma.
- Zona horaria.
- Uso de `LANG=C` en scripting.
- Codificaciones y conversión de caracteres.

**Qué debes practicar**
- Consultar locale activa.
- Cambiar zona horaria.
- Convertir codificaciones.

**Comandos, archivos y utilidades citados por LPI**
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
**Importancia:** 3

**Qué debes dominar**
- Ajustar fecha y hora del sistema.
- Sincronizar reloj con NTP.
- Entender UTC y reloj hardware.
- Conocer `ntpd`, `chrony` y `ntpq`.

**Qué debes practicar**
- Consultar y ajustar hora.
- Revisar configuración de NTP/Chrony.
- Entender `pool.ntp.org`.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 108.2 Registros del sistema
**Importancia:** 4

**Qué debes dominar**
- Configurar `rsyslog`.
- Entender prioridades, acciones y subsistemas.
- Consultar y filtrar el journal de `systemd`.
- Configurar persistencia y limpieza de logs.
- Entender `logrotate` y relación `rsyslog` / `systemd-journald`.

**Qué debes practicar**
- Consultas con `journalctl`.
- Envío manual de mensajes con `logger`.
- Revisión de rotación de logs.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 108.3 Conceptos básicos del Agente de Transferencia de Correo
**Importancia:** 3

**Qué debes dominar**
- Alias y reenvío básico de correo en host cliente.
- Reconocer los MTA más comunes.

**Qué debes practicar**
- Uso de `~/.forward`.
- Regeneración de aliases.
- Consulta de cola de correo.

**Comandos, archivos y utilidades citados por LPI**
- `~/.forward`
- *sendmail emulation layer commands*
- `newaliases`
- `mail`
- `mailq`
- `postfix`
- `sendmail`
- `exim`

---

### 108.4 Gestión de la impresión y de las impresoras
**Importancia:** 2

**Qué debes dominar**
- Configuración básica de CUPS.
- Gestión de colas de impresión.
- Resolución de problemas.
- Alta y baja de trabajos.

**Qué debes practicar**
- Revisar configuración en `/etc/cups/`.
- Manejar interfaz de compatibilidad LPD.

**Comandos, archivos y utilidades citados por LPI**
- utilidades, herramientas y archivos de configuración de `CUPS`
- `/etc/cups/`
- interfaz legacy de `lpd` (`lpr`, `lprm`, `lpq`)

---

## Tema 109: Fundamentos de redes

### 109.1 Fundamentos de los protocolos de Internet
**Importancia:** 4

**Qué debes dominar**
- Fundamentos TCP/IP.
- Máscaras y CIDR.
- IPv4 vs IPv6.
- Diferencias entre TCP, UDP e ICMP.
- Puertos comunes.

**Qué debes practicar**
- Interpretación de direcciones y subredes.
- Identificación de protocolos y servicios.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/services`
- `IPv4`, `IPv6`
- `Subnetting`
- `TCP`, `UDP`, `ICMP`

---

### 109.2 Configuración de red persistente
**Importancia:** 4

**Qué debes dominar**
- Configurar red persistente en Linux.
- Entender configuración TCP/IP básica.
- Gestionar Ethernet y Wi-Fi con `NetworkManager`.
- Conocer `systemd-networkd`.

**Qué debes practicar**
- Nombre de host.
- Resolución básica local.
- Gestión con `nmcli`.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/hostname`
- `/etc/hosts`
- `/etc/nsswitch.conf`
- `/etc/resolv.conf`
- `nmcli`
- `hostnamectl`
- `ifup`
- `ifdown`

---

### 109.3 Resolución de problemas básicos de red
**Importancia:** 4

**Qué debes dominar**
- Diagnóstico básico de conectividad.
- Inspección de IP, sockets y rutas.
- Uso de herramientas clásicas y modernas.

**Qué debes practicar**
- Comprobación de conectividad.
- Trazado de ruta.
- Revisión de sockets y puertos.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 109.4 Configuración DNS en el lado del cliente
**Importancia:** 2

**Qué debes dominar**
- Consultar DNS remotos.
- Configurar resolución local.
- Cambiar el orden de resolución de nombres.
- Depurar errores de resolución.
- Conocer `systemd-resolved`.

**Qué debes practicar**
- Consultas con `dig` y `host`.
- Revisión de `/etc/resolv.conf`, `/etc/hosts` y `nsswitch`.

**Comandos, archivos y utilidades citados por LPI**
- `/etc/hosts`
- `/etc/resolv.conf`
- `/etc/nsswitch.conf`
- `host`
- `dig`
- `getent`

---

## Tema 110: Seguridad

### 110.1 Tareas de administración de seguridad
**Importancia:** 3

**Qué debes dominar**
- Auditar archivos con `suid/sgid`.
- Cambiar contraseñas y caducidad.
- Detectar puertos abiertos.
- Limitar recursos de usuario.
- Ver qué usuarios están conectados.
- Uso básico de `sudo`.

**Qué debes practicar**
- Búsquedas con `find`.
- Consultas de puertos y procesos.
- Gestión de expiración de contraseñas.

**Comandos, archivos y utilidades citados por LPI**
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
- `who`, `w`, `last`

---

### 110.2 Configuración de la seguridad del sistema
**Importancia:** 3

**Qué debes dominar**
- Entender *shadow passwords*.
- Desactivar servicios no usados.
- Comprender el papel de TCP Wrappers.

**Qué debes practicar**
- Revisión de cuentas y ficheros de autenticación.
- Identificación de servicios heredados y sockets.

**Comandos, archivos y utilidades citados por LPI**
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

---

### 110.3 Protección de datos mediante cifrado
**Importancia:** 4

**Qué debes dominar**
- Uso básico del cliente OpenSSH.
- Claves de host y claves de usuario.
- Uso básico de GnuPG.
- Cifrar, descifrar, firmar y verificar archivos.
- Redirección de puertos y túneles SSH, incluido X11.

**Qué debes practicar**
- Generar claves.
- Cargar claves en agente.
- Autorizar acceso por clave pública.
- Operaciones básicas con `gpg`.

**Comandos, archivos y utilidades citados por LPI**
- `ssh`
- `ssh-keygen`
- `ssh-agent`
- `ssh-add`
- `~/.ssh/id_rsa` y `id_rsa.pub`
- `~/.ssh/id_dsa` y `id_dsa.pub`
- `~/.ssh/id_ecdsa` y `id_ecdsa.pub`
- `~/.ssh/id_ed25519` y `id_ed25519.pub`
- `/etc/ssh/ssh_host_rsa_key` y `ssh_host_rsa_key.pub`
- `/etc/ssh/ssh_host_dsa_key` y `ssh_host_dsa_key.pub`
- `/etc/ssh/ssh_host_ecdsa_key` y `ssh_host_ecdsa_key.pub`
- `/etc/ssh/ssh_host_ed25519_key` y `ssh_host_ed25519_key.pub`
- `~/.ssh/authorized_keys`
- `ssh_known_hosts`
- `gpg`
- `gpg-agent`
- `~/.gnupg/`

---

# Recomendación de estudio final

## Bloques prioritarios
1. **103, 104, 107, 109 y 110**: son los más prácticos y rentables.
2. **102.4 y 102.5**: imprescindible saber Debian y RPM/YUM.
3. **105**: scripting y entorno de shell suelen dar mucho juego en examen y práctica real.

## Método recomendado
- Crea una VM Debian y otra Rocky/Alma/RHEL-like.
- Practica cada comando del documento.
- Haz un resumen propio con:
  - sintaxis mínima,
  - caso de uso,
  - ejemplo real,
  - errores típicos.

## Técnica de repaso
Para cada objetivo, contesta:
- ¿qué problema resuelve?
- ¿qué comandos debo reconocer?
- ¿qué archivos de configuración debo ubicar?
- ¿podría hacerlo en terminal sin mirar apuntes?

---

**Fuente base:** página oficial de objetivos LPIC-1 101-500 / 102-500, versión 5.0, Linux Professional Institute.
