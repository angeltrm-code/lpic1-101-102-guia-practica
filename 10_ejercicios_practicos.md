# 10 — Ejercicios prácticos (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Este archivo reúne **ejercicios prácticos por bloques**, pensados para entrenar la parte operativa de los exámenes 101 y 102.  
> Están orientados a práctica real en terminal, con un enfoque progresivo: **objetivo**, **tareas**, **pistas** y **comprobación**.

## Cómo usar este archivo

- Haz los ejercicios **en terminal**, no solo leyéndolos.
- Intenta resolver primero sin mirar la pista.
- Comprueba al final si el resultado es correcto.
- Si puedes, repítelos tanto en **Debian** como en una distro tipo **Rocky/Red Hat** cuando aplique.

---

## Bloque 1. Navegación y manejo básico de archivos
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md)

### Ejercicio 1.1 — Crear una estructura de trabajo
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `pwd`, `mkdir`, `cd`, `touch`, `ls`.

**Tareas**
1. Comprueba en qué directorio estás.
2. Crea una carpeta llamada `lpic-lab`.
3. Entra en ella.
4. Crea esta estructura:
   - `tema101`
   - `tema102`
   - `notas`
5. Dentro de `notas`, crea los archivos:
   - `dia1.txt`
   - `dia2.txt`

**Pistas**
- Usa `pwd`
- Usa `mkdir -p`
- Usa `touch`

**Comprobación**
- `ls -R` debe mostrar la jerarquía creada.

---

### Ejercicio 1.2 — Copiar, mover y eliminar
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `cp`, `mv`, `rm`, `rmdir`.

**Tareas**
1. Copia `dia1.txt` a `tema101`.
2. Renombra la copia como `introduccion.txt`.
3. Mueve `dia2.txt` a `tema102`.
4. Elimina `introduccion.txt`.
5. Intenta borrar un directorio vacío con `rmdir`.

**Pistas**
- Recuerda que `mv` también renombra.
- `rmdir` solo borra directorios vacíos.

**Comprobación**
- Usa `find .` para revisar el resultado final.

---

### Ejercicio 1.3 — Rutas absolutas y relativas
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** distinguir rutas absolutas y relativas.

**Tareas**
1. Sitúate dentro de `tema101`.
2. Crea un archivo llamado `rutas.txt`.
3. Copia ese archivo a `../tema102/`.
4. Desde `tema101`, muestra el contenido de `../tema102/rutas.txt`.
5. Ahora muestra ese mismo archivo usando una ruta absoluta.

**Comprobación**
- Debes ser capaz de explicar qué comando usó ruta relativa y cuál absoluta.

---

## Bloque 2. Visualización y edición de texto
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md)

### Ejercicio 2.1 — Crear y leer archivos
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `echo`, redirecciones, `cat`, `less`, `head`, `tail`.

**Tareas**
1. Crea un archivo `usuarios.txt` con varias líneas de texto.
2. Añade dos líneas más sin sobrescribir el contenido.
3. Muestra el contenido completo.
4. Muestra solo las primeras 3 líneas.
5. Muestra solo las últimas 2 líneas.

**Pistas**
- `>`
- `>>`
- `head -n`
- `tail -n`

**Comprobación**
- El archivo debe conservar todas las líneas.

---

### Ejercicio 2.2 — Editar con un editor
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** abrir, modificar y guardar con `nano` o `vi`.

**Tareas**
1. Abre `usuarios.txt` con el editor que prefieras.
2. Añade una línea indicando la fecha de práctica.
3. Guarda los cambios.
4. Sal del editor.
5. Verifica que la línea existe.

**Comprobación**
- Debes poder guardar y salir sin ayuda externa.

---

## Bloque 3. Filtros y procesamiento de texto
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md)

### Ejercicio 3.1 — Buscar información en `/etc/passwd`
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `grep`, `cut`, `awk`, `wc`.

**Tareas**
1. Busca la línea correspondiente al usuario `root`.
2. Muestra solo la primera columna de `/etc/passwd`.
3. Muestra usuario y shell por defecto.
4. Cuenta cuántas líneas tiene el archivo.

**Pistas**
- `grep root /etc/passwd`
- `cut -d: -f1`
- `awk -F:`
- `wc -l`

**Comprobación**
- Debes entender qué representa cada campo separado por `:`.

---

### Ejercicio 3.2 — Excluir comentarios
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** usar `grep -v`.

**Tareas**
1. Muestra el contenido de `/etc/fstab`.
2. Filtra las líneas comentadas.
3. Filtra además líneas vacías si existen.

**Pistas**
- `grep -v '^#'`
- Puedes encadenar con otra tubería.

**Comprobación**
- La salida final debe mostrar solo entradas útiles.

---

### Ejercicio 3.3 — Ordenar y contar duplicados
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `sort`, `uniq`, `tr`.

**Tareas**
1. Crea un archivo con varias palabras repetidas, una por línea.
2. Ordénalo.
3. Cuenta cuántas veces aparece cada palabra.
4. Convierte una línea de texto en mayúsculas.

**Comprobación**
- Debes obtener un conteo correcto de duplicados consecutivos.

---

## Bloque 4. Búsqueda de archivos
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md)

### Ejercicio 4.1 — Buscar por nombre y tipo
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `find`.

**Tareas**
1. Busca todos los archivos `.conf` dentro de `/etc`.
2. Busca solo directorios dentro de tu carpeta de laboratorio.
3. Busca archivos propiedad de tu usuario dentro de tu home.

**Pistas**
- `find /etc -name "*.conf"`
- `find . -type d`
- `find ~ -user tu_usuario`

---

### Ejercicio 4.2 — Ejecutar acciones con `find`
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** usar `-exec`.

**Tareas**
1. Crea varios archivos `.tmp` en tu laboratorio.
2. Localízalos con `find`.
3. Elimínalos usando `-exec rm`.
4. Verifica que ya no existen.

**Qué debes recordar**
- Esta forma aparece mucho en ejercicios y preguntas LPIC.

---

## Bloque 5. Permisos, propiedad y enlaces
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md)

### Ejercicio 5.1 — Permisos básicos
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `chmod`.

**Tareas**
1. Crea un script llamado `saludo.sh`.
2. Escribe una línea que muestre “Hola LPIC”.
3. Revisa sus permisos iniciales.
4. Dale permiso de ejecución al propietario.
5. Ejecuta el script.

**Pistas**
- `chmod u+x saludo.sh`

**Comprobación**
- Debe ejecutarse con `./saludo.sh`.

---

### Ejercicio 5.2 — Permisos numéricos
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** interpretar y aplicar permisos octales.

**Tareas**
1. Crea un archivo `privado.txt`.
2. Asigna permisos `600`.
3. Crea un directorio `scripts`.
4. Asigna permisos `755`.
5. Explica qué significan esos permisos.

**Comprobación**
- Usa `ls -l` para verificar.

---

### Ejercicio 5.3 — Propietario y grupo
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `chown` y `chgrp`.

**Tareas**
1. Consulta el propietario y grupo de un archivo.
2. Si tienes permisos suficientes, cambia el grupo del archivo.
3. Si estás en una VM de laboratorio con sudo, cambia propietario y grupo de forma conjunta.

**Comprobación**
- Usa `ls -l`.

---

### Ejercicio 5.4 — Enlaces duros y simbólicos
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** diferenciar `ln` y `ln -s`.

**Tareas**
1. Crea un archivo llamado `original.txt`.
2. Crea un enlace duro.
3. Crea un enlace simbólico.
4. Observa diferencias con `ls -l`.
5. Borra el archivo original y revisa qué pasa con cada enlace.

**Qué debes aprender**
- El enlace simbólico puede quedar roto.
- El enlace duro se comporta de forma distinta.

---

## Bloque 6. Procesos y prioridades
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [07_opciones_frecuentes.md](07_opciones_frecuentes.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md)

### Ejercicio 6.1 — Observar procesos
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** practicar `ps`, `top`, `uptime`.

**Tareas**
1. Muestra tus procesos actuales.
2. Muestra todos los procesos del sistema.
3. Abre `top` y observa consumo.
4. Consulta el tiempo encendido del sistema.

**Comprobación**
- Debes distinguir PID, usuario, CPU y memoria.

---

### Ejercicio 6.2 — Lanzar un proceso en segundo plano
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** entender foreground y background.

**Tareas**
1. Ejecuta un comando que tarde un poco, por ejemplo `sleep 300`.
2. Envíalo a segundo plano.
3. Verifica que sigue existiendo.
4. Finalízalo con `kill`.

**Pistas**
- Usa `&`
- Usa `ps`
- Usa `kill`

---

### Ejercicio 6.3 — Prioridades
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `nice` y `renice`.

**Tareas**
1. Lanza un proceso con prioridad modificada.
2. Consulta su PID.
3. Cambia su prioridad con `renice`.
4. Comprueba el cambio.

**Qué debes recordar**
- Un valor nice más alto implica menor prioridad.

---

## Bloque 7. Gestión de paquetes
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md)

### Ejercicio 7.1 — Debian
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `apt` y `dpkg`.

**Tareas**
1. Actualiza índices de paquetes.
2. Busca un paquete, por ejemplo `tree`.
3. Instálalo.
4. Comprueba qué paquete contiene `/bin/ls`.
5. Lista paquetes instalados relacionados con `ssh`.

**Pistas**
- `apt update`
- `apt search`
- `dpkg -S`
- `dpkg -l`

---

### Ejercicio 7.2 — Rocky / Red Hat
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `rpm`, `yum` o `dnf`.

**Tareas**
1. Lista todos los paquetes instalados.
2. Consulta si está instalado `bash`.
3. Muestra información del paquete `bash`.
4. Lista los archivos que pertenecen al paquete `bash`.

**Pistas**
- `rpm -qa`
- `rpm -q bash`
- `rpm -qi bash`
- `rpm -ql bash`

---

## Bloque 8. Discos, particiones y montaje
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md)

### Ejercicio 8.1 — Identificar discos y sistemas de archivos
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `lsblk`, `blkid`, `df`, `du`.

**Tareas**
1. Lista discos y particiones.
2. Muestra UUID y tipos de filesystem.
3. Comprueba espacio libre.
4. Comprueba el tamaño de `/var/log`.

**Comprobación**
- Debes diferenciar entre tamaño de particiones y tamaño usado por directorios.

---

### Ejercicio 8.2 — Montaje manual
**Dificultad:** Avanzado
**Tiempo estimado:** 20-40 min
**Objetivo:** practicar `mount` y `umount`.

**Tareas**
1. Crea un punto de montaje en `/mnt/prueba`.
2. Si tienes una partición o imagen de laboratorio disponible, móntala.
3. Verifica que aparece montada.
4. Desmóntala.

**Qué debes recordar**
- No desmontes nada crítico del sistema real.
- Haz esto en VM o con medios de prueba.

---

### Ejercicio 8.3 — Revisar `/etc/fstab`
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** interpretar montajes persistentes.

**Tareas**
1. Abre `/etc/fstab`.
2. Identifica cada columna.
3. Explica qué significa:
   - dispositivo o UUID
   - punto de montaje
   - tipo
   - opciones
   - dump
   - pass

**Comprobación**
- Debes poder explicar el propósito de cada campo.

---

## Bloque 9. Usuarios, grupos y autenticación
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md)

### Ejercicio 9.1 — Información de usuarios
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** practicar `id`, `whoami`, `/etc/passwd`, `/etc/group`.

**Tareas**
1. Consulta tu usuario actual.
2. Muestra tu UID y grupos.
3. Busca tu entrada en `/etc/passwd`.
4. Busca tus grupos en `/etc/group`.

---

### Ejercicio 9.2 — Crear y modificar usuarios
**Dificultad:** Avanzado
**Tiempo estimado:** 20-40 min
**Objetivo:** practicar `useradd`, `passwd`, `usermod`, `userdel`.

**Tareas**
1. Crea un usuario de prueba con home.
2. Asígnale contraseña.
3. Añádelo a un grupo suplementario.
4. Consulta su caducidad con `chage -l`.
5. Elimínalo al terminar.

**Qué debes recordar**
- Hazlo en VM o entorno de laboratorio.

---

### Ejercicio 9.3 — Revisar shadow y shells
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** relacionar autenticación y entorno.

**Tareas**
1. Revisa `/etc/shadow` con privilegios.
2. Revisa `/etc/shells`.
3. Explica por qué `/etc/shadow` tiene permisos restrictivos.

---

## Bloque 10. Shell y scripting
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md)

### Ejercicio 10.1 — Variables y entorno
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** practicar `echo`, `env`, `export`.

**Tareas**
1. Muestra las variables `HOME`, `PATH` y `SHELL`.
2. Crea una variable llamada `CURSO=LPIC1`.
3. Muéstrala.
4. Expórtala y comprueba que sigue disponible en una subshell.

---

### Ejercicio 10.2 — Script simple
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** crear un script funcional.

**Tareas**
1. Crea un script `info.sh`.
2. Haz que muestre:
   - usuario actual
   - directorio actual
   - fecha
3. Dale permisos de ejecución.
4. Ejecútalo.

**Comprobación**
- Debe funcionar con `./info.sh`.

---

### Ejercicio 10.3 — Parámetros posicionales
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** usar `$1`, `$2`, `$#`, `$0`.

**Tareas**
1. Crea un script que reciba un nombre.
2. Muestre:
   - nombre del script
   - número de argumentos
   - primer argumento
3. Ejecútalo pasando un valor.

**Comprobación**
- Debes entender qué representa cada variable especial.

---

## Bloque 11. Tareas programadas
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md), [11_labs_guiados.md](11_labs_guiados.md)

### Ejercicio 11.1 — Cron de usuario
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** practicar `crontab -e` y `crontab -l`.

**Tareas**
1. Crea una tarea que escriba la fecha en un archivo de tu home cada minuto.
2. Lista la crontab.
3. Espera o verifica que se ejecuta.
4. Elimínala al terminar.

**Qué debes recordar**
- En una máquina real, no dejes tareas innecesarias activas.

---

### Ejercicio 11.2 — At
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** programar una tarea única.

**Tareas**
1. Programa una orden que cree un archivo dentro de unos minutos.
2. Lista las tareas pendientes.
3. Comprueba que se ejecuta o elimínala.

---

## Bloque 12. Logs y journal
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md), [11_labs_guiados.md](11_labs_guiados.md)

### Ejercicio 12.1 — Revisar logs clásicos
**Dificultad:** Básico
**Tiempo estimado:** 10-20 min
**Objetivo:** localizar registros del sistema.

**Tareas**
1. Lista el contenido de `/var/log`.
2. Localiza logs de autenticación.
3. Muestra las últimas líneas del log correspondiente.
4. Sigue el log en tiempo real durante unos segundos.

---

### Ejercicio 12.2 — Journal de systemd
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** usar `journalctl`.

**Tareas**
1. Muestra logs del arranque actual.
2. Muestra logs de un servicio concreto, por ejemplo `ssh` o `NetworkManager`.
3. Busca mensajes recientes detallados.

**Pistas**
- `journalctl -b`
- `journalctl -u ssh`
- `journalctl -xe`

---

## Bloque 13. Red y resolución de problemas
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md)

### Ejercicio 13.1 — Información básica de red
**Dificultad:** Básico
**Tiempo estimado:** 5-10 min
**Objetivo:** practicar `ip`, `hostname`, `ss`.

**Tareas**
1. Muestra interfaces y direcciones IP.
2. Muestra la tabla de rutas.
3. Consulta el hostname.
4. Muestra puertos en escucha.

---

### Ejercicio 13.2 — Conectividad y DNS
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** distinguir fallos de red y DNS.

**Tareas**
1. Haz ping a una IP pública.
2. Haz ping a un nombre de dominio.
3. Usa `host`, `dig` o `nslookup` con ese dominio.
4. Explica qué significaría:
   - llegar a la IP pero no al dominio
   - no llegar ni a la IP

---

### Ejercicio 13.3 — Configuración persistente
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** reconocer archivos de red.

**Tareas**
1. Revisa `/etc/hosts`.
2. Revisa `/etc/resolv.conf`.
3. En Debian, revisa si existe `/etc/network/interfaces`.
4. En Rocky/Red Hat, revisa rutas de configuración de red del sistema.

**Comprobación**
- Debes saber para qué sirve cada archivo.

---

## Bloque 14. Seguridad básica
**Qué deberías haber leído antes:** [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md), [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md)

### Ejercicio 14.1 — SSH
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** reconocer cliente y configuración.

**Tareas**
1. Revisa `/etc/ssh/ssh_config`.
2. Si existe y tienes permisos, revisa `/etc/ssh/sshd_config`.
3. Comprueba si el servicio SSH está activo.
4. Si tienes otra VM disponible, prueba una conexión SSH.

---

### Ejercicio 14.2 — sudo y privilegios
**Dificultad:** Medio
**Tiempo estimado:** 10-20 min
**Objetivo:** entender delegación de privilegios.

**Tareas**
1. Ejecuta un comando con `sudo`.
2. Revisa si existe `/etc/sudoers.d/`.
3. Explica por qué no se edita `sudoers` de cualquier manera.

---

### Ejercicio 14.3 — GPG o cifrado básico
**Dificultad:** Avanzado
**Tiempo estimado:** 20-40 min
**Objetivo:** practicar cifrado sencillo.

**Tareas**
1. Crea un archivo de texto con información de prueba.
2. Cífralo con `gpg -c`.
3. Descífralo.
4. Explica la diferencia entre cifrado y hash.

---

## Bloque 15. Repaso integrado tipo LPIC
**Qué deberías haber leído antes:** [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md), [08_conceptos_clave_101.md](08_conceptos_clave_101.md), [09_conceptos_clave_102.md](09_conceptos_clave_102.md), [11_labs_guiados.md](11_labs_guiados.md)

### Ejercicio 15.1 — Caso completo de administración básica
**Dificultad:** Avanzado
**Tiempo estimado:** 20-40 min
**Objetivo:** combinar varias áreas.

**Escenario**
Debes preparar un pequeño entorno de trabajo para un usuario nuevo.

**Tareas**
1. Crea un directorio de proyecto con varias subcarpetas.
2. Crea archivos de trabajo dentro.
3. Asigna permisos adecuados.
4. Busca archivos `.txt`.
5. Comprímelos en un `.tar.gz`.
6. Revisa el espacio ocupado.
7. Programa una tarea para listar el contenido del proyecto en un log.

**Qué entrenas**
- archivos
- permisos
- búsqueda
- compresión
- cron
- revisión de resultados

---

### Ejercicio 15.2 — Diagnóstico de sistema
**Dificultad:** Avanzado
**Tiempo estimado:** 20-40 min
**Objetivo:** revisar sistema como lo haría un admin junior.

**Tareas**
1. Consulta kernel, arquitectura y CPU.
2. Comprueba RAM y swap.
3. Lista discos y montajes.
4. Revisa uptime y carga.
5. Mira procesos activos.
6. Revisa logs recientes.
7. Comprueba conectividad de red.

**Qué entrenas**
- visión global del sistema
- comandos esenciales de administración

---

## Bloque 16. Autoevaluación
**Qué deberías haber leído antes:** [10_ejercicios_practicos.md](10_ejercicios_practicos.md), [11_labs_guiados.md](11_labs_guiados.md), [13_checklist_preparacion_lpic1.md](13_checklist_preparacion_lpic1.md)

Después de resolver los ejercicios, deberías poder responder “sí” a estas preguntas:

- ¿Sé moverme por el sistema usando rutas absolutas y relativas?
- ¿Sé crear, copiar, mover y borrar archivos sin dudar?
- ¿Sé buscar texto en archivos del sistema?
- ¿Sé usar `find` con filtros básicos?
- ¿Sé interpretar permisos y cambiarlos?
- ¿Sé distinguir un enlace duro de uno simbólico?
- ¿Sé consultar y finalizar procesos?
- ¿Sé usar `apt`/`dpkg` y reconocer `rpm`/`yum`/`dnf`?
- ¿Sé identificar discos, particiones y montajes?
- ¿Sé interpretar `/etc/fstab`?
- ¿Sé consultar usuarios, grupos y shells?
- ¿Sé crear un script sencillo?
- ¿Sé programar una tarea con cron o at?
- ¿Sé revisar logs y journal?
- ¿Sé diferenciar un problema de conectividad de uno de DNS?
- ¿Sé explicar el uso de `sudo`, SSH y cifrado básico?

---

## Bloque 17. Recomendación de uso dentro del proyecto
**Qué deberías haber leído antes:** [10_ejercicios_practicos.md](10_ejercicios_practicos.md), [11_labs_guiados.md](11_labs_guiados.md), [12_chuleta_repaso_rapido.md](12_chuleta_repaso_rapido.md)

Este archivo encaja muy bien después de:

- `06_comandos_con_sintaxis_y_ejemplos.md`
- `07_opciones_frecuentes.md`
- `08_conceptos_clave_101.md`
- `09_conceptos_clave_102.md`

## Siguiente paso recomendado

El siguiente archivo natural del proyecto es:

- `11_labs_guiados.md`

Ese documento puede transformar estos ejercicios en **mini laboratorios paso a paso**, más largos y totalmente reproducibles.
