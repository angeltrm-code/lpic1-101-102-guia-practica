# 08 — Conceptos clave 101 (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Este archivo reúne los **conceptos fundamentales del examen 101**, explicados de forma clara y orientados al estudio práctico.  
> La idea es complementar los archivos de comandos, rutas y matrices con la **base teórica** que suele aparecer en preguntas de examen y en laboratorios.

## Cómo usar este archivo

- Léelo como si fuera un **resumen teórico guiado**.
- No busca sustituir la práctica, sino darte el marco mental correcto.
- Cuando aparezca un concepto, relaciónalo con:
  - un comando
  - un fichero
  - una situación real de administración

---

## 1. Arquitectura del sistema

### Qué significa “arquitectura” en Linux
La arquitectura describe el tipo de procesador y el modelo de ejecución para el que está preparado el sistema operativo.

Ejemplos comunes:
- `x86_64`
- `amd64`
- `i386`
- `aarch64`

**Qué debes entender**
- Un kernel y sus binarios deben ser compatibles con la arquitectura del hardware.
- La arquitectura influye en:
  - los paquetes instalables
  - el rendimiento
  - la compatibilidad con software y virtualización

---

### CPU, núcleos e hilos
Un procesador puede tener:
- **una o varias CPUs físicas**
- **varios núcleos por CPU**
- **varios hilos de ejecución por núcleo**

**Idea importante**
- Más núcleos permiten más trabajo en paralelo.
- Linux expone esta información con herramientas como `lscpu`, `/proc/cpuinfo` o `nproc`.

---

### Tipos de hardware que conviene reconocer
En LPIC-1 debes saber identificar, al menos a nivel conceptual:
- CPU
- RAM
- discos HDD/SSD/NVMe
- particiones
- interfaces de red
- buses y dispositivos
- módulos del kernel
- controladores

**Qué debes recordar**
- Linux representa muchos dispositivos como archivos dentro de `/dev`.
- Parte de la información del hardware también se expone en `/proc` y `/sys`.

---

### IRQ, DMA e I/O
Son conceptos clásicos de hardware que siguen apareciendo en temarios:

- **IRQ (Interrupt Request):** mecanismo para que un dispositivo llame la atención de la CPU.
- **DMA (Direct Memory Access):** permite a ciertos dispositivos transferir datos a memoria sin cargar tanto a la CPU.
- **I/O ports:** mecanismos de comunicación entre CPU y dispositivos.

**Qué debes recordar**
- En Linux puedes consultar información histórica o de diagnóstico en:
  - `/proc/interrupts`
  - `/proc/dma`
  - `/proc/ioports`

---

## 2. BIOS, UEFI y proceso de arranque

### BIOS vs UEFI
Son firmware que inicializan el hardware y lanzan el proceso de arranque.

#### BIOS
- Sistema tradicional.
- Suele asociarse a discos con tabla de particiones MBR.

#### UEFI
- Sistema moderno.
- Suele trabajar con GPT.
- Permite partición EFI (`ESP`) y mecanismos más avanzados de arranque.

**Qué debes entender**
- Ambos arrancan el sistema, pero UEFI es más moderno y flexible.
- En equipos actuales es habitual usar UEFI + GPT.

---

### Secuencia general de arranque
De forma simplificada:

1. Firmware (BIOS/UEFI)
2. Cargador de arranque (GRUB, por ejemplo)
3. Kernel Linux
4. `initramfs` / `initrd`
5. Proceso `init` o `systemd`
6. Servicios, objetivos y login

**Qué debes recordar**
- El arranque no termina al cargar el kernel.
- Aún hay que montar raíz, arrancar servicios y preparar el entorno del sistema.

---

### Kernel
El kernel es el núcleo del sistema operativo.

**Funciones principales**
- gestionar CPU
- memoria
- procesos
- dispositivos
- sistemas de archivos
- red
- seguridad básica del sistema

**Idea clave**
- El kernel actúa como mediador entre el hardware y el software de usuario.

---

### Initramfs / initrd
Es una imagen de arranque temporal cargada junto al kernel.

**Para qué sirve**
- cargar módulos necesarios
- detectar hardware
- montar el sistema raíz real
- preparar el entorno inicial

**Qué debes recordar**
- Si el kernel no puede encontrar o montar la raíz, el arranque falla.
- `initramfs` es muy importante cuando hay drivers, LVM, RAID o cifrado implicados.

---

### GRUB
GRUB es un gestor de arranque muy común en Linux.

**Qué hace**
- presenta menú de arranque
- permite elegir kernel o sistema
- pasa parámetros al kernel
- inicia el sistema operativo

**Archivos clave**
- `/boot/grub/grub.cfg`
- `/etc/default/grub`

**Qué debes recordar**
- El archivo `grub.cfg` suele generarse automáticamente.
- Normalmente editas ajustes en `/etc/default/grub` y luego regeneras la configuración.

---

## 3. Runlevels, targets y modos de arranque

### Runlevels
Modelo clásico de SysVinit para definir estados del sistema.

Runlevels típicos:
- `0`: apagado
- `1`: modo monousuario
- `3`: modo multiusuario en texto
- `5`: modo multiusuario con entorno gráfico
- `6`: reinicio

**Qué debes recordar**
- Es un modelo clásico, muy importante para entender documentación antigua y preguntas teóricas.

---

### Targets en systemd
Systemd sustituye los runlevels por **targets**.

Equivalencias frecuentes:
- `rescue.target` ≈ runlevel 1
- `multi-user.target` ≈ runlevel 3
- `graphical.target` ≈ runlevel 5
- `reboot.target` ≈ runlevel 6

**Qué debes entender**
- Un target es un conjunto lógico de servicios y dependencias.
- Permite definir en qué estado debe iniciar el sistema.

---

### Modo monousuario o rescate
Modo de mantenimiento con pocos servicios, usado para reparación o administración crítica.

**Cuándo se usa**
- recuperación de contraseñas
- reparación de ficheros
- mantenimiento del sistema
- diagnóstico

---

## 4. Gestión de paquetes y software

### Qué es un paquete
Un paquete contiene software y metadatos necesarios para:
- instalar
- actualizar
- eliminar
- verificar dependencias
- registrar archivos instalados

---

### Diferencia entre paquetes y fuentes
- **Paquete binario:** ya compilado y listo para instalar.
- **Código fuente:** requiere compilación antes de usarlo.

**Qué debes recordar**
- LPIC pregunta tanto por instalación binaria como por comprensión general del software compilado.

---

### Formatos principales
#### Debian
- paquetes `.deb`
- herramientas como `dpkg` y `apt`

#### RPM
- paquetes `.rpm`
- herramientas como `rpm`, `yum` y `dnf`

---

### Dependencias
Una dependencia es otro paquete o librería que un programa necesita para funcionar.

**Qué debes recordar**
- Herramientas de alto nivel como `apt`, `yum` o `dnf` resuelven dependencias.
- Herramientas de bajo nivel como `dpkg` o `rpm` no siempre lo hacen automáticamente.

---

### Librerías compartidas
Son bibliotecas reutilizables por varios programas.

**Ventajas**
- ahorro de espacio
- actualización centralizada
- reutilización de código

**Qué debes entender**
- Un programa puede fallar si no encuentra una librería compartida necesaria.
- La gestión de estas librerías forma parte del temario.

---

## 5. Virtualización básica

### Qué es virtualizar
Virtualizar es ejecutar sistemas o recursos simulados sobre una capa de software.

Ejemplos:
- una máquina virtual Linux dentro de otra máquina
- varios servidores virtuales en el mismo hardware físico

---

### Hipervisor
Es la capa que permite crear y ejecutar máquinas virtuales.

#### Tipo 1
Corre directamente sobre el hardware.

#### Tipo 2
Corre sobre un sistema operativo anfitrión.

**Ejemplos**
- VirtualBox: tipo 2
- KVM: se integra con Linux de forma muy eficiente

---

### Qué debes entender en LPIC-1
No se suele pedir un nivel profundo de administración de virtualización, pero sí:
- entender qué es una VM
- reconocer el concepto de anfitrión e invitado
- saber que existen herramientas para detectar si Linux está virtualizado

---

## 6. Línea de comandos y shell

### Qué es la shell
La shell es el intérprete de comandos.

**Qué hace**
- recibe órdenes del usuario
- las interpreta
- ejecuta comandos o scripts
- gestiona variables, tuberías y redirecciones

**Ejemplos**
- `bash`
- `sh`
- `zsh`

---

### Diferencia entre shell y terminal
- **Terminal:** interfaz donde escribes.
- **Shell:** programa que interpreta lo que escribes.

---

### Ruta absoluta y ruta relativa
#### Ruta absoluta
Empieza por `/` y se interpreta desde la raíz del sistema.

Ejemplo:
```bash
/etc/ssh/sshd_config
```

#### Ruta relativa
Se interpreta desde el directorio actual.

Ejemplo:
```bash
./script.sh
../documento.txt
```

**Qué debes recordar**
- Es un concepto básico y esencial para casi todo el examen.

---

### Comandos internos y externos
#### Internos
Forman parte de la shell.

Ejemplos:
- `cd`
- `echo`
- `alias`

#### Externos
Son ejecutables del sistema.

Ejemplos:
- `ls`
- `cp`
- `grep`

---

## 7. Entrada, salida, redirecciones y tuberías

### Entrada estándar, salida estándar y error estándar
Todo proceso trabaja normalmente con tres flujos:
- **stdin**: entrada estándar
- **stdout**: salida estándar
- **stderr**: salida de error

**Qué debes recordar**
- Son fundamentales para entender redirecciones y pipelines.

---

### Redirección
Permite enviar salida o errores a un archivo o leer desde uno.

Ejemplos:
- `>` sobrescribe salida
- `>>` añade al final
- `2>` redirige errores

---

### Tuberías
Una tubería (`|`) envía la salida de un comando a la entrada del siguiente.

**Ejemplo mental**
- un comando produce datos
- otro comando los filtra
- otro los ordena o muestra

**Qué debes entender**
- Linux favorece combinar herramientas pequeñas en lugar de usar una sola herramienta enorme.

---

## 8. Procesamiento de texto

### Filosofía Unix
Muchas utilidades Unix hacen una sola cosa, pero la hacen bien.

Ejemplos:
- `grep` busca
- `sort` ordena
- `cut` extrae
- `awk` procesa columnas
- `sed` transforma texto

**Qué debes recordar**
- LPIC valora mucho esta filosofía.
- No solo importa memorizar comandos, sino entender cómo se combinan.

---

### Expresiones regulares
Son patrones para buscar o validar texto.

Ejemplos:
- buscar líneas que empiecen por una palabra
- encontrar direcciones IP
- filtrar comentarios o usuarios

**Qué debes recordar**
- Hay expresiones básicas y extendidas.
- `grep`, `sed` y `awk` las usan con frecuencia.

---

## 9. Procesos, prioridades y señales

### Qué es un proceso
Es un programa en ejecución.

**Qué debes entender**
- Un mismo programa puede tener varios procesos.
- Cada proceso tiene un PID.
- Linux permite observarlos, priorizarlos y señalarlos.

---

### Proceso padre e hijo
Cuando un proceso crea otro, el original es el **padre** y el nuevo es el **hijo**.

**Qué debes recordar**
- Muchos servicios generan procesos hijos.
- Es importante para entender árboles de procesos.

---

### Foreground y background
#### Foreground
El proceso ocupa tu terminal.

#### Background
El proceso sigue ejecutándose sin bloquear la terminal.

---

### Prioridades y “nice”
Linux usa prioridades para repartir tiempo de CPU.

**Qué debes recordar**
- Un valor `nice` más alto suele significar menor prioridad.
- Puedes ajustar la prioridad al lanzar un proceso o después.

---

### Señales
Una señal es una forma de comunicarse con un proceso.

Ejemplos clásicos:
- `SIGTERM`: finalización ordenada
- `SIGKILL`: finalización forzada
- `SIGHUP`: recarga o cierre de sesión, según contexto

**Qué debes entender**
- No todas las señales “matan”; algunas notifican o piden recarga.

---

## 10. Particiones y tablas de partición

### Qué es una partición
Es una división lógica de un disco.

**Para qué sirve**
- separar sistema, datos, swap, etc.
- organizar el uso del disco
- facilitar administración y recuperación

---

### MBR
Esquema tradicional de particionado.

**Características**
- límite más antiguo
- hasta 4 particiones primarias
- menor flexibilidad que GPT

---

### GPT
Esquema moderno, habitual con UEFI.

**Ventajas**
- más robusto
- más flexible
- soporta más particiones
- mejor para discos modernos

---

### Partición primaria, extendida y lógica
Conceptos clásicos ligados sobre todo a MBR.

- **Primaria:** partición directa usable.
- **Extendida:** contenedor para lógicas.
- **Lógica:** partición dentro de la extendida.

**Qué debes recordar**
- En GPT esta distinción deja de tener la misma importancia.

---

## 11. Sistemas de archivos

### Qué es un sistema de archivos
Es la estructura lógica que organiza cómo se almacenan archivos y directorios.

Ejemplos:
- `ext4`
- `xfs`
- `btrfs`
- `vfat`

---

### Formatear
Formatear es crear un sistema de archivos sobre una partición o dispositivo.

**Qué debes entender**
- Formatear prepara el espacio para guardar datos.
- Normalmente destruye el contenido previo.

---

### Montar
Montar significa hacer accesible un sistema de archivos dentro del árbol de directorios.

**Idea clave**
- En Linux, los discos no “aparecen” automáticamente como letras.
- Se montan en un punto como `/mnt`, `/media` o cualquier ruta adecuada.

---

### Desmontar
Desmontar significa separar el sistema de archivos del árbol del sistema.

**Qué debes recordar**
- Antes de quitar un dispositivo, conviene desmontarlo correctamente.

---

### Integridad del sistema de archivos
Se refiere a que la estructura y metadatos del filesystem estén consistentes.

**Qué puede afectar a la integridad**
- apagados bruscos
- errores de disco
- corrupción
- fallos durante escritura

---

## 12. Inodos, enlaces y metadatos

### Inodo
Es una estructura que guarda metadatos sobre un archivo:
- permisos
- propietario
- tamaño
- fechas
- punteros a bloques de datos

**Qué debes recordar**
- El nombre del archivo no es el inodo.
- El sistema relaciona nombre e inodo a través de directorios.

---

### Enlace duro
Es otra entrada de directorio que apunta al mismo inodo.

**Consecuencias**
- comparte contenido y metadatos
- no es simplemente un “acceso directo”
- normalmente no cruza sistemas de archivos

---

### Enlace simbólico
Es un archivo especial que apunta por nombre a otra ruta.

**Qué debes recordar**
- Es más flexible.
- Puede apuntar a otras rutas o incluso quedar roto si el destino desaparece.

---

## 13. Permisos y propiedad

### Propietario, grupo y otros
Cada archivo tiene permisos para:
- **usuario propietario**
- **grupo**
- **otros**

---

### Permisos básicos
- `r`: lectura
- `w`: escritura
- `x`: ejecución

**Qué debes entender**
- Su significado cambia ligeramente según sea archivo o directorio.

#### En archivos
- `r`: leer contenido
- `w`: modificar
- `x`: ejecutar

#### En directorios
- `r`: listar contenido
- `w`: crear/borrar entradas si además se permite acceso
- `x`: atravesar o entrar en el directorio

---

### Notación simbólica y octal
#### Simbólica
Ejemplo:
```bash
u+x
g-w
o-r
```

#### Octal
Ejemplo:
- `644`
- `755`
- `700`

**Qué debes recordar**
- Debes saber convertir mentalmente casos típicos.

---

### Permisos especiales
#### SUID
Cuando se ejecuta un archivo, corre con permisos del propietario.

#### SGID
Puede hacer que un ejecutable use el grupo del archivo o que un directorio herede grupo.

#### Sticky bit
En directorios compartidos, evita que usuarios borren archivos de otros si no son propietarios.

**Ejemplo típico**
- `/tmp`

---

### Umask
La umask define qué permisos se restringen por defecto al crear archivos o directorios.

**Qué debes recordar**
- No asigna permisos directamente.
- Actúa restando permisos por defecto.

---

## 14. FHS: jerarquía del sistema de archivos

### Qué es FHS
FHS significa **Filesystem Hierarchy Standard**.

Define una estructura estándar para organizar directorios en Linux.

---

### Directorios esenciales que debes reconocer
- `/`
- `/bin`
- `/sbin`
- `/etc`
- `/home`
- `/root`
- `/var`
- `/tmp`
- `/usr`
- `/opt`
- `/boot`
- `/dev`
- `/proc`
- `/sys`
- `/mnt`
- `/media`
- `/srv`

**Qué debes recordar**
- LPIC pregunta bastante por la función de estas rutas.
- No basta con conocer el nombre: debes saber **qué tipo de contenido va en cada una**.

---

## 15. Búsqueda y localización de archivos

### Buscar un archivo no es lo mismo que identificarlo
Hay varias necesidades diferentes:
- encontrar por nombre
- saber de qué paquete procede
- conocer su tipo
- localizar ejecutables o documentación

**Qué debes entender**
- Por eso existen herramientas distintas:
  - `find`
  - `locate`
  - `which`
  - `whereis`
  - `file`
  - `dpkg -S`
  - `rpm -qf`

---

## 16. Qué suele preguntarse realmente en el 101

En el examen 101 suelen aparecer preguntas del tipo:
- diferencias entre BIOS y UEFI
- qué hace GRUB
- qué función tiene `initramfs`
- qué diferencias hay entre MBR y GPT
- cómo se interpreta un permiso `755`
- qué es un enlace duro
- qué archivo controla montajes persistentes
- qué diferencia hay entre `df` y `du`
- qué utilidad sirve para particionar, montar o verificar
- qué significa una opción frecuente de un comando

---

## 17. Cómo estudiar este bloque de conceptos

### Método recomendado
Para cada concepto, intenta asociar:

1. **definición breve**
2. **comando relacionado**
3. **archivo o ruta relacionada**
4. **ejemplo real de uso**
5. **error típico o confusión común**

Ejemplo:
- **Concepto:** montaje persistente
- **Comando relacionado:** `mount`
- **Ruta relacionada:** `/etc/fstab`
- **Ejemplo real:** montar automáticamente una partición de datos al arrancar
- **Confusión típica:** creer que montar manualmente y configurar persistencia es lo mismo

---

## 18. Resumen de prioridad alta para el 101

Domina especialmente estos conceptos:

- arquitectura del sistema
- BIOS vs UEFI
- secuencia de arranque
- kernel
- `initramfs`
- GRUB
- runlevels y targets
- paquetes y dependencias
- librerías compartidas
- shell, redirecciones y tuberías
- expresiones regulares básicas
- procesos, señales y nice
- MBR vs GPT
- particiones y montaje
- sistemas de archivos
- inodos
- enlaces duros y simbólicos
- permisos normales y especiales
- umask
- FHS

---

## 19. Relación con el resto del proyecto

Este archivo complementa especialmente:

- `01_objetivos_desarrollados.md`
- `03_matriz_objetivo_comandos.md`
- `05_rutas_y_ficheros_clave.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`
- `07_opciones_frecuentes.md`

## Siguiente paso recomendado

El siguiente archivo natural del proyecto es:

- `09_conceptos_clave_102.md`

Con ese completarás la parte conceptual principal del temario LPIC-1.
