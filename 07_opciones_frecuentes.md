# 07 — Opciones frecuentes de comandos (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Reúne las **opciones y flags** más comunes de los comandos que aparecen con frecuencia en los exámenes 101 y 102, agrupadas por bloques y con una explicación breve.

## Cómo usar este archivo

- No estudies las opciones como una lista suelta.
- Relaciónalas siempre con el **comando** y con el **efecto** que producen.
- La idea es reconocer rápidamente qué hace una opción cuando aparezca en un ejercicio, una pregunta teórica o un laboratorio.

---

## 1. Opciones muy repetidas en muchos comandos

### `-h`
Suele significar una de estas dos cosas, según el comando:
- **human-readable**: salida legible para humanos.
- **help**: ayuda del comando.

**Ejemplos**
```bash
df -h
du -h
free -h
```

**Qué debes recordar**
- En herramientas de espacio y memoria suele significar “formato legible”.
- En otros comandos puede usarse como ayuda.

---

### `-a`
Suele significar:
- **all**: incluir todos los elementos.

**Ejemplos**
```bash
ls -a
ps aux
uname -a
```

**Qué debes recordar**
- En `ls`, incluye archivos ocultos.
- En otros comandos suele ampliar la salida.

---

### `-l`
Suele significar:
- **long** o formato detallado.

**Ejemplos**
```bash
ls -l
crontab -l
chage -l usuario
```

**Qué debes recordar**
- Muy común en listados detallados.

---

### `-r`
Suele significar una de estas ideas:
- **recursive**: recursivo.
- **reverse**: inverso.
- **reboot**: reiniciar, según el comando.

**Ejemplos**
```bash
cp -r docs/ copia/
rm -r carpeta/
grep -r ssh /etc
shutdown -r now
sort -r archivo.txt
```

---

### `-f`
Suele significar:
- **force**: forzar.
- a veces **file** en comandos como `tar`.

**Ejemplos**
```bash
rm -f archivo.txt
tail -f /var/log/syslog
tar xf copia.tar
tar czf copia.tar.gz carpeta/
```

**Qué debes recordar**
- El significado depende mucho del comando.
- En `rm`, fuerza.
- En `tail`, sigue el archivo en tiempo real.
- En `tar`, indica el nombre del fichero tar.

---

### `-i`
Suele significar:
- **interactive** o confirmación.
- **ignore case** en búsqueda de texto.

**Ejemplos**
```bash
rm -i archivo.txt
cp -i archivo.txt copia.txt
grep -i error log.txt
```

---

### `-n`
Suele significar:
- salida numérica.
- línea número.
- valor numérico.

**Ejemplos**
```bash
head -n 5 archivo.txt
tail -n 10 archivo.txt
sort -n numeros.txt
route -n
```

---

### `-v`
Suele significar:
- **verbose**: salida detallada.

**Ejemplos**
```bash
cp -v archivo.txt copia.txt
mv -v viejo.txt nuevo.txt
rm -v archivo.txt
```

---

### `-q`
Suele significar:
- **quiet** o modo silencioso.
- **query** en `rpm`.

**Ejemplos**
```bash
rpm -q bash
```

---

### `-p`
Suele significar:
- preservar atributos.
- crear padres.
- especificar puerto o PID según el comando.

**Ejemplos**
```bash
mkdir -p proyecto/docs
cp -p archivo.txt copia.txt
renice 5 -p 1234
```

---

## 2. Opciones frecuentes de `ls`

### `ls -l`
Muestra formato largo: permisos, propietario, grupo, tamaño y fecha.

### `ls -a`
Incluye archivos ocultos.

### `ls -la`
Combina listado largo y archivos ocultos.

### `ls -h`
Con `-l`, muestra tamaños legibles.

**Ejemplo**
```bash
ls -lah
```

### `ls -R`
Lista de forma recursiva subdirectorios.

**Qué debes recordar**
- `ls -lah` es una combinación muy típica.

---

## 3. Opciones frecuentes de `cp`, `mv` y `rm`

### `cp -r`
Copia directorios de forma recursiva.

### `cp -i`
Pregunta antes de sobrescribir.

### `cp -p`
Preserva permisos y fechas.

### `cp -v`
Muestra lo que está copiando.

**Ejemplo**
```bash
cp -rpv origen/ destino/
```

---

### `mv -i`
Pregunta antes de sobrescribir.

### `mv -v`
Muestra el cambio realizado.

---

### `rm -r`
Borra directorios y su contenido.

### `rm -f`
Fuerza el borrado sin preguntar.

### `rm -i`
Pide confirmación.

### `rm -rf`
Combinación muy potente y peligrosa.

**Qué debes recordar**
- `rm -rf` elimina recursivamente y sin preguntar.

---

## 4. Opciones frecuentes de `mkdir` y `ln`

### `mkdir -p`
Crea directorios intermedios si no existen.

**Ejemplo**
```bash
mkdir -p curso/lpic/tema1
```

---

### `ln -s`
Crea enlace simbólico.

**Qué debes recordar**
- Sin `-s`, crea enlace duro.

---

## 5. Opciones frecuentes de `cat`, `less`, `head`, `tail`

### `head -n`
Muestra un número concreto de líneas.

**Ejemplo**
```bash
head -n 20 /etc/passwd
```

### `tail -n`
Muestra las últimas líneas.

### `tail -f`
Sigue un archivo en tiempo real.

**Ejemplo**
```bash
tail -f /var/log/auth.log
```

### `less`
No usa muchas flags básicas en el estudio inicial, pero debes recordar:
- navegar con flechas o AvPág/RePág
- salir con `q`
- buscar con `/texto`

---

## 6. Opciones frecuentes de `grep`

### `grep -i`
Ignora mayúsculas y minúsculas.

### `grep -r`
Busca recursivamente.

### `grep -n`
Muestra número de línea.

### `grep -v`
Invierte la coincidencia.

### `grep -E`
Usa expresiones regulares extendidas.

### `grep -c`
Cuenta coincidencias o líneas coincidentes.

**Ejemplos**
```bash
grep -i root /etc/passwd
grep -rn ssh /etc
grep -v "^#" /etc/fstab
grep -E "root|admin" archivo.txt
```

**Qué debes recordar**
- `grep -v` es muy usado para excluir comentarios o líneas concretas.
- `grep -E` equivale al uso tradicional de `egrep`.

---

## 7. Opciones frecuentes de `sed`, `awk`, `cut`, `sort`, `uniq`, `wc`

### `sed -n`
Evita imprimir todo y solo muestra lo que se indique.

**Ejemplo**
```bash
sed -n '1,5p' archivo.txt
```

---

### `awk -F`
Define el separador de campos.

**Ejemplo**
```bash
awk -F: '{print $1,$7}' /etc/passwd
```

---

### `cut -d`
Define delimitador.

### `cut -f`
Selecciona campos.

### `cut -c`
Selecciona columnas/caracteres.

**Ejemplos**
```bash
cut -d: -f1 /etc/passwd
cut -c1-10 archivo.txt
```

---

### `sort -n`
Orden numérico.

### `sort -r`
Orden inverso.

### `sort -u`
Ordena y elimina duplicados.

**Ejemplos**
```bash
sort -n numeros.txt
sort -ru palabras.txt
```

---

### `uniq -c`
Cuenta repeticiones consecutivas.

### `uniq -d`
Muestra solo duplicados.

**Ejemplo**
```bash
sort nombres.txt | uniq -c
```

---

### `wc -l`
Cuenta líneas.

### `wc -w`
Cuenta palabras.

### `wc -c`
Cuenta bytes.

**Ejemplo**
```bash
wc -l /etc/passwd
```

---

## 8. Opciones frecuentes de `find`

### `find -name`
Busca por nombre.

### `find -type`
Filtra por tipo:
- `f` archivo
- `d` directorio
- `l` enlace simbólico

### `find -user`
Busca por propietario.

### `find -group`
Busca por grupo.

### `find -mtime`
Busca por antigüedad en días.

### `find -size`
Busca por tamaño.

### `find -exec`
Ejecuta una acción sobre cada resultado.

**Ejemplos**
```bash
find /etc -name "*.conf"
find . -type f
find /home -user angel
find /var/log -mtime -7
find . -name "*.tmp" -exec rm {} \;
```

**Qué debes recordar**
- `find` es uno de los comandos más importantes de LPIC.
- `-exec` aparece mucho en preguntas prácticas.

---

## 9. Opciones frecuentes de `tar`, `gzip`, `bzip2`, `xz`

### Opciones comunes de `tar`

#### `c`
Crear archivo tar.

#### `x`
Extraer.

#### `t`
Listar contenido.

#### `f`
Trabajar con fichero.

#### `v`
Modo detallado.

#### `z`
Usar gzip.

#### `j`
Usar bzip2.

#### `J`
Usar xz.

**Ejemplos**
```bash
tar cf copia.tar carpeta/
tar xf copia.tar
tar tf copia.tar
tar czf copia.tar.gz carpeta/
tar cjf copia.tar.bz2 carpeta/
tar cJf copia.tar.xz carpeta/
```

**Qué debes recordar**
- En `tar`, muchas opciones se combinan sin guion.
- Debes reconocer bien `czf`, `cjf`, `xf`, `tf`.

---

## 10. Opciones frecuentes de `ps`, `top`, `kill`, `nice`, `renice`

### `ps aux`
Formato clásico BSD, muy frecuente.

### `ps -ef`
Formato tipo SysV, también muy frecuente.

### `kill -9`
Envía SIGKILL.

### `nice -n`
Ejecuta con prioridad específica.

### `renice -p`
Cambia prioridad de un PID concreto.

**Ejemplos**
```bash
ps aux
ps -ef
kill -9 1234
nice -n 10 tar cf copia.tar /home
renice 5 -p 1234
```

**Qué debes recordar**
- No todo proceso debe matarse con `-9`; es la opción más brusca.

---

## 11. Opciones frecuentes de `chmod`, `chown`, `chgrp`, `umask`

### `chmod` en formato numérico
```bash
chmod 644 archivo.txt
chmod 755 script.sh
```

### `chmod` en formato simbólico
```bash
chmod u+x script.sh
chmod g-w archivo.txt
chmod o-r archivo.txt
```

**Qué debes recordar**
- Debes manejar ambos formatos: numérico y simbólico.

---

### `chown usuario:grupo archivo`
Cambia propietario y grupo a la vez.

### `chown -R`
Cambia de forma recursiva.

**Ejemplo**
```bash
sudo chown -R angel:angel proyecto/
```

---

### `chgrp -R`
Cambia grupo de forma recursiva.

---

### `umask 022`
Define permisos por defecto.

**Qué debes recordar**
- Umask no asigna permisos directamente: los restringe.

---

## 12. Opciones frecuentes de `useradd`, `usermod`, `userdel`, `passwd`, `chage`

### `useradd -m`
Crea directorio personal.

### `useradd -s`
Define shell.

### `useradd -u`
Define UID.

**Ejemplo**
```bash
sudo useradd -m -s /bin/bash alumno
```

---

### `usermod -aG`
Añade a grupos suplementarios.

**Ejemplo**
```bash
sudo usermod -aG sudo alumno
```

**Qué debes recordar**
- Muy importante: `-aG`
- Si omites `-a`, puedes sobrescribir grupos existentes.

---

### `userdel -r`
Elimina usuario y su home.

---

### `passwd -l`
Bloquea cuenta.

### `passwd -u`
Desbloquea cuenta.

**Ejemplos**
```bash
sudo passwd -l alumno
sudo passwd -u alumno
```

---

### `chage -l`
Muestra política de caducidad.

**Ejemplo**
```bash
sudo chage -l alumno
```

---

## 13. Opciones frecuentes de `apt`, `dpkg`, `rpm`, `yum`, `dnf`

### `apt update`
Actualiza índices.

### `apt upgrade`
Actualiza paquetes.

### `apt install`
Instala.

### `apt remove`
Elimina.

### `apt search`
Busca paquetes.

---

### `dpkg -i`
Instala paquete `.deb`.

### `dpkg -l`
Lista paquetes instalados.

### `dpkg -S`
Busca qué paquete contiene un archivo.

---

### `rpm -q`
Consulta paquete.

### `rpm -qa`
Lista todos los paquetes.

### `rpm -qi`
Información del paquete.

### `rpm -ql`
Archivos del paquete.

**Ejemplos**
```bash
rpm -q bash
rpm -qa
rpm -qi bash
rpm -ql bash
```

---

### `yum install`
Instala paquetes.

### `yum update`
Actualiza paquetes.

### `yum search`
Busca paquetes.

---

### `dnf install`
Instala paquetes.

### `dnf update`
Actualiza paquetes.

### `dnf search`
Busca paquetes.

---

## 14. Opciones frecuentes de `mount`, `umount`, `df`, `du`, `lsblk`, `fdisk`

### `mount -a`
Monta todo lo definido en `/etc/fstab`.

### `mount -t`
Especifica tipo de filesystem.

**Ejemplos**
```bash
sudo mount -a
sudo mount -t ext4 /dev/sdb1 /mnt
```

---

### `umount`
Normalmente se usa sin muchas flags básicas en el nivel inicial, pero debes recordar:
- se puede desmontar por dispositivo o por punto de montaje

---

### `df -h`
Espacio libre en formato legible.

### `du -sh`
Uso de un directorio en formato resumido y legible.

**Ejemplos**
```bash
df -h
du -sh /var/log
```

---

### `lsblk -f`
Muestra discos, UUID y filesystem.

---

### `fdisk -l`
Lista tablas de particiones.

**Ejemplo**
```bash
sudo fdisk -l
```

---

## 15. Opciones frecuentes de `ip`, `ping`, `ss`, `netstat`, `host`, `dig`

### `ip a`
Muestra direcciones IP e interfaces.

### `ip route`
Muestra tabla de rutas.

### `ip link`
Muestra interfaces.

---

### `ping -c`
Número de paquetes enviados.

**Ejemplo**
```bash
ping -c 4 8.8.8.8
```

---

### `ss -tuln`
Muestra puertos TCP/UDP en escucha, sin resolver nombres.

**Qué significan**
- `t` TCP
- `u` UDP
- `l` listening
- `n` numérico

---

### `netstat -tulnp`
Muy típica en entornos clásicos.

**Qué significan**
- `t` TCP
- `u` UDP
- `l` listening
- `n` numérico
- `p` proceso asociado

---

### `dig`
Suele usarse sin flags básicas al inicio, pero conviene reconocer:
```bash
dig dominio
dig dominio MX
```

---

## 16. Opciones frecuentes de `crontab` y `journalctl`

### `crontab -l`
Lista crontab del usuario.

### `crontab -e`
Edita crontab del usuario.

### `crontab -r`
Elimina crontab del usuario.

**Qué debes recordar**
- `-r` borra la tabla del usuario.

---

### `journalctl -b`
Logs del arranque actual.

### `journalctl -u`
Logs de una unidad concreta.

### `journalctl -xe`
Mensajes detallados recientes.

**Ejemplos**
```bash
journalctl -b
journalctl -u ssh
journalctl -xe
```

---

## 17. Opciones frecuentes de `ssh`, `scp`, `gpg`

### `ssh -p`
Conecta a un puerto distinto del 22.

**Ejemplo**
```bash
ssh -p 2222 usuario@host
```

---

### `scp -r`
Copia directorios de forma recursiva.

**Ejemplo**
```bash
scp -r carpeta/ usuario@host:/tmp/
```

---

### `gpg -c`
Cifra con contraseña simétrica.

### `gpg -d`
Descifra.

**Ejemplos**
```bash
gpg -c secreto.txt
gpg -d secreto.txt.gpg
```

---

## 18. Combinaciones que deberías reconocer al instante

### Listados
```bash
ls -lah
```

### Búsqueda en archivos
```bash
grep -rn "ssh" /etc
```

### Buscar por nombre
```bash
find /etc -name "*.conf"
```

### Espacio en disco
```bash
df -h
du -sh /var/log
```

### Paquetes
```bash
apt search ssh
rpm -qi bash
```

### Procesos
```bash
ps aux
kill -9 1234
```

### Red
```bash
ip a
ping -c 4 1.1.1.1
ss -tuln
```

### Logs
```bash
journalctl -u ssh
tail -f /var/log/auth.log
```

---

## 19. Errores típicos que conviene evitar

- Confundir `-h` de ayuda con `-h` de salida legible.
- Usar `rm -rf` sin entender su impacto.
- Confundir `cp -r` con `mv`.
- Olvidar `-a` en `usermod -aG`.
- Confundir `grep -v` con `grep -i`.
- No distinguir `tar czf` de `tar xf`.
- Confundir `df` con `du`.
- Pensar que `umask` da permisos en vez de restringirlos.

---

## 20. Relación con el resto del proyecto

Este archivo complementa especialmente:

- `02_comandos_agrupados.md`
- `03_matriz_objetivo_comandos.md`
- `04_matriz_comando_objetivo.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`

## Siguiente paso recomendado

Después de este documento, lo más útil es avanzar con uno de estos dos:

- `08_conceptos_clave_101.md`
- `10_ejercicios_practicos.md`

Si seguimos el plan por fases, el siguiente paso natural es:

- `08_conceptos_clave_101.md`
