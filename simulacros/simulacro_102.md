# Simulacro de Examen LPIC-1 (102)

Este simulacro contiene 25 preguntas de opción múltiple representativas del examen 102, más 3 mini-casos prácticos al final. Trata de contestarlo sin apoyos. Las soluciones están al final del documento.

## Preguntas (1 a 25)

**1. Al escribir un script de shell bash, ¿qué variable de entorno contiene el código de salida (exit status) del último comando ejecutado?**
A. `$!`
B. `$?`
C. `$$`
D. `$#`

**2. Quieres ejecutar el script `./backup.sh` usando un programa BASH completamente nuevo en lugar del actual. ¿Cómo se especifica eso en la primera línea del archivo del script (el shebang)?**
A. `//bin/bash`
B. `#!/bin/bash`
C. `#!bash`
D. `import bash`

**3. ¿Qué sentencia en un script de bash lee la entrada del usuario desde el teclado y la guarda en la variable `USUARIO`?**
A. `input USUARIO`
B. `read USUARIO`
C. `get USUARIO`
D. `set USUARIO=$1`

**4. Elige la sintaxis correcta para un bucle for tradicional en Bash que itere por tres archivos: `a.txt`, `b.txt`, `c.txt`:**
A. `for FILE in a.txt b.txt c.txt; do cat $FILE; done`
B. `foreach FILE (a.txt b.txt c.txt) do cat $FILE; done`
C. `for FILE in {a.txt, b.txt, c.txt}: cat $FILE`
D. `for FILE=a.txt to c.txt; do cat $FILE; done`

**5. ¿Qué archivo del usuario configura alias y variables de entorno que se leen en cada sesión de shell interactiva que no requiere login (como al abrir una terminal nueva en el escritorio)?**
A. `~/.bash_profile`
B. `~/.bashrc`
C. `/etc/profile`
D. `~/.profile`

**6. ¿Qué comando SQL es usado clásicamente dentro de un script para consultar bases de datos si tienes un motor, pero en LPIC-1 102 básico, qué concepto relacional básico debes conocer sobre extraer columnas de todas las filas?**
A. `SELECT columna FROM tabla;`
B. `EXTRACT columna DE tabla;`
C. `GET columna IN tabla;`
D. `SHOW columna FROM tabla;`

**7. ¿Qué entorno gráfico (Display Server) es un protocolo moderno, diseñado para sustituir al tradicional X11 por ser más seguro y tener menos sobrecarga?**
A. `XFree86`
B. `LightDM`
C. `Wayland`
D. `GNOME`

**8. En accesibilidad, las "Sticky Keys" (teclas especiales permanentes) sirven principalmente para:**
A. Mantener presionada la tecla Shift o Ctrl mientras se pulsa otra, útil para quienes no pueden pulsar dos teclas a la vez.
B. Ignorar pulsaciones de teclas repetidas si se mantiene el dedo bajado.
C. Aumentar el tamaño del puntero del ratón en la pantalla.
D. Leer en voz alta los menús mediante un lector de pantalla (ej. Orca).

**9. ¿Qué comando usas para crear una nueva cuenta de usuario `alex` que utilice `/bin/zsh` como su shell por defecto?**
A. `usermod -s /bin/zsh alex`
B. `useradd -s /bin/zsh alex`
C. `adduser -shell /bin/zsh alex`
D. `chsh -s /bin/zsh alex` (solo si Alex ya existe)

**10. ¿Qué archivo contiene las contraseñas reales de los usuarios cifradas (hasheadas) en un sistema Linux estándar seguro moderno?**
A. `/etc/passwd`
B. `/etc/shadow`
C. `/var/log/secure`
D. `/etc/security/passwords`

**11. Quieres programar el comando `/usr/local/bin/limpiar_cache.sh` para que se ejecute todos los domingos a las 3:30 AM usando el cron del sistema. ¿Cuál es el registro correcto en `/etc/crontab`?**
A. `30 3 * * 7 root /usr/local/bin/limpiar_cache.sh`
B. `3 30 * * sun root /usr/local/bin/limpiar_cache.sh`
C. `* 3 30 7 * root /usr/local/bin/limpiar_cache.sh`
D. `30 3 * 7 * root /usr/local/bin/limpiar_cache.sh`

**12. ¿Qué comando antiguo de System V se utiliza para encolar un trabajo para ejecutarse una única vez en el futuro (ej. "a las 5 PM de hoy")?**
A. `cron`
B. `at`
C. `batch`
D. `crontab`

**13. Tienes un systemd timer configurado. ¿Qué comando lista todos los timers activos en tu sistema systemd?**
A. `systemctl list-timers`
B. `systemd-timers --list`
C. `journalctl -t timer`
D. `crontab -l`

**14. Para ver y configurar la zona horaria del sistema de forma persistente a "Europe/Madrid" en distribuciones modernas, ¿qué utilidad es la estándar?**
A. `ntpdate`
B. `timedatectl`
C. `hwclock`
D. `tzselect`

**15. ¿Cuál es el nombre del daemon ligero clásico de NTP común en reemplazo de ntpd, introducido por Red Hat y usado mucho por defecto para sincronizar la red?**
A. `chronyd`
B. `timesyncd`
C. `ntp-daemon`
D. `syslog-ng`

**16. Quieres redirigir todos los correos del usuario "root" a un usuario normal llamado "admin" en un sistema local de postfix/exim. ¿Qué fichero editas tradicionalmente?**
A. `/etc/aliases`
B. `/etc/mail/forward.cf`
C. `/etc/postfix/main.cf`
D. `/var/spool/mail/root`

**17. (Después de la edición anterior) ¿Qué comando ejecutas para actualizar la base de datos binaria de alias de correo?**
A. `update-mail`
B. `newaliases`
C. `mail -a`
D. `systemctl restart postfix`

**18. En IPv4, tienes la dirección 192.168.1.10 y la máscara de red es `255.255.255.0`. En notación CIDR, esto equivale a:**
A. `/8`
B. `/16`
C. `/24`
D. `/32`

**19. El nuevo sustituto de comandos clásicos como `ifconfig` o `route` es la familia de comandos `ip` de `iproute2`. ¿Cómo muestras tus rutas de red actuales (la tabla de enrutamiento)?**
A. `ip link show`
B. `ip route show` (o `ip r`)
C. `ip address list`
D. `ip table show`

**20. ¿Qué puerto TCP común se utiliza habitualmente para SSH?**
A. 21
B. 22
C. 23
D. 25

**21. Tienes problemas para ver google.com desde el servidor. ¿Qué comando hace una consulta DNS simple para obtener la IP de un nombre de dominio de los servidores configurados en `/etc/resolv.conf`?**
A. `dig google.com` (o `host google.com`)
B. `ping -D google.com`
C. `netstat -u google.com`
D. `traceroute google.com`

**22. Para comprobar qué puertos están actualmente en escucha por servicios TCP/UDP en tu sistema, ¿cuál de los siguientes es el comando moderno más recomendado (reemplazo de `netstat`)?**
A. `lsof -i`
B. `ss -tulpan`
C. `ip port list`
D. `fw-list`

**23. ¿Qué archivo permite denegar temporalmente que usuarios normales iniciar sesión, obligando a herramientas como `login` a rechazar la conexión dejando un mensaje a los usuarios conectando?**
A. `/etc/nologin`
B. `/etc/shadow`
C. `/etc/deny_users`
D. `/etc/securetty`

**24. Has editado tu archivo `sudoers` incorrectamente con un editor normal y provocas un error de sintaxis que bloquea sudo. ¿Qué comando oficial LPI deberías haber usado EXCLUSIVAMENTE para editar el sudoers y evitar este problema?**
A. `nano /etc/sudoers`
B. `visudo`
C. `vi /etc/sudoers`
D. `sudoedit /etc/sudoers`

**25. Quieres conectar a `server1` mediante ssh pero usando un puerto no estándar (ej. puerto 2222) y con el usuario "operador". ¿Qué sintaxis es válida?**
A. `ssh -p 2222 operador@server1`
B. `ssh --port 2222 operador@server1`
C. `ssh server1:2222 -u operador`
D. `ssh -u operador -P 2222 server1`

---

## Mini-casos prácticos

**Caso 1 (Redes):**  
Estás en un servidor averiado por red. Tienes que configurar *temporalmente* (hasta el reinicio) la tarjeta de red `eth0` con la dirección IP `10.0.0.5` y máscara `/24` utilizando la herramienta `iproute2`. ¿Qué comando usas?  
*Respuesta (comando completo):* _________________________________________________

**Caso 2 (Gestión de usuarios):**  
El empleado 'david' ha abandonado la compañía de malas maneras. Quieres bloquear inmediatamente su cuenta de usuario para que no inicie sesión por contraseña nunca más y eliminar su directorio de trabajo personal `/home/david` para liberar espacio permanentemente. Hazlo en un solo comando típico de System V / Debian-based user management.  
*Respuesta (comando completo):* _________________________________________________

**Caso 3 (Bash y Scripting):**  
Tienes un script viejo en tu directorio local (`./limpia_log.sh`) que arroja un error "Permission denied" al intentar ejecutarlo. El archivo es de tu propiedad, pero falta el permiso de ejecución. Usa el atajo octal tradicional de `chmod` (añadir ejecución general sin tocar lectura/escritura) o la letra de operador para volverlo ejecutable, y luego ejecútalo en la misma línea usando `&&`.  
*Respuesta (comandos unidos):* _________________________________________________

---
---

## Soluciones Simulacro 102

**Respuestas Test Puntuado (1 punto cada una)**
1. **B** (`$?` siempre muestra si el mandato previo acabó en '0' OK o '>0' Error).
2. **B** (El shebang requiere almohadilla, cierre de admiración y la ruta absoluta al binario).
3. **B** (`read` lee un valor introducido interactivo desde stdin).
4. **A** (`for VARIABLE in lista_cosas; do comandos; done`).
5. **B** (`~/.bashrc` se orienta a interactivo non-login, `~/.bash_profile` o `~/.profile` a login shells).
6. **A** (Pregunta teórica simple de SQL oficial).
7. **C** (Aparece fuertemente en LPIC-1 tema 106 de UI gráficas).
8. **A** (Aparece en Accesibilidad e Interfaces de usuario).
9. **B** (`useradd -s ...` lo hace al crear. `usermod` es posterior).
10. **B** (`/etc/passwd` hoy muestra solo una x. Las contraseñas encriptadas saltan a `/etc/shadow`).
11. **A** (Minuto 30, Hora 3, Todo día mes, Todo mes, Día 7=Domingo. Todo ejecutado como root).
12. **B** (`at` lee de stdin los comandos para X momento en el futuro).
13. **A** (Comando básico de control de cronómetros systemd).
14. **B** (`timedatectl set-timezone Europe/Madrid` y sirve para visualizarlo también).
15. **A** (chronyd y su binario cliente chronyc, reemplazaron a ntpd tradicional).
16. **A** (`/etc/aliases` almacena nombres "alias: destino" en Mail Transfer Agents clásicos).
17. **B** (Ejecuta utilería `newaliases` que actualiza el `.db` binario).
18. **C** (255=8 bits x 3 = 24 bits on).
19. **B** (`ip route show` o sus short-forms).
20. **B** (Puerto clásico que deberías saber).
21. **A** (Busca la resolución forward en DNS).
22. **B** (`ss` de socket statistics).
23. **A** (`/etc/nologin`).
24. **B** (`visudo` valida el parsing de sintaxis sudo al salir para que no revienten los privilegios).
25. **A** (`ssh -p PUERTO usuario@host`).

**Soluciones sugeridas Mini-casos (1 punto cada uno)**
* C1: `ip address add 10.0.0.5/24 dev eth0` (o `ip a add 10.0.0.5/24 dev eth0`).
* C2: `userdel -r david` (la -r remove elimina su home directory y correos relacionados. El bloqueo es implícito por su eliminación total. `usermod -L` solo bloquea passwd).
* C3: `chmod +x ./limpia_log.sh && ./limpia_log.sh` (o `chmod 755 ./limpia_log.sh && ./limpia_log.sh`).
