# 06 — Comandos con sintaxis y ejemplos (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Este archivo amplía la lista de comandos con **sintaxis básica**, **ejemplos de uso** y una **nota breve de estudio** orientada a los exámenes 101 y 102.

## Cómo usar este archivo

- Aprende primero **qué hace** el comando.
- Después memoriza su **sintaxis base**.
- Finalmente practica con los **ejemplos**.
- No hace falta dominar todas las opciones avanzadas al principio, pero sí entender el uso típico.

---

## 1. Información del sistema y hardware

### `uname`
Muestra información del sistema.

**Sintaxis básica**
```bash
uname [opciones]
```

**Ejemplos**
```bash
uname -a
uname -r
```

**Qué debes recordar**
- `-a` muestra toda la información principal.
- `-r` muestra la versión del kernel.

---

### `arch`
Muestra la arquitectura del sistema.

**Sintaxis básica**
```bash
arch
```

**Ejemplo**
```bash
arch
```

**Qué debes recordar**
- Útil para identificar si el sistema es `x86_64`, por ejemplo.

---

### `hostname`
Muestra o cambia el nombre del host.

**Sintaxis básica**
```bash
hostname
hostname nuevo-nombre
```

**Ejemplos**
```bash
hostname
hostname servidor01
```

**Qué debes recordar**
- En sistemas modernos suele preferirse `hostnamectl`.

---

### `lscpu`
Muestra información de la CPU.

**Sintaxis básica**
```bash
lscpu
```

**Ejemplo**
```bash
lscpu
```

**Qué debes recordar**
- Muy útil para ver núcleos, arquitectura y virtualización.

---

### `free`
Muestra memoria RAM y swap.

**Sintaxis básica**
```bash
free [opciones]
```

**Ejemplo**
```bash
free -h
```

**Qué debes recordar**
- `-h` da salida legible para humanos.

---

### `dmesg`
Muestra mensajes del kernel.

**Sintaxis básica**
```bash
dmesg
dmesg | grep patron
```

**Ejemplos**
```bash
dmesg | grep -i usb
dmesg | grep -i eth
```

**Qué debes recordar**
- Muy usado para diagnosticar hardware y arranque.

---

### `lsmod`
Lista módulos del kernel cargados.

**Sintaxis básica**
```bash
lsmod
```

**Ejemplo**
```bash
lsmod
```

**Qué debes recordar**
- Suele combinarse con `modprobe` y `rmmod`.

---

### `modprobe`
Carga o gestiona módulos del kernel.

**Sintaxis básica**
```bash
modprobe modulo
```

**Ejemplo**
```bash
sudo modprobe loop
```

**Qué debes recordar**
- Resuelve dependencias automáticamente.

---

## 2. Arranque, apagado y servicios

### `systemctl`
Gestiona servicios y unidades en systemd.

**Sintaxis básica**
```bash
systemctl accion unidad
```

**Ejemplos**
```bash
systemctl status ssh
sudo systemctl start ssh
sudo systemctl enable ssh
sudo systemctl restart NetworkManager
```

**Qué debes recordar**
- Muy importante en sistemas modernos.
- Acciones comunes: `start`, `stop`, `restart`, `status`, `enable`, `disable`.

---

### `journalctl`
Consulta logs de systemd.

**Sintaxis básica**
```bash
journalctl [opciones]
```

**Ejemplos**
```bash
journalctl -xe
journalctl -u ssh
journalctl -b
```

**Qué debes recordar**
- `-u` filtra por unidad.
- `-b` muestra logs desde el último arranque.

---

### `shutdown`
Apaga o reinicia el sistema.

**Sintaxis básica**
```bash
shutdown [opciones] tiempo [mensaje]
```

**Ejemplos**
```bash
sudo shutdown -h now
sudo shutdown -r now
sudo shutdown +10 "Reinicio programado"
```

**Qué debes recordar**
- `-h` apaga.
- `-r` reinicia.

---

### `reboot`
Reinicia el sistema.

**Sintaxis básica**
```bash
reboot
```

**Ejemplo**
```bash
sudo reboot
```

---

### `halt`
Detiene el sistema.

**Sintaxis básica**
```bash
halt
```

**Ejemplo**
```bash
sudo halt
```

---

### `uptime`
Muestra tiempo encendido y carga media.

**Sintaxis básica**
```bash
uptime
```

**Ejemplo**
```bash
uptime
```

---

## 3. Gestión de paquetes

### `apt`
Gestión de paquetes en Debian y derivadas.

**Sintaxis básica**
```bash
apt accion paquete
```

**Ejemplos**
```bash
sudo apt update
sudo apt upgrade
sudo apt install vim
sudo apt remove nano
apt search openssh
```

**Qué debes recordar**
- `update` actualiza índices.
- `upgrade` actualiza paquetes instalados.
- `install`, `remove`, `search` son acciones muy frecuentes.

---

### `dpkg`
Gestiona paquetes `.deb` a bajo nivel.

**Sintaxis básica**
```bash
dpkg [opciones] paquete.deb
```

**Ejemplos**
```bash
sudo dpkg -i paquete.deb
dpkg -l
dpkg -S /bin/ls
```

**Qué debes recordar**
- `-i` instala un `.deb`.
- `-l` lista paquetes.
- `-S` busca qué paquete contiene un archivo.

---

### `rpm`
Gestiona paquetes RPM.

**Sintaxis básica**
```bash
rpm [opciones]
```

**Ejemplos**
```bash
rpm -qa
rpm -q bash
rpm -qi bash
rpm -ql bash
```

**Qué debes recordar**
- Muy importante aunque trabajes más con Debian.
- `-qa` lista todo.
- `-q` consulta.
- `-qi` muestra información.
- `-ql` lista archivos del paquete.

---

### `yum`
Gestión de paquetes en sistemas RPM clásicos.

**Sintaxis básica**
```bash
yum accion paquete
```

**Ejemplos**
```bash
sudo yum install vim
sudo yum update
yum search openssh
```

**Qué debes recordar**
- En sistemas modernos puede sustituirse por `dnf`, pero LPIC sigue mencionando YUM.

---

### `dnf`
Sustituto moderno de YUM en muchas distribuciones RPM.

**Sintaxis básica**
```bash
dnf accion paquete
```

**Ejemplos**
```bash
sudo dnf install vim
sudo dnf update
dnf search httpd
```

---

## 4. Navegación y manejo básico de archivos

### `pwd`
Muestra el directorio actual.

**Sintaxis básica**
```bash
pwd
```

**Ejemplo**
```bash
pwd
```

---

### `ls`
Lista archivos y directorios.

**Sintaxis básica**
```bash
ls [opciones] [ruta]
```

**Ejemplos**
```bash
ls
ls -l
ls -la
ls /etc
```

**Qué debes recordar**
- `-l` formato largo.
- `-a` incluye ocultos.

---

### `cd`
Cambia de directorio.

**Sintaxis básica**
```bash
cd ruta
```

**Ejemplos**
```bash
cd /etc
cd ..
cd ~
```

**Qué debes recordar**
- `..` es el directorio padre.
- `~` es el home del usuario.

---

### `mkdir`
Crea directorios.

**Sintaxis básica**
```bash
mkdir [opciones] directorio
```

**Ejemplos**
```bash
mkdir pruebas
mkdir -p proyecto/docs
```

**Qué debes recordar**
- `-p` crea jerarquías completas.

---

### `rmdir`
Elimina directorios vacíos.

**Sintaxis básica**
```bash
rmdir directorio
```

**Ejemplo**
```bash
rmdir vacio
```

---

### `touch`
Crea archivos vacíos o actualiza marcas de tiempo.

**Sintaxis básica**
```bash
touch archivo
```

**Ejemplos**
```bash
touch nota.txt
touch archivo1 archivo2
```

---

### `cp`
Copia archivos o directorios.

**Sintaxis básica**
```bash
cp [opciones] origen destino
```

**Ejemplos**
```bash
cp archivo.txt copia.txt
cp -r docs/ backup_docs/
```

**Qué debes recordar**
- `-r` para directorios.

---

### `mv`
Mueve o renombra archivos y directorios.

**Sintaxis básica**
```bash
mv origen destino
```

**Ejemplos**
```bash
mv viejo.txt nuevo.txt
mv archivo.txt /tmp/
```

---

### `rm`
Elimina archivos o directorios.

**Sintaxis básica**
```bash
rm [opciones] objetivo
```

**Ejemplos**
```bash
rm archivo.txt
rm -r carpeta/
rm -f fichero.txt
```

**Qué debes recordar**
- `-r` recursivo.
- `-f` fuerza eliminación.

---

### `ln`
Crea enlaces duros o simbólicos.

**Sintaxis básica**
```bash
ln origen enlace
ln -s origen enlace
```

**Ejemplos**
```bash
ln archivo.txt enlace_duro
ln -s /etc/hosts hosts_link
```

**Qué debes recordar**
- `-s` crea enlace simbólico.
- LPIC suele preguntar la diferencia entre ambos tipos.

---

### `file`
Identifica el tipo de un archivo.

**Sintaxis básica**
```bash
file archivo
```

**Ejemplo**
```bash
file /bin/ls
```

---

### `stat`
Muestra metadatos de un archivo.

**Sintaxis básica**
```bash
stat archivo
```

**Ejemplo**
```bash
stat nota.txt
```

---

## 5. Visualización y edición de texto

### `cat`
Muestra el contenido de archivos.

**Sintaxis básica**
```bash
cat archivo
```

**Ejemplos**
```bash
cat /etc/hostname
cat archivo1 archivo2
```

---

### `less`
Permite leer archivos largos de forma paginada.

**Sintaxis básica**
```bash
less archivo
```

**Ejemplo**
```bash
less /etc/services
```

**Qué debes recordar**
- Muy útil para logs y archivos largos.

---

### `head`
Muestra el inicio de un archivo.

**Sintaxis básica**
```bash
head [opciones] archivo
```

**Ejemplo**
```bash
head -n 5 /etc/passwd
```

---

### `tail`
Muestra el final de un archivo.

**Sintaxis básica**
```bash
tail [opciones] archivo
```

**Ejemplos**
```bash
tail -n 10 /var/log/syslog
tail -f /var/log/syslog
```

**Qué debes recordar**
- `-f` sigue el crecimiento del archivo en tiempo real.

---

### `nano`
Editor de texto sencillo.

**Sintaxis básica**
```bash
nano archivo
```

**Ejemplo**
```bash
nano notas.txt
```

---

### `vi` / `vim`
Editor de texto clásico.

**Sintaxis básica**
```bash
vi archivo
vim archivo
```

**Ejemplo**
```bash
vi /etc/hosts
```

**Qué debes recordar**
- Debes saber al menos abrir, insertar, guardar y salir.

---

## 6. Filtros y procesamiento de texto

### `grep`
Busca patrones en texto.

**Sintaxis básica**
```bash
grep [opciones] patron archivo
```

**Ejemplos**
```bash
grep root /etc/passwd
grep -i error logfile.txt
grep -r ssh /etc
```

**Qué debes recordar**
- `-i` ignora mayúsculas/minúsculas.
- `-r` busca recursivamente.

---

### `egrep`
Versión tradicional de grep con expresiones regulares extendidas.

**Sintaxis básica**
```bash
egrep patron archivo
```

**Ejemplo**
```bash
egrep "root|admin" /etc/passwd
```

**Qué debes recordar**
- Hoy suele equivaler a `grep -E`.

---

### `sed`
Editor de flujo para transformar texto.

**Sintaxis básica**
```bash
sed 'expresion' archivo
```

**Ejemplos**
```bash
sed 's/root/admin/' archivo.txt
sed -n '1,10p' archivo.txt
```

---

### `awk`
Procesa texto por columnas y patrones.

**Sintaxis básica**
```bash
awk 'programa' archivo
```

**Ejemplos**
```bash
awk '{print $1}' /etc/passwd
awk -F: '{print $1,$7}' /etc/passwd
```

**Qué debes recordar**
- Muy útil para campos separados por delimitadores.

---

### `cut`
Extrae columnas o campos.

**Sintaxis básica**
```bash
cut [opciones] archivo
```

**Ejemplos**
```bash
cut -d: -f1 /etc/passwd
cut -c1-5 archivo.txt
```

---

### `sort`
Ordena líneas de texto.

**Sintaxis básica**
```bash
sort archivo
```

**Ejemplos**
```bash
sort nombres.txt
sort -n numeros.txt
```

---

### `uniq`
Elimina o muestra duplicados consecutivos.

**Sintaxis básica**
```bash
uniq [opciones]
```

**Ejemplos**
```bash
sort nombres.txt | uniq
sort nombres.txt | uniq -c
```

---

### `wc`
Cuenta líneas, palabras y bytes.

**Sintaxis básica**
```bash
wc [opciones] archivo
```

**Ejemplos**
```bash
wc archivo.txt
wc -l /etc/passwd
```

---

### `tr`
Traduce o reemplaza caracteres.

**Sintaxis básica**
```bash
tr conjunto1 conjunto2
```

**Ejemplo**
```bash
echo "hola" | tr 'a-z' 'A-Z'
```

---

### `tee`
Muestra salida por pantalla y la guarda en archivo.

**Sintaxis básica**
```bash
comando | tee archivo
```

**Ejemplo**
```bash
ls -l | tee listado.txt
```

---

### `xargs`
Construye y ejecuta comandos a partir de la entrada estándar.

**Sintaxis básica**
```bash
comando | xargs otra-orden
```

**Ejemplo**
```bash
find . -name "*.log" | xargs rm
```

**Qué debes recordar**
- Útil, pero hay que tener cuidado con espacios en nombres de archivo.

---

## 7. Redirecciones y tuberías

### Redirección `>`
Envía la salida a un archivo, sobrescribiéndolo.

**Ejemplo**
```bash
echo "hola" > saludo.txt
```

---

### Redirección `>>`
Añade salida al final de un archivo.

**Ejemplo**
```bash
echo "otra línea" >> saludo.txt
```

---

### Redirección `2>`
Envía errores a un archivo.

**Ejemplo**
```bash
comando_inexistente 2> errores.txt
```

---

### Tubería `|`
Envía la salida de un comando a otro.

**Ejemplo**
```bash
cat /etc/passwd | grep root
```

---

## 8. Búsqueda de archivos y comandos

### `find`
Busca archivos y directorios.

**Sintaxis básica**
```bash
find ruta condiciones
```

**Ejemplos**
```bash
find /etc -name "*.conf"
find . -type f
find /home -user angel
```

**Qué debes recordar**
- Muy importante en LPIC.
- Suele combinarse con `-name`, `-type`, `-user`, `-mtime`.

---

### `locate`
Busca archivos en una base de datos indexada.

**Sintaxis básica**
```bash
locate patron
```

**Ejemplo**
```bash
locate sshd_config
```

**Qué debes recordar**
- Depende de una base de datos actualizada.

---

### `which`
Muestra la ruta del ejecutable usado.

**Sintaxis básica**
```bash
which comando
```

**Ejemplo**
```bash
which ls
```

---

### `whereis`
Busca binario, fuentes y páginas man.

**Sintaxis básica**
```bash
whereis comando
```

**Ejemplo**
```bash
whereis bash
```

---

## 9. Procesos y prioridades

### `ps`
Muestra procesos.

**Sintaxis básica**
```bash
ps [opciones]
```

**Ejemplos**
```bash
ps
ps aux
ps -ef
```

**Qué debes recordar**
- `aux` y `-ef` son formatos muy comunes.

---

### `top`
Monitor interactivo de procesos.

**Sintaxis básica**
```bash
top
```

**Ejemplo**
```bash
top
```

---

### `kill`
Envía señales a procesos.

**Sintaxis básica**
```bash
kill señal PID
```

**Ejemplos**
```bash
kill 1234
kill -9 1234
```

**Qué debes recordar**
- `-9` fuerza la finalización con SIGKILL.

---

### `killall`
Finaliza procesos por nombre.

**Sintaxis básica**
```bash
killall nombre
```

**Ejemplo**
```bash
killall firefox
```

---

### `nice`
Ejecuta un comando con prioridad modificada.

**Sintaxis básica**
```bash
nice -n valor comando
```

**Ejemplo**
```bash
nice -n 10 tar cf copia.tar /home
```

---

### `renice`
Cambia la prioridad de un proceso existente.

**Sintaxis básica**
```bash
renice valor -p PID
```

**Ejemplo**
```bash
renice 5 -p 1234
```

---

## 10. Compresión, archivado y copias

### `tar`
Empaqueta archivos.

**Sintaxis básica**
```bash
tar opciones archivo.tar origen
```

**Ejemplos**
```bash
tar cf copia.tar carpeta/
tar xf copia.tar
tar czf copia.tar.gz carpeta/
tar cjf copia.tar.bz2 carpeta/
```

**Qué debes recordar**
- `c` crea.
- `x` extrae.
- `f` usa fichero.
- `z` gzip.
- `j` bzip2.

---

### `gzip`
Comprime archivos con gzip.

**Sintaxis básica**
```bash
gzip archivo
gunzip archivo.gz
```

**Ejemplo**
```bash
gzip informe.txt
```

---

### `bzip2`
Comprime archivos con bzip2.

**Sintaxis básica**
```bash
bzip2 archivo
bunzip2 archivo.bz2
```

**Ejemplo**
```bash
bzip2 informe.txt
```

---

### `xz`
Comprime archivos con xz.

**Sintaxis básica**
```bash
xz archivo
unxz archivo.xz
```

**Ejemplo**
```bash
xz informe.txt
```

---

### `dd`
Copia y convierte datos a bajo nivel.

**Sintaxis básica**
```bash
dd if=origen of=destino [opciones]
```

**Ejemplo**
```bash
dd if=/dev/zero of=archivo.img bs=1M count=100
```

**Qué debes recordar**
- Muy potente y también peligroso.

---

## 11. Discos, particiones y sistemas de archivos

### `lsblk`
Lista discos, particiones y puntos de montaje.

**Sintaxis básica**
```bash
lsblk
```

**Ejemplo**
```bash
lsblk -f
```

---

### `blkid`
Muestra UUID y tipo de filesystem.

**Sintaxis básica**
```bash
blkid
blkid dispositivo
```

**Ejemplo**
```bash
sudo blkid /dev/sda1
```

---

### `fdisk`
Gestiona particiones MBR y consulta discos.

**Sintaxis básica**
```bash
fdisk dispositivo
```

**Ejemplos**
```bash
sudo fdisk -l
sudo fdisk /dev/sdb
```

**Qué debes recordar**
- Muy clásico en LPIC.

---

### `parted`
Herramienta de particionado avanzada.

**Sintaxis básica**
```bash
parted dispositivo
```

**Ejemplo**
```bash
sudo parted /dev/sdb
```

---

### `gdisk`
Gestiona particiones GPT.

**Sintaxis básica**
```bash
gdisk dispositivo
```

**Ejemplo**
```bash
sudo gdisk /dev/sdb
```

---

### `mkfs`
Crea un sistema de archivos.

**Sintaxis básica**
```bash
mkfs -t tipo dispositivo
```

**Ejemplo**
```bash
sudo mkfs -t ext4 /dev/sdb1
```

---

### `mkswap`
Crea espacio swap.

**Sintaxis básica**
```bash
mkswap dispositivo
```

**Ejemplo**
```bash
sudo mkswap /dev/sdb2
```

---

### `swapon`
Activa swap.

**Sintaxis básica**
```bash
swapon dispositivo
```

**Ejemplo**
```bash
sudo swapon /dev/sdb2
```

---

### `swapoff`
Desactiva swap.

**Sintaxis básica**
```bash
swapoff dispositivo
```

**Ejemplo**
```bash
sudo swapoff /dev/sdb2
```

---

### `mount`
Monta sistemas de archivos.

**Sintaxis básica**
```bash
mount dispositivo punto_montaje
```

**Ejemplos**
```bash
sudo mount /dev/sdb1 /mnt
mount | grep sdb1
```

---

### `umount`
Desmonta sistemas de archivos.

**Sintaxis básica**
```bash
umount objetivo
```

**Ejemplo**
```bash
sudo umount /mnt
```

---

### `fsck`
Comprueba y repara sistemas de archivos.

**Sintaxis básica**
```bash
fsck dispositivo
```

**Ejemplo**
```bash
sudo fsck /dev/sdb1
```

---

### `du`
Muestra uso de disco por archivos y directorios.

**Sintaxis básica**
```bash
du [opciones] ruta
```

**Ejemplo**
```bash
du -sh /var/log
```

---

### `df`
Muestra espacio libre en sistemas de archivos montados.

**Sintaxis básica**
```bash
df [opciones]
```

**Ejemplo**
```bash
df -h
```

---

## 12. Permisos y propiedad

### `chmod`
Cambia permisos.

**Sintaxis básica**
```bash
chmod modo archivo
```

**Ejemplos**
```bash
chmod 644 archivo.txt
chmod u+x script.sh
```

**Qué debes recordar**
- Debes conocer notación numérica y simbólica.

---

### `chown`
Cambia propietario.

**Sintaxis básica**
```bash
chown usuario archivo
chown usuario:grupo archivo
```

**Ejemplos**
```bash
sudo chown angel archivo.txt
sudo chown angel:users archivo.txt
```

---

### `chgrp`
Cambia grupo propietario.

**Sintaxis básica**
```bash
chgrp grupo archivo
```

**Ejemplo**
```bash
sudo chgrp developers proyecto.txt
```

---

### `umask`
Define permisos por defecto.

**Sintaxis básica**
```bash
umask
umask valor
```

**Ejemplos**
```bash
umask
umask 022
```

---

## 13. Usuarios y grupos

### `id`
Muestra UID, GID y grupos.

**Sintaxis básica**
```bash
id [usuario]
```

**Ejemplo**
```bash
id
id root
```

---

### `whoami`
Muestra el usuario actual.

**Sintaxis básica**
```bash
whoami
```

**Ejemplo**
```bash
whoami
```

---

### `useradd`
Crea usuarios.

**Sintaxis básica**
```bash
useradd [opciones] usuario
```

**Ejemplo**
```bash
sudo useradd -m alumno
```

---

### `usermod`
Modifica usuarios.

**Sintaxis básica**
```bash
usermod [opciones] usuario
```

**Ejemplo**
```bash
sudo usermod -aG sudo alumno
```

**Qué debes recordar**
- `-aG` añade a grupos suplementarios sin borrar los existentes.

---

### `userdel`
Elimina usuarios.

**Sintaxis básica**
```bash
userdel [opciones] usuario
```

**Ejemplo**
```bash
sudo userdel -r alumno
```

---

### `groupadd`
Crea grupos.

**Sintaxis básica**
```bash
groupadd grupo
```

**Ejemplo**
```bash
sudo groupadd desarrollo
```

---

### `groupmod`
Modifica grupos.

**Sintaxis básica**
```bash
groupmod [opciones] grupo
```

**Ejemplo**
```bash
sudo groupmod -n dev desarrollo
```

---

### `groupdel`
Elimina grupos.

**Sintaxis básica**
```bash
groupdel grupo
```

**Ejemplo**
```bash
sudo groupdel dev
```

---

### `passwd`
Gestiona contraseñas.

**Sintaxis básica**
```bash
passwd [usuario]
```

**Ejemplos**
```bash
passwd
sudo passwd alumno
```

---

### `chage`
Gestiona caducidad de contraseñas.

**Sintaxis básica**
```bash
chage [opciones] usuario
```

**Ejemplo**
```bash
sudo chage -l alumno
```

---

### `su`
Cambia a otro usuario.

**Sintaxis básica**
```bash
su usuario
su - usuario
```

**Ejemplos**
```bash
su root
su - alumno
```

**Qué debes recordar**
- `su -` carga entorno completo de login.

---

### `sudo`
Ejecuta comandos como otro usuario, normalmente root.

**Sintaxis básica**
```bash
sudo comando
```

**Ejemplo**
```bash
sudo apt update
```

---

## 14. Shell, entorno y variables

### `echo`
Muestra texto o variables.

**Sintaxis básica**
```bash
echo texto
echo $VARIABLE
```

**Ejemplos**
```bash
echo "Hola"
echo $HOME
```

---

### `env`
Muestra variables de entorno.

**Sintaxis básica**
```bash
env
```

**Ejemplo**
```bash
env | grep HOME
```

---

### `export`
Define variables de entorno para procesos hijos.

**Sintaxis básica**
```bash
export VARIABLE=valor
```

**Ejemplo**
```bash
export EDITOR=vim
```

---

### `alias`
Define alias de comandos.

**Sintaxis básica**
```bash
alias nombre='comando'
```

**Ejemplo**
```bash
alias ll='ls -la'
```

---

### `history`
Muestra historial de comandos.

**Sintaxis básica**
```bash
history
```

**Ejemplo**
```bash
history | tail
```

---

## 15. Red y diagnóstico básico

### `ip`
Herramienta moderna de red.

**Sintaxis básica**
```bash
ip objeto accion
```

**Ejemplos**
```bash
ip a
ip route
ip link show
```

**Qué debes recordar**
- Sustituye a varias herramientas clásicas.

---

### `ifconfig`
Herramienta clásica de red.

**Sintaxis básica**
```bash
ifconfig
```

**Ejemplo**
```bash
ifconfig -a
```

**Qué debes recordar**
- Antigua, pero LPIC suele pedir reconocerla.

---

### `route`
Muestra o ajusta rutas.

**Sintaxis básica**
```bash
route
```

**Ejemplo**
```bash
route -n
```

---

### `ping`
Comprueba conectividad.

**Sintaxis básica**
```bash
ping destino
```

**Ejemplo**
```bash
ping -c 4 8.8.8.8
```

---

### `ss`
Muestra sockets y conexiones.

**Sintaxis básica**
```bash
ss [opciones]
```

**Ejemplo**
```bash
ss -tuln
```

---

### `netstat`
Herramienta clásica de red.

**Sintaxis básica**
```bash
netstat [opciones]
```

**Ejemplo**
```bash
netstat -tulnp
```

---

### `host`
Consulta DNS.

**Sintaxis básica**
```bash
host nombre
```

**Ejemplo**
```bash
host openai.com
```

---

### `dig`
Consulta DNS en detalle.

**Sintaxis básica**
```bash
dig nombre
```

**Ejemplo**
```bash
dig openai.com
```

---

### `nslookup`
Consulta DNS básica.

**Sintaxis básica**
```bash
nslookup nombre
```

**Ejemplo**
```bash
nslookup openai.com
```

---

### `nmcli`
Gestiona NetworkManager desde terminal.

**Sintaxis básica**
```bash
nmcli [objeto] [acción]
```

**Ejemplo**
```bash
nmcli device status
```

---

## 16. Tareas programadas

### `crontab`
Gestiona tareas programadas de usuario.

**Sintaxis básica**
```bash
crontab [opciones]
```

**Ejemplos**
```bash
crontab -l
crontab -e
```

**Qué debes recordar**
- `-l` lista.
- `-e` edita.

---

### `at`
Programa una tarea única.

**Sintaxis básica**
```bash
at hora
```

**Ejemplo**
```bash
at 23:00
```

---

### `atq`
Lista tareas pendientes de `at`.

**Sintaxis básica**
```bash
atq
```

---

### `atrm`
Elimina tareas programadas con `at`.

**Sintaxis básica**
```bash
atrm numero
```

---

## 17. Seguridad y cifrado

### `ssh`
Cliente de acceso remoto seguro.

**Sintaxis básica**
```bash
ssh usuario@host
```

**Ejemplo**
```bash
ssh angel@192.168.1.50
```

---

### `scp`
Copia archivos por SSH.

**Sintaxis básica**
```bash
scp origen destino
```

**Ejemplo**
```bash
scp archivo.txt angel@192.168.1.50:/tmp/
```

---

### `gpg`
Herramienta de cifrado y firmas.

**Sintaxis básica**
```bash
gpg [opciones] archivo
```

**Ejemplo**
```bash
gpg -c secreto.txt
```

---

### `openssl`
Herramienta de criptografía y certificados.

**Sintaxis básica**
```bash
openssl subcomando
```

**Ejemplo**
```bash
openssl version
```

---

### `cryptsetup`
Gestiona volúmenes cifrados LUKS.

**Sintaxis básica**
```bash
cryptsetup accion dispositivo
```

**Ejemplo**
```bash
sudo cryptsetup luksFormat /dev/sdb1
```

---

## 18. Entorno gráfico y localización

### `xdpyinfo`
Muestra información del servidor X.

**Sintaxis básica**
```bash
xdpyinfo
```

---

### `xwininfo`
Muestra información de ventanas X.

**Sintaxis básica**
```bash
xwininfo
```

---

### `xev`
Captura eventos de teclado y ratón en X.

**Sintaxis básica**
```bash
xev
```

---

### `setxkbmap`
Configura mapa de teclado en X.

**Sintaxis básica**
```bash
setxkbmap diseño
```

**Ejemplo**
```bash
setxkbmap es
```

---

### `locale`
Muestra configuración regional actual.

**Sintaxis básica**
```bash
locale
```

---

### `localectl`
Gestiona localización y teclado en sistemas con systemd.

**Sintaxis básica**
```bash
localectl [subcomando]
```

**Ejemplo**
```bash
localectl status
```

---

## 19. Consejos finales de estudio para este archivo

### Domina primero estos grupos
1. Navegación y manejo de archivos
2. Filtros de texto
3. Procesos
4. Permisos y usuarios
5. Discos y montaje
6. Paquetes
7. Red básica

### Comandos especialmente importantes
- `ls`
- `cp`
- `mv`
- `rm`
- `find`
- `grep`
- `sed`
- `awk`
- `tar`
- `chmod`
- `chown`
- `ps`
- `top`
- `kill`
- `mount`
- `umount`
- `fdisk`
- `lsblk`
- `apt`
- `dpkg`
- `rpm`
- `ip`
- `ping`
- `crontab`
- `systemctl`

## 20. Relación con el resto del proyecto

Este archivo complementa especialmente:

- `02_comandos_agrupados.md`
- `03_matriz_objetivo_comandos.md`
- `04_matriz_comando_objetivo.md`
- `05_rutas_y_ficheros_clave.md`

## Siguiente paso recomendado

El siguiente archivo más útil del proyecto es:

- `07_opciones_frecuentes.md`

Ese documento permitirá estudiar las **opciones cortas y largas más repetidas** en comandos clave, algo muy útil para LPIC-1.
