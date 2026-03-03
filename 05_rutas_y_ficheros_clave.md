# 05 — Rutas y ficheros clave (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Recoge las **rutas, directorios y ficheros** que conviene reconocer para los exámenes **101 y 102**, con una explicación breve y orientada al estudio.

## Cómo usar este archivo

- Úsalo como **guía de referencia rápida** para recordar qué hace cada ruta.
- No todos los archivos se editan a mano en todas las distribuciones, pero **debes reconocer su función**.
- Cuando una ruta cambie entre distribuciones o dependa del sistema, se indica en las notas.

---

## 1. Arranque, kernel y proceso de inicio

### `/boot`
Directorio donde se guardan elementos necesarios para el arranque del sistema, como el kernel y el initramfs.

### `/boot/vmlinuz`
Imagen del kernel Linux que el cargador de arranque utiliza para iniciar el sistema.

### `/boot/initrd.img` o `/boot/initramfs-*`
Imagen de arranque inicial con módulos y utilidades necesarios para montar el sistema de archivos raíz durante el inicio.

### `/boot/grub/`
Directorio principal de GRUB en sistemas BIOS o heredados, con módulos y archivos de configuración del cargador.

### `/boot/grub/grub.cfg`
Archivo de configuración generado de GRUB. Normalmente no se edita a mano; suele regenerarse con herramientas como `update-grub` o `grub2-mkconfig`.

### `/etc/default/grub`
Archivo donde se ajustan opciones generales de GRUB, como el tiempo de espera o los parámetros del kernel.

### `/etc/inittab`
Archivo clásico de SysVinit para definir runlevels y comportamiento del arranque. En sistemas modernos con systemd puede no existir.

### `/sbin/init`
Proceso inicial histórico del sistema. En entornos modernos suele apuntar a systemd.

### `/usr/lib/systemd/`
Jerarquía con unidades, servicios y archivos internos de systemd.

### `/etc/systemd/`
Directorio de configuración local de systemd. Aquí pueden existir unidades personalizadas o sobrescrituras.

### `/etc/systemd/system/`
Ubicación habitual para servicios y unidades definidos o modificados por el administrador.

### `/run`
Directorio temporal en memoria que almacena información de ejecución del sistema desde el arranque actual.

### `/proc`
Sistema de archivos virtual con información sobre procesos, kernel, memoria y dispositivos.

### `/sys`
Sistema de archivos virtual que expone información del kernel y dispositivos a través de sysfs.

---

## 2. Hardware, dispositivos y módulos

### `/dev`
Contiene archivos de dispositivo que representan discos, terminales, particiones y otros recursos del sistema.

### `/dev/sdX`
Nombre típico de discos SCSI, SATA o USB detectados por Linux, por ejemplo `/dev/sda`.

### `/dev/nvme0n1`
Nombre típico de discos NVMe.

### `/dev/tty`
Dispositivos de terminal. Muy importante para entender consolas locales y sesiones de texto.

### `/lib/modules/`
Módulos del kernel organizados por versión.

### `/lib/modules/$(uname -r)/`
Ruta donde se encuentran los módulos del kernel actualmente cargable para la versión activa.

### `/proc/cpuinfo`
Información de CPU expuesta por el kernel.

### `/proc/meminfo`
Información detallada de memoria RAM y swap.

### `/proc/interrupts`
Interrupciones registradas por el sistema.

### `/proc/ioports`
Puertos de entrada/salida usados por dispositivos.

### `/proc/dma`
Información sobre canales DMA, si aplica.

---

## 3. Particiones, montaje y sistemas de archivos

### `/etc/fstab`
Archivo clave para definir qué sistemas de archivos se montan automáticamente y con qué opciones.

### `/etc/mtab`
Listado de sistemas de archivos montados. En muchos sistemas modernos es un enlace hacia información del kernel.

### `/proc/mounts`
Fuente del kernel con la lista actual de montajes.

### `/mnt`
Punto de montaje temporal o manual, usado a menudo por el administrador.

### `/media`
Punto de montaje típico para medios extraíbles, como USB o CD/DVD.

### `/lost+found`
Directorio especial presente en algunos sistemas de archivos, usado para recuperar fragmentos tras errores o reparaciones.

### `/swapfile`
Archivo de intercambio si el sistema usa swap basada en archivo en lugar de partición.

### `/etc/filesystems`
Puede listar tipos de sistemas de archivos conocidos o permitidos, según la distribución.

### `/sbin/fsck`
Ruta histórica de la utilidad de comprobación de sistemas de archivos.

### `/sbin/mkfs`
Ruta genérica histórica para herramientas de creación de sistemas de archivos.

---

## 4. Usuarios, grupos y autenticación

### `/etc/passwd`
Base de datos de usuarios del sistema. Contiene nombre de usuario, UID, GID, ruta del home y shell por defecto.

### `/etc/shadow`
Archivo protegido con hashes de contraseñas y políticas de expiración.

### `/etc/group`
Base de datos de grupos del sistema.

### `/etc/gshadow`
Archivo protegido con información sensible de grupos.

### `/etc/skel/`
Plantilla base que se copia al crear el directorio personal de un nuevo usuario.

### `/home`
Directorio raíz habitual para los directorios personales de los usuarios normales.

### `/root`
Directorio personal del superusuario `root`.

### `/etc/login.defs`
Configuración general relacionada con creación de usuarios, UID/GID y políticas de contraseña en muchas distribuciones.

### `/etc/default/useradd`
Valores por defecto usados por `useradd` en sistemas que soportan este archivo.

### `/etc/shells`
Lista de shells válidas o permitidas en el sistema.

### `/etc/security/`
Jerarquía usada por varios componentes de seguridad, especialmente PAM y límites de recursos.

### `/etc/security/limits.conf`
Archivo habitual para establecer límites de recursos por usuario o grupo.

### `/etc/pam.d/`
Directorio de configuración de PAM, usado para autenticación, autorización y control de sesiones.

### `/etc/nologin`
Si existe, puede impedir el inicio de sesión de usuarios normales mostrando un mensaje.

---

## 5. Entorno de shell y sesión

### `/etc/profile`
Configuración global de shell para usuarios que inician sesión con shells compatibles.

### `/etc/bash.bashrc`
Archivo global de configuración de Bash en Debian y derivadas. No existe igual en todas las distribuciones.

### `~/.profile`
Configuración personal de entorno al iniciar sesión.

### `~/.bash_profile`
Archivo personal típico para shells de login Bash.

### `~/.bash_login`
Alternativa a `.bash_profile` si esta no existe.

### `~/.bashrc`
Configuración personal interactiva de Bash: alias, variables, prompt y funciones.

### `~/.bash_logout`
Acciones a ejecutar al cerrar una sesión de shell de login.

### `/etc/environment`
Archivo simple para variables globales de entorno.

### `/etc/inputrc`
Configuración de readline, útil para edición en línea de comandos.

### `~/.inputrc`
Versión por usuario de la configuración de readline.

---

## 6. Tareas programadas y automatización

### `/etc/crontab`
Archivo principal de cron a nivel del sistema.

### `/etc/cron.d/`
Directorio para tareas cron definidas por paquetes o por el administrador.

### `/etc/cron.hourly/`
Scripts ejecutados periódicamente cada hora, según la implementación del sistema.

### `/etc/cron.daily/`
Scripts ejecutados diariamente.

### `/etc/cron.weekly/`
Scripts ejecutados semanalmente.

### `/etc/cron.monthly/`
Scripts ejecutados mensualmente.

### `/var/spool/cron/`
Ubicación típica de crontabs por usuario, aunque puede variar según la distribución.

### `/var/spool/at/`
Ubicación asociada a trabajos programados con `at`, dependiendo de la implementación.

### `/etc/anacrontab`
Configuración de anacron, útil para tareas periódicas en equipos que no están siempre encendidos.

---

## 7. Red, nombre del sistema y resolución

### `/etc/hostname`
Nombre persistente del sistema.

### `/etc/hosts`
Resolución local estática de nombres a direcciones IP.

### `/etc/resolv.conf`
Configuración de resolutores DNS. En muchos sistemas puede ser gestionado automáticamente por NetworkManager, systemd-resolved u otros servicios.

### `/etc/nsswitch.conf`
Define el orden de búsqueda para nombres, usuarios, grupos y otros servicios del sistema.

### `/etc/network/interfaces`
Archivo clásico de red en Debian y derivadas. Muy importante para LPIC aunque no se use en todas las distribuciones modernas.

### `/etc/sysconfig/network-scripts/`
Ubicación histórica de scripts de red en Red Hat/CentOS/Rocky Linux clásicos.

### `/etc/sysconfig/network`
Archivo histórico de configuración general de red en sistemas Red Hat clásicos.

### `/etc/hosts.allow`
Control de acceso basado en TCP Wrappers para servicios compatibles.

### `/etc/hosts.deny`
Complemento de `hosts.allow` para denegar acceso.

### `/etc/services`
Base de datos local de puertos y nombres de servicio.

### `/etc/protocols`
Listado local de protocolos de red conocidos.

---

## 8. Registros y monitorización

### `/var/log/`
Directorio principal de logs del sistema.

### `/var/log/syslog`
Log general del sistema en Debian y derivadas cuando se usa rsyslog o syslog tradicional.

### `/var/log/messages`
Log general del sistema en muchas distribuciones tipo Red Hat.

### `/var/log/auth.log`
Registro típico de autenticación en Debian y derivadas.

### `/var/log/secure`
Registro típico de seguridad/autenticación en Red Hat y derivadas.

### `/var/log/kern.log`
Mensajes del kernel en sistemas que lo separan en un archivo específico.

### `/var/log/dmesg`
Volcado o registro de mensajes de arranque del kernel, según distribución.

### `/var/log/boot.log`
Mensajes del proceso de arranque, si la distribución lo genera.

### `/var/log/wtmp`
Registro binario de inicios y cierres de sesión.

### `/var/log/btmp`
Registro binario de intentos fallidos de inicio de sesión.

### `/var/run/utmp` o `/run/utmp`
Registro de sesiones activas.

### `/etc/rsyslog.conf`
Archivo principal de configuración de rsyslog.

### `/etc/rsyslog.d/`
Directorio para fragmentos de configuración adicionales de rsyslog.

### `/etc/systemd/journald.conf`
Configuración principal de systemd-journald.

---

## 9. Impresión y servicios esenciales

### `/etc/printcap`
Archivo clásico de configuración de impresoras en sistemas BSD/lpd; hoy puede no usarse, pero conviene reconocerlo.

### `/etc/cups/`
Directorio de configuración del sistema de impresión CUPS.

### `/etc/aliases`
Alias locales de correo para el MTA.

### `/etc/alias`
Ruta histórica o alternativa en algunos sistemas.

### `/var/spool/mail/`
Ubicación típica de buzones locales de correo.

### `/etc/postfix/`
Configuración de Postfix, si está instalado.

### `/etc/ssmtp/`
Configuración de SSMTP, si existe en el sistema.

---

## 10. Seguridad, acceso remoto y cifrado

### `/etc/ssh/sshd_config`
Configuración del servidor SSH.

### `/etc/ssh/ssh_config`
Configuración global del cliente SSH.

### `~/.ssh/`
Directorio personal con claves y configuración SSH del usuario.

### `~/.ssh/authorized_keys`
Claves públicas autorizadas para acceso remoto al usuario.

### `~/.ssh/known_hosts`
Registro de hosts SSH conocidos.

### `/etc/sudoers`
Archivo principal de configuración de `sudo`. Debe editarse con `visudo`.

### `/etc/sudoers.d/`
Fragmentos adicionales de configuración de sudo.

### `/etc/crypttab`
Define volúmenes cifrados que deben abrirse durante el arranque.

### `/etc/ssl/`
Directorio con certificados, claves y material TLS/SSL según distribución y paquetes instalados.

### `/root/.gnupg/` y `~/.gnupg/`
Directorios usados por GnuPG para almacenar claves y configuración.

---

## 11. Jerarquía FHS y rutas generales importantes

### `/`
Raíz del sistema de archivos. Todo cuelga de esta ruta.

### `/bin`
Comandos esenciales de usuario. En sistemas modernos puede ser un enlace a `/usr/bin`.

### `/sbin`
Comandos esenciales de administración. También puede estar integrado en `/usr/sbin`.

### `/usr`
Jerarquía con la mayor parte del software, documentación y datos de solo lectura compartidos.

### `/usr/bin`
Programas de usuario no esenciales para el arranque mínimo.

### `/usr/sbin`
Herramientas de administración no esenciales para el arranque mínimo.

### `/usr/lib`
Bibliotecas y componentes compartidos de programas.

### `/lib`
Bibliotecas esenciales para binarios básicos y arranque. A menudo integrada con `/usr/lib`.

### `/opt`
Software adicional o de terceros instalado fuera de la jerarquía habitual de paquetes base.

### `/srv`
Datos servidos por servicios del sistema, como web o FTP, cuando la política de la distribución lo usa.

### `/tmp`
Directorio temporal para ficheros de corta duración.

### `/var`
Datos variables: logs, colas, cachés, spools y estados cambiantes.

### `/var/tmp`
Temporal de más larga duración que `/tmp`.

---

## 12. Rutas personales y permisos

### `~`
Directorio personal del usuario actual.

### `~/.*`
Archivos ocultos del usuario, normalmente usados para configuración.

### `.` 
Directorio actual.

### `..`
Directorio padre.

### Rutas absolutas
Empiezan por `/` y se interpretan desde la raíz del sistema.

### Rutas relativas
Se interpretan desde el directorio actual.

---

## 13. Qué deberías saber de cada fichero en LPIC-1

Para cada ruta importante, intenta responder estas preguntas:

1. **¿Qué guarda o controla?**
2. **¿Se consulta, se edita o ambas cosas?**
3. **¿Quién debería poder modificarlo?**
4. **¿A qué objetivo del examen se relaciona?**
5. **¿Con qué comando lo revisarías?**

Ejemplo rápido:

- `/etc/fstab`
  - Define montajes persistentes.
  - Se consulta y a veces se edita.
  - Solo debería modificarlo un administrador.
  - Relacionado con particiones, montaje y sistemas de archivos.
  - Se revisa con `cat`, `less`, `grep` o un editor como `vi`.

---

## 14. Prioridades de estudio recomendadas

### Prioridad alta
- `/etc/fstab`
- `/etc/passwd`
- `/etc/shadow`
- `/etc/group`
- `/etc/hosts`
- `/etc/resolv.conf`
- `/etc/hostname`
- `/etc/crontab`
- `/var/log/`
- `/boot/grub/grub.cfg`
- `/etc/default/grub`
- `/etc/sudoers`
- `~/.bashrc`
- `/etc/profile`

### Prioridad media
- `/etc/pam.d/`
- `/etc/login.defs`
- `/etc/nsswitch.conf`
- `/etc/ssh/sshd_config`
- `/etc/crypttab`
- `/etc/rsyslog.conf`
- `/etc/systemd/`
- `/etc/systemd/system/`
- `/proc/*`
- `/sys`

### Prioridad de reconocimiento
- `/etc/printcap`
- `/etc/aliases`
- `/var/spool/mail/`
- `/etc/sysconfig/network`
- `/etc/sysconfig/network-scripts/`
- `/etc/filesystems`
- `/etc/hosts.allow`
- `/etc/hosts.deny`

---

## 15. Relación con el resto del proyecto

Este archivo complementa especialmente:

- `01_objetivos_desarrollados.md`
- `02_comandos_agrupados.md`
- `03_matriz_objetivo_comandos.md`
- `04_matriz_comando_objetivo.md`

## Siguiente paso recomendado

El siguiente archivo más útil del proyecto es:

- `06_comandos_con_sintaxis_y_ejemplos.md`

Ese documento permitirá pasar de la **identificación de comandos** a su **uso real con sintaxis y ejemplos típicos de examen**.
