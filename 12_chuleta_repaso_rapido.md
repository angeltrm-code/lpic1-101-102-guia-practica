# 12 — Chuleta de repaso rápido (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Esta chuleta condensa los **conceptos, comandos, rutas y recordatorios clave** para repasar de forma rápida antes del examen o antes de realizar prácticas.

## Cómo usar esta chuleta

- No sustituye el estudio completo.
- Sirve para:
  - repasar rápido
  - refrescar comandos
  - recordar rutas clave
  - detectar huecos antes del examen
- Si un punto no lo entiendes al leerlo, debes volver al documento completo correspondiente.

---

## 1. Ideas base que no debes olvidar

- Linux lo organiza casi todo como **archivos y directorios**.
- En Linux, un disco se **monta** dentro del árbol del sistema; no se usa el modelo de letras como en Windows.
- La shell interpreta comandos, variables, tuberías y redirecciones.
- Muchos comandos Unix hacen **una sola cosa bien** y se combinan entre sí.
- El examen LPIC mezcla:
  - teoría
  - reconocimiento de comandos
  - ficheros de configuración
  - casos prácticos simples

---

## 2. Arranque y arquitectura

### Secuencia de arranque
1. BIOS o UEFI
2. GRUB
3. Kernel
4. initramfs/initrd
5. init/systemd
6. servicios y login

### BIOS vs UEFI
- BIOS: modelo clásico
- UEFI: modelo moderno, normalmente con GPT

### GRUB
- gestor de arranque
- archivos clave:
  - `/boot/grub/grub.cfg`
  - `/etc/default/grub`

### Kernel
- gestiona CPU, memoria, procesos, dispositivos, red y filesystems

### Runlevels clásicos
- `0` apagado
- `1` monousuario
- `3` multiusuario texto
- `5` multiusuario gráfico
- `6` reinicio

### Targets systemd
- `rescue.target`
- `multi-user.target`
- `graphical.target`
- `reboot.target`

---

## 3. Rutas y directorios que debes reconocer

### Muy importantes
- `/etc`
- `/home`
- `/root`
- `/var`
- `/tmp`
- `/usr`
- `/boot`
- `/dev`
- `/proc`
- `/sys`
- `/mnt`
- `/media`

### Recuerda
- `/etc` → configuración
- `/home` → usuarios normales
- `/root` → home de root
- `/var/log` → logs
- `/boot` → arranque
- `/dev` → dispositivos
- `/proc` y `/sys` → pseudo-filesystems del kernel

---

## 4. Ficheros clave que debes saber situar

### Usuarios y autenticación
- `/etc/passwd`
- `/etc/shadow`
- `/etc/group`
- `/etc/gshadow`

### Shell y entorno
- `/etc/profile`
- `~/.profile`
- `~/.bashrc`
- `/etc/environment`

### Montajes
- `/etc/fstab`
- `/proc/mounts`

### Red
- `/etc/hostname`
- `/etc/hosts`
- `/etc/resolv.conf`
- `/etc/nsswitch.conf`
- `/etc/network/interfaces` (Debian clásico)
- `/etc/sysconfig/network-scripts/` (RHEL clásico)

### Logs
- `/var/log/syslog`
- `/var/log/messages`
- `/var/log/auth.log`
- `/var/log/secure`

### Tareas programadas
- `/etc/crontab`
- `/etc/cron.d/`
- `/etc/anacrontab`

### Seguridad
- `/etc/ssh/sshd_config`
- `/etc/sudoers`
- `/etc/pam.d/`
- `/etc/crypttab`

---

## 5. Comandos básicos de navegación y archivos

```bash
pwd
ls
ls -l
ls -la
cd
mkdir
mkdir -p
touch
cp
cp -r
mv
rm
rm -r
rmdir
ln
ln -s
find
locate
file
stat
```

### Recordatorios
- `mv` mueve y también renombra
- `rm -r` borra directorios con contenido
- `ln` crea enlace duro
- `ln -s` crea enlace simbólico
- `find` es muy importante en LPIC

---

## 6. Visualización y tratamiento de texto

```bash
cat
less
head
tail
grep
grep -i
grep -v
grep -r
grep -E
sed
awk
cut
sort
uniq
wc
tr
tee
xargs
```

### Recordatorios
- `tail -f` sigue un log en tiempo real
- `grep -v` excluye coincidencias
- `awk -F:` es típico para `/etc/passwd`
- `sort | uniq -c` cuenta duplicados
- `cut -d: -f1` extrae primera columna en archivos separados por `:`

---

## 7. Redirecciones y tuberías

```bash
>
>>
2>
|
```

### Recuerda
- `>` sobrescribe
- `>>` añade
- `2>` redirige errores
- `|` conecta comandos

Ejemplo típico:
```bash
grep -v '^#' /etc/fstab | grep -v '^$'
```

---

## 8. Procesos y prioridad

```bash
ps
ps aux
ps -ef
top
kill
kill -9 PID
killall
nice
renice
uptime
```

### Ideas clave
- cada proceso tiene PID
- `nice` más alto = menor prioridad
- `kill -9` es forzado; no lo uses como primera opción
- `top` es interactivo

---

## 9. Permisos, propiedad y umask

```bash
chmod
chown
chgrp
umask
```

### Permisos básicos
- `r` leer
- `w` escribir
- `x` ejecutar

### Permisos típicos
- `644` → rw-r--r--
- `755` → rwxr-xr-x
- `600` → rw-------

### Formato simbólico
```bash
chmod u+x script.sh
chmod g-w archivo.txt
chmod o-r archivo.txt
```

### Permisos especiales
- SUID
- SGID
- sticky bit

### Recuerda
- `umask` restringe permisos por defecto, no los asigna directamente

---

## 10. Paquetes

### Debian
```bash
apt update
apt upgrade
apt install paquete
apt remove paquete
apt search paquete
dpkg -i paquete.deb
dpkg -l
dpkg -S /ruta/archivo
```

### RPM / RHEL-like
```bash
rpm -q paquete
rpm -qa
rpm -qi paquete
rpm -ql paquete
yum install paquete
yum update
dnf install paquete
dnf update
```

### Recuerda
- `apt` y `dnf` son herramientas de alto nivel
- `dpkg` y `rpm` trabajan más a bajo nivel

---

## 11. Discos, particiones y filesystems

```bash
lsblk
lsblk -f
blkid
fdisk -l
parted
gdisk
mkfs
mkswap
swapon
swapoff
mount
mount -a
umount
df -h
du -sh
fsck
```

### Recuerda
- `df` muestra espacio de filesystems montados
- `du` mide uso de archivos/directorios
- `/etc/fstab` define montajes persistentes
- MBR es clásico, GPT es moderno

---

## 12. Usuarios, grupos y cuentas

```bash
whoami
id
useradd
usermod
userdel
groupadd
groupmod
groupdel
passwd
chage
su
sudo
```

### Recordatorios
- `useradd -m` crea home
- `usermod -aG grupo usuario` añade a grupo suplementario
- `passwd -l` bloquea cuenta
- `chage -l usuario` muestra caducidad
- `su - usuario` carga entorno de login

---

## 13. Shell y scripting

```bash
echo
env
export
alias
history
bash script.sh
./script.sh
```

### Variables útiles
- `HOME`
- `PATH`
- `USER`
- `SHELL`
- `LANG`

### Parámetros de script
- `$0` nombre del script
- `$1`, `$2` argumentos
- `$#` número de argumentos
- `$@` todos los argumentos

### Recuerda
- shebang típico:
```bash
#!/bin/bash
```
- comillas simples no expanden variables
- comillas dobles sí

---

## 14. Tareas programadas

```bash
crontab -l
crontab -e
crontab -r
at
atq
atrm
```

### Cron
Campos:
- minuto
- hora
- día del mes
- mes
- día de la semana

Ejemplo:
```cron
* * * * * date >> /tmp/prueba.log
```

### Recuerda
- `cron` = repetitivo
- `at` = una sola vez
- `anacron` ayuda en equipos que no están siempre encendidos

---

## 15. Logs y systemd journal

```bash
tail -f /var/log/auth.log
tail -f /var/log/secure
journalctl -b
journalctl -u ssh
journalctl -xe
systemctl status ssh
systemctl status sshd
systemctl start servicio
systemctl stop servicio
systemctl restart servicio
systemctl enable servicio
```

### Recuerda
- Debian suele usar `auth.log`
- RHEL-like suele usar `secure`
- `journalctl -b` = arranque actual
- `journalctl -u` = unidad concreta

---

## 16. Red básica

```bash
ip a
ip route
ip link
ifconfig -a
route -n
ping -c 4 1.1.1.1
ping -c 4 openai.com
ss -tuln
netstat -tulnp
host dominio
dig dominio
nslookup dominio
hostname
nmcli device status
```

### Ideas clave
- IP correcta no implica DNS correcto
- si llegas a una IP pero no al nombre → sospecha DNS
- si no llegas a ninguna IP → sospecha conectividad o gateway
- loopback típico: `127.0.0.1`

---

## 17. Seguridad y cifrado

```bash
ssh usuario@host
ssh -p 2222 usuario@host
scp archivo usuario@host:/ruta/
gpg -c archivo.txt
gpg -d archivo.txt.gpg
openssl version
cryptsetup luksFormat /dev/sdXN
```

### Ideas clave
- root tiene control total
- usa `sudo` cuando sea posible
- SSH = acceso remoto seguro
- GPG = cifrado y firma
- hash no es lo mismo que cifrado
- mínimo privilegio = dar solo permisos necesarios

---

## 18. X11, localización y hora

```bash
xdpyinfo
xwininfo
xev
setxkbmap es
locale
localectl status
date
timedatectl
```

### Recuerda
- `DISPLAY` indica sesión X
- locale afecta idioma, fechas, números y codificación
- hora del sistema y zona horaria no son exactamente lo mismo

---

## 19. Diferencias que suelen preguntar

### Enlace duro vs simbólico
- duro → mismo inodo
- simbólico → apunta por nombre/ruta

### `df` vs `du`
- `df` → uso de filesystem montado
- `du` → uso de directorios/archivos

### `apt` vs `dpkg`
- `apt` → alto nivel, dependencias
- `dpkg` → bajo nivel

### `rpm` vs `dnf/yum`
- `rpm` → bajo nivel
- `dnf/yum` → alto nivel

### `cron` vs `at`
- `cron` → periódico
- `at` → una sola ejecución

### BIOS vs UEFI
- BIOS → clásico
- UEFI → moderno

### MBR vs GPT
- MBR → clásico, más limitado
- GPT → moderno, más flexible

### login shell vs no-login shell
- no cargan exactamente los mismos archivos

---

## 20. Opciones/flags muy frecuentes

### Muy repetidas
- `-a` → all
- `-l` → long
- `-h` → human-readable/help según contexto
- `-r` → recursive/reverse/reboot según comando
- `-f` → force/file/follow según comando
- `-i` → interactive / ignore case según comando
- `-n` → numeric / number
- `-v` → verbose
- `-p` → preserve / parents / pid / port según comando

### Muy típicas en contexto
```bash
ls -lah
grep -rn "ssh" /etc
find /etc -name "*.conf"
df -h
du -sh /var/log
ps aux
kill -9 PID
tar czf copia.tar.gz carpeta/
tar xf copia.tar
ip a
ss -tuln
journalctl -u ssh
```

---

## 21. Errores típicos de examen o laboratorio

- confundir ruta absoluta con relativa
- olvidar `-a` en `usermod -aG`
- usar `rm -rf` sin pensar
- confundir `grep -i` con `grep -v`
- no distinguir `df` de `du`
- pensar que `umask` asigna permisos directamente
- olvidar que `uniq` funciona mejor con datos ordenados
- no distinguir cron del usuario y cron del sistema
- confundir problema DNS con problema de conectividad
- asumir que todos los logs tienen el mismo nombre en todas las distros

---

## 22. Qué deberías poder hacer antes del examen

- moverte con soltura por la shell
- crear, copiar, mover y borrar archivos/directorios
- buscar texto y filtrar resultados
- consultar procesos y finalizar uno
- interpretar permisos y modificarlos
- identificar discos, particiones y montajes
- consultar `/etc/fstab`
- gestionar paquetes en Debian y reconocer RPM
- consultar usuarios, grupos y shells
- escribir scripts sencillos
- programar tareas
- revisar logs
- comprobar conectividad y DNS
- explicar SSH, sudo, PAM, GPG y cifrado básico

---

## 23. Si un punto de esta chuleta no lo recuerdas, vuelve a…

- `05_rutas_y_ficheros_clave.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`
- `07_opciones_frecuentes.md`
- `08_conceptos_clave_101.md`
- `09_conceptos_clave_102.md`
- `10_ejercicios_practicos.md`
- `11_labs_guiados.md`

## Siguiente paso recomendado

El siguiente archivo natural del proyecto es:

- `13_checklist_preparacion_lpic1.md`

Ese documento servirá para marcar qué dominas ya y qué te falta reforzar.
