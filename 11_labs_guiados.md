# 11 — Labs guiados (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Este archivo convierte parte del material anterior en **mini laboratorios guiados, paso a paso y reproducibles**, pensados para practicar en una VM Linux de forma ordenada.

## Cómo usar este archivo

- Ejecuta cada laboratorio en una **máquina virtual** o entorno de pruebas.
- Lee primero el objetivo completo.
- Sigue los pasos en orden.
- Comprueba el resultado en cada fase.
- Si algo falla, revisa la sección **errores comunes** antes de repetir.

## Recomendación de entorno

### Opción mínima
- 1 VM Debian o Ubuntu para practicar LPIC-1

### Opción recomendada
- 1 VM Debian
- 1 VM Rocky Linux / AlmaLinux / RHEL-like

### Requisitos
- usuario con permisos `sudo`
- acceso a terminal
- conexión de red funcional
- snapshot previo si quieres poder volver atrás

---

## Lab 1 — Archivos, directorios y rutas

### Objetivo
Practicar:
- `pwd`
- `ls`
- `cd`
- `mkdir`
- `touch`
- `cp`
- `mv`
- `rm`
- `rmdir`

### Escenario
Vas a crear una pequeña estructura de trabajo para estudiar LPIC-1 y luego la modificarás.

### Pasos

#### Paso 1. Comprueba dónde estás
```bash
pwd
```

**Qué debes ver**
- la ruta de tu directorio actual

---

#### Paso 2. Crea una carpeta principal
```bash
mkdir -p ~/lpic-labs/lab1
cd ~/lpic-labs/lab1
```

**Comprobación**
```bash
pwd
ls
```

---

#### Paso 3. Crea una estructura de subdirectorios
```bash
mkdir -p tema101 tema102 notas
```

**Comprobación**
```bash
ls
```

---

#### Paso 4. Crea archivos vacíos
```bash
touch notas/dia1.txt notas/dia2.txt tema101/comandos.txt
```

**Comprobación**
```bash
find .
```

---

#### Paso 5. Copia y renombra archivos
```bash
cp notas/dia1.txt tema101/
mv tema101/dia1.txt tema101/introduccion.txt
```

**Comprobación**
```bash
find .
```

---

#### Paso 6. Mueve un archivo
```bash
mv notas/dia2.txt tema102/
```

---

#### Paso 7. Elimina un archivo y un directorio vacío
```bash
rm tema101/introduccion.txt
mkdir vacio
rmdir vacio
```

**Comprobación final**
```bash
find .
```

### Qué deberías haber aprendido
- diferencia entre copiar y mover
- diferencia entre borrar archivos y borrar directorios vacíos
- uso de rutas relativas y absolutas

### Errores comunes
- intentar usar `rmdir` sobre un directorio con contenido
- confundir `mv` como “solo mover” cuando también renombra
- crear archivos en una ruta distinta a la prevista

---

## Lab 2 — Texto, redirecciones y filtros

### Objetivo
Practicar:
- `echo`
- `cat`
- `head`
- `tail`
- `grep`
- `cut`
- `awk`
- `sort`
- `uniq`
- redirecciones y tuberías

### Escenario
Vas a crear un archivo de texto y usar filtros para extraer información útil.

### Pasos

#### Paso 1. Crea el laboratorio
```bash
mkdir -p ~/lpic-labs/lab2
cd ~/lpic-labs/lab2
```

---

#### Paso 2. Crea un archivo con varias líneas
```bash
echo "root:x:0:0:root:/root:/bin/bash" > usuarios_demo.txt
echo "ana:x:1000:1000:Ana:/home/ana:/bin/bash" >> usuarios_demo.txt
echo "juan:x:1001:1001:Juan:/home/juan:/bin/zsh" >> usuarios_demo.txt
echo "invitado:x:1002:1002:Invitado:/home/invitado:/bin/false" >> usuarios_demo.txt
```

**Comprobación**
```bash
cat usuarios_demo.txt
```

---

#### Paso 3. Muestra solo las primeras y últimas líneas
```bash
head -n 2 usuarios_demo.txt
tail -n 2 usuarios_demo.txt
```

---

#### Paso 4. Busca usuarios con shell bash
```bash
grep "/bin/bash" usuarios_demo.txt
```

---

#### Paso 5. Muestra solo el nombre de usuario
```bash
cut -d: -f1 usuarios_demo.txt
```

---

#### Paso 6. Muestra nombre y shell con `awk`
```bash
awk -F: '{print $1, $7}' usuarios_demo.txt
```

---

#### Paso 7. Crea un archivo con palabras duplicadas
```bash
printf "ssh
cron
ssh
sudo
cron
cron
" > palabras.txt
```

**Comprobación**
```bash
cat palabras.txt
```

---

#### Paso 8. Ordena y cuenta duplicados
```bash
sort palabras.txt | uniq -c
```

---

#### Paso 9. Filtra líneas que no empiecen por comentario en `/etc/fstab`
```bash
grep -v '^#' /etc/fstab | grep -v '^$'
```

### Qué deberías haber aprendido
- cómo construir archivos con `>` y `>>`
- cómo filtrar por patrón
- cómo extraer columnas
- cómo combinar herramientas pequeñas con tuberías

### Errores comunes
- sobrescribir un archivo por error usando `>`
- olvidar el delimitador correcto en `cut` o `awk`
- usar `uniq` sin ordenar antes cuando buscas agrupación correcta

---

## Lab 3 — Búsqueda, permisos y enlaces

### Objetivo
Practicar:
- `find`
- `chmod`
- `chown`
- `chgrp`
- `ln`
- `ln -s`
- `ls -l`

### Escenario
Vas a crear una carpeta de scripts y ajustar sus permisos correctamente.

### Pasos

#### Paso 1. Prepara el laboratorio
```bash
mkdir -p ~/lpic-labs/lab3/scripts
cd ~/lpic-labs/lab3
```

---

#### Paso 2. Crea archivos de prueba
```bash
touch scripts/backup.sh scripts/monitor.sh scripts/notas.txt
```

---

#### Paso 3. Da permisos de ejecución a los scripts
```bash
chmod u+x scripts/backup.sh scripts/monitor.sh
```

**Comprobación**
```bash
ls -l scripts
```

---

#### Paso 4. Crea un enlace duro y uno simbólico
```bash
touch original.txt
ln original.txt enlace_duro.txt
ln -s original.txt enlace_simbolico.txt
```

**Comprobación**
```bash
ls -li
```

**Qué debes observar**
- el enlace duro comparte inodo
- el simbólico no

---

#### Paso 5. Busca scripts `.sh`
```bash
find . -name "*.sh"
```

---

#### Paso 6. Busca solo directorios
```bash
find . -type d
```

---

#### Paso 7. Si tienes permisos, cambia grupo o propietario
```bash
# Ejemplos, solo si procede en tu laboratorio
# sudo chgrp users scripts/notas.txt
# sudo chown $USER:$USER scripts/notas.txt
```

### Qué deberías haber aprendido
- aplicar permisos simbólicos
- observar permisos con `ls -l`
- diferenciar enlace duro y simbólico
- buscar archivos por nombre y tipo

### Errores comunes
- olvidar `-s` en enlaces simbólicos
- pensar que el enlace simbólico comparte inodo con el original
- ejecutar `find` desde una ruta equivocada

---

## Lab 4 — Procesos, foreground/background y prioridad

### Objetivo
Practicar:
- `ps`
- `top`
- `kill`
- `nice`
- `renice`
- `uptime`

### Escenario
Vas a lanzar procesos simples y administrarlos como lo haría un admin junior.

### Pasos

#### Paso 1. Consulta estado general del sistema
```bash
uptime
ps aux | head
```

---

#### Paso 2. Lanza un proceso en segundo plano
```bash
sleep 300 &
```

**Comprobación**
```bash
ps aux | grep sleep
```

---

#### Paso 3. Finaliza el proceso
1. Identifica el PID del `sleep`
2. Finalízalo:
```bash
kill PID
```

**Comprobación**
```bash
ps aux | grep sleep
```

---

#### Paso 4. Lanza un proceso con `nice`
```bash
nice -n 10 sleep 300 &
```

**Comprobación**
```bash
ps -o pid,ni,cmd -C sleep
```

---

#### Paso 5. Cambia prioridad con `renice`
```bash
renice 5 -p PID
```

**Comprobación**
```bash
ps -o pid,ni,cmd -p PID
```

---

#### Paso 6. Finaliza el proceso otra vez
```bash
kill PID
```

### Qué deberías haber aprendido
- diferencia entre proceso en foreground y background
- cómo localizar y terminar un proceso
- cómo modificar prioridad

### Errores comunes
- matar el PID equivocado
- abusar de `kill -9` sin necesidad
- no comprobar si el proceso sigue activo tras enviar la señal

---

## Lab 5 — Paquetes en Debian y RPM

### Objetivo
Practicar:
- `apt`
- `dpkg`
- `rpm`
- `yum`
- `dnf`

### Escenario
Vas a consultar, instalar y relacionar paquetes con archivos.

### Variante A — Debian/Ubuntu

#### Paso 1. Actualiza índices
```bash
sudo apt update
```

---

#### Paso 2. Busca un paquete
```bash
apt search tree
```

---

#### Paso 3. Instálalo
```bash
sudo apt install -y tree
```

---

#### Paso 4. Comprueba qué paquete contiene `/bin/ls`
```bash
dpkg -S /bin/ls
```

---

#### Paso 5. Lista paquetes relacionados con SSH
```bash
dpkg -l | grep ssh
```

### Variante B — Rocky / RHEL-like

#### Paso 1. Lista todos los paquetes
```bash
rpm -qa | head
```

---

#### Paso 2. Consulta si existe `bash`
```bash
rpm -q bash
```

---

#### Paso 3. Muestra información del paquete
```bash
rpm -qi bash
```

---

#### Paso 4. Lista archivos del paquete
```bash
rpm -ql bash | head
```

### Qué deberías haber aprendido
- diferencia entre herramienta de alto nivel y bajo nivel
- cómo relacionar archivos con paquetes
- cómo consultar metadatos de paquetes

### Errores comunes
- usar sintaxis de Debian en una distro RPM o al revés
- asumir que `rpm` resuelve dependencias igual que `dnf`
- no distinguir `apt` de `dpkg`

---

## Lab 6 — Discos, particiones, montaje y fstab

### Objetivo
Practicar:
- `lsblk`
- `blkid`
- `df`
- `du`
- `mount`
- `umount`
- lectura de `/etc/fstab`

### Escenario
Vas a revisar almacenamiento y comprender cómo se montan sistemas de archivos.

### Pasos

#### Paso 1. Lista discos y particiones
```bash
lsblk
lsblk -f
```

---

#### Paso 2. Consulta UUID y tipos de filesystem
```bash
sudo blkid
```

---

#### Paso 3. Revisa espacio de disco
```bash
df -h
du -sh /var/log
```

**Qué debes observar**
- `df` trabaja sobre sistemas de archivos montados
- `du` mide uso de directorios o archivos

---

#### Paso 4. Revisa `/etc/fstab`
```bash
cat /etc/fstab
```

#### Paso 5. Filtra comentarios y líneas vacías
```bash
grep -v '^#' /etc/fstab | grep -v '^$'
```

#### Paso 6. Explica cada columna de una línea real
- dispositivo o UUID
- punto de montaje
- tipo de filesystem
- opciones
- dump
- pass

### Paso opcional de laboratorio seguro
Solo si tienes una partición o dispositivo de pruebas:
```bash
sudo mkdir -p /mnt/prueba
# sudo mount /dev/sdXN /mnt/prueba
# mount | grep /mnt/prueba
# sudo umount /mnt/prueba
```

### Qué deberías haber aprendido
- identificar discos y filesystems
- diferenciar `df` y `du`
- interpretar `/etc/fstab`
- entender montaje manual vs persistente

### Errores comunes
- intentar montar un dispositivo incorrecto
- olvidar desmontar
- editar `fstab` sin comprender la línea completa

---

## Lab 7 — Usuarios, grupos y autenticación

### Objetivo
Practicar:
- `whoami`
- `id`
- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`
- `useradd`
- `usermod`
- `passwd`
- `chage`

### Escenario
Vas a crear una cuenta de prueba y revisar cómo Linux almacena la información de usuarios.

### Pasos

#### Paso 1. Consulta tu identidad actual
```bash
whoami
id
```

---

#### Paso 2. Revisa tu entrada en passwd
```bash
grep "^$(whoami):" /etc/passwd
```

---

#### Paso 3. Revisa grupos
```bash
grep "$(whoami)" /etc/group
```

---

#### Paso 4. Crea un usuario de laboratorio
```bash
sudo useradd -m alumno_lpic
sudo passwd alumno_lpic
```

---

#### Paso 5. Añádelo a un grupo suplementario
```bash
sudo usermod -aG sudo alumno_lpic
```

> En algunas distros el grupo administrativo puede ser `wheel` en vez de `sudo`.

---

#### Paso 6. Consulta caducidad
```bash
sudo chage -l alumno_lpic
```

---

#### Paso 7. Revisa shadow con privilegios
```bash
sudo grep "^alumno_lpic:" /etc/shadow
```

---

#### Paso 8. Elimina el usuario al terminar
```bash
sudo userdel -r alumno_lpic
```

### Qué deberías haber aprendido
- cómo se representa un usuario en passwd y shadow
- diferencia entre grupo principal y suplementario
- cómo añadir a grupos sin sobrescribir otros

### Errores comunes
- olvidar `-a` en `usermod -aG`
- trabajar sobre un usuario real en lugar de uno de laboratorio
- intentar leer `shadow` sin privilegios

---

## Lab 8 — Shell, variables y scripting

### Objetivo
Practicar:
- `echo`
- `env`
- `export`
- `chmod`
- ejecución de scripts
- parámetros posicionales

### Escenario
Vas a construir scripts pequeños para automatizar tareas simples.

### Pasos

#### Paso 1. Crea el laboratorio
```bash
mkdir -p ~/lpic-labs/lab8
cd ~/lpic-labs/lab8
```

---

#### Paso 2. Revisa variables del entorno
```bash
echo $HOME
echo $PATH
echo $SHELL
```

---

#### Paso 3. Crea una variable propia
```bash
CURSO=LPIC1
echo $CURSO
export CURSO
bash -c 'echo $CURSO'
```

**Qué debes observar**
- tras `export`, la variable está disponible en la subshell

---

#### Paso 4. Crea un script simple
```bash
cat > info.sh <<'EOF'
#!/bin/bash
echo "Usuario: $USER"
echo "Directorio actual: $(pwd)"
echo "Fecha: $(date)"
EOF
```

---

#### Paso 5. Dale permisos y ejecútalo
```bash
chmod u+x info.sh
./info.sh
```

---

#### Paso 6. Crea un script con parámetros
```bash
cat > saludo.sh <<'EOF'
#!/bin/bash
echo "Script: $0"
echo "Argumentos recibidos: $#"
echo "Primer argumento: $1"
EOF
```

```bash
chmod u+x saludo.sh
./saludo.sh Angel
```

### Qué deberías haber aprendido
- diferencia entre variable local y exportada
- estructura mínima de un script shell
- uso de parámetros posicionales

### Errores comunes
- olvidar el permiso de ejecución
- romper el script por comillas mal cerradas
- pensar que `export` es necesario para toda variable

---

## Lab 9 — Cron, at y automatización

### Objetivo
Practicar:
- `crontab`
- `at`
- `atq`
- `atrm`

### Escenario
Vas a programar tareas repetitivas y tareas únicas.

### Pasos

#### Paso 1. Revisa tu crontab actual
```bash
crontab -l
```

> Si no existe, es normal en un entorno nuevo.

---

#### Paso 2. Añade una tarea temporal
Edita con:
```bash
crontab -e
```

Añade una línea como esta:
```cron
* * * * * date >> /tmp/lpic_cron.log
```

---

#### Paso 3. Comprueba que se ejecuta
```bash
tail -f /tmp/lpic_cron.log
```

---

#### Paso 4. Elimina la tarea al terminar
```bash
crontab -e
```
Borra la línea guardada.

---

#### Paso 5. Programa una tarea con `at`
```bash
at now + 2 minutes
```

Dentro del prompt de `at`, escribe:
```bash
touch /tmp/tarea_at_ok
```

Finaliza con `Ctrl+D`.

---

#### Paso 6. Lista tareas pendientes
```bash
atq
```

---

#### Paso 7. Comprueba el resultado o elimina la tarea
```bash
ls -l /tmp/tarea_at_ok
# o bien
# atrm NUMERO
```

### Qué deberías haber aprendido
- diferencia entre cron y at
- cómo comprobar que una tarea realmente se ejecuta
- necesidad de limpiar tareas temporales tras la práctica

### Errores comunes
- dejar tareas activas sin querer
- editar la crontab equivocada
- pensar que `at` sirve para tareas recurrentes

---

## Lab 10 — Logs, journal, red y seguridad básica

### Objetivo
Practicar:
- `/var/log`
- `tail`
- `journalctl`
- `ip`
- `ping`
- `host` / `dig` / `nslookup`
- `ss`
- `ssh`
- `sudo`

### Escenario
Vas a revisar el sistema como si estuvieras haciendo una comprobación básica de administración.

### Pasos

#### Paso 1. Revisa logs del sistema
```bash
ls /var/log
```

Busca logs de autenticación según tu distro:
```bash
ls /var/log/auth.log /var/log/secure 2>/dev/null
```

---

#### Paso 2. Mira las últimas líneas del log de autenticación disponible
```bash
tail -n 20 /var/log/auth.log 2>/dev/null
tail -n 20 /var/log/secure 2>/dev/null
```

---

#### Paso 3. Consulta journal del arranque
```bash
journalctl -b | tail -n 20
```

---

#### Paso 4. Consulta journal de un servicio
```bash
journalctl -u ssh 2>/dev/null | tail -n 20
journalctl -u sshd 2>/dev/null | tail -n 20
```

---

#### Paso 5. Revisa red básica
```bash
ip a
ip route
hostname
ss -tuln
```

---

#### Paso 6. Comprueba conectividad
```bash
ping -c 4 1.1.1.1
ping -c 4 openai.com
```

---

#### Paso 7. Revisa resolución DNS
```bash
host openai.com 2>/dev/null
dig openai.com 2>/dev/null | head
nslookup openai.com 2>/dev/null
```

---

#### Paso 8. Revisa configuración SSH
```bash
ls /etc/ssh
sudo grep -v '^#' /etc/ssh/sshd_config 2>/dev/null | grep -v '^$' | head
```

---

#### Paso 9. Comprueba si SSH está activo
```bash
systemctl status ssh 2>/dev/null
systemctl status sshd 2>/dev/null
```

### Qué deberías haber aprendido
- localizar logs útiles
- consultar journal en systems con systemd
- revisar conectividad y DNS por separado
- comprobar puertos y servicios
- ubicar configuración SSH

### Errores comunes
- confundir problema DNS con problema de conectividad general
- no adaptar `ssh` vs `sshd` según la distro
- asumir que el log de autenticación siempre tiene el mismo nombre

---

## Lab 11 — Repaso integrado de administración básica

### Objetivo
Combinar varias áreas del temario en un único flujo.

### Escenario
Vas a preparar una carpeta de trabajo, generar archivos, aplicar permisos, buscar contenido, comprimir resultados y revisar el sistema.

### Pasos

#### Paso 1. Crea estructura de proyecto
```bash
mkdir -p ~/lpic-labs/lab11/{docs,scripts,logs}
cd ~/lpic-labs/lab11
```

---

#### Paso 2. Genera archivos de ejemplo
```bash
echo "inventario del sistema" > docs/informe.txt
echo "echo Hola LPIC" > scripts/hola.sh
chmod u+x scripts/hola.sh
```

---

#### Paso 3. Revisa permisos
```bash
ls -l scripts docs
```

---

#### Paso 4. Busca archivos `.txt`
```bash
find . -name "*.txt"
```

---

#### Paso 5. Busca la palabra “inventario”
```bash
grep -rn "inventario" .
```

---

#### Paso 6. Comprime el proyecto
```bash
tar czf lab11_backup.tar.gz docs scripts logs
```

**Comprobación**
```bash
tar tf lab11_backup.tar.gz
```

---

#### Paso 7. Revisa espacio y estado del sistema
```bash
du -sh .
df -h
uptime
```

### Qué deberías haber aprendido
- combinar tareas de archivos, permisos, búsqueda y archivado
- revisar el resultado con comandos de verificación
- pensar como un administrador que valida cada paso

---

## Qué hacer después de completar estos labs

Si has terminado estos laboratorios y te sientes cómodo, deberías poder:

- moverte con soltura por el sistema
- manipular archivos y permisos sin dudar
- usar filtros de texto para extraer información
- revisar procesos y prioridades
- consultar paquetes y su relación con archivos
- entender almacenamiento y montajes
- administrar usuarios básicos
- crear scripts sencillos
- programar tareas
- revisar logs, red y servicios

## Recomendación de progreso

### Si aún dudas con comandos básicos
Repite:
- Lab 1
- Lab 2
- Lab 3

### Si dudas con administración del sistema
Repite:
- Lab 4
- Lab 6
- Lab 7
- Lab 10

### Si dudas con shell y automatización
Repite:
- Lab 8
- Lab 9

## Relación con el resto del proyecto

Este archivo encaja especialmente con:

- `10_ejercicios_practicos.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`
- `08_conceptos_clave_101.md`
- `09_conceptos_clave_102.md`

## Siguiente paso recomendado

El siguiente archivo natural del proyecto es:

- `12_chuleta_repaso_rapido.md`

Ese documento servirá para condensar todo en un material de repaso rápido, muy útil antes del examen o antes de rehacer laboratorios.
