# 09 — Conceptos clave 102 (LPIC-1 101 y 102)

> Documento de trabajo para el proyecto LPIC-1.  
> Este archivo reúne los **conceptos fundamentales del examen 102**, explicados de forma clara y orientados al estudio práctico.  
> Complementa los archivos de comandos, rutas, matrices y conceptos del 101 para cerrar la base teórica principal de LPIC-1.

## Cómo usar este archivo

- Léelo como un **resumen teórico guiado** del examen 102.
- Relaciona cada concepto con:
  - un comando
  - un archivo o ruta
  - una situación real de administración
- La idea no es memorizar frases, sino **entender cómo funciona el sistema**.

---

## 1. Shells y entorno de usuario

### Qué es una shell de login
Es la shell que se ejecuta al iniciar sesión de forma completa.

**Qué debes recordar**
- Suele leer ciertos archivos de configuración globales y personales.
- No es lo mismo una shell de login que una shell interactiva no-login.

---

### Shell interactiva vs no interactiva
#### Interactiva
Recibe órdenes directamente del usuario.

#### No interactiva
Ejecuta un script o comandos sin interacción directa.

**Por qué importa**
- No siempre se cargan los mismos archivos de configuración.
- Esto afecta alias, variables y comportamiento del entorno.

---

### Personalización del entorno
El entorno del usuario puede personalizarse con:
- variables de entorno
- alias
- funciones
- prompt
- ficheros de configuración

**Archivos típicos**
- `/etc/profile`
- `/etc/bash.bashrc` en Debian y derivadas
- `~/.profile`
- `~/.bash_profile`
- `~/.bashrc`

**Qué debes entender**
- Hay configuración global y configuración por usuario.
- No todos los ficheros se cargan siempre en el mismo contexto.

---

### Variables de entorno
Son valores asociados a la sesión y heredables por procesos hijos.

Ejemplos:
- `HOME`
- `PATH`
- `LANG`
- `SHELL`
- `USER`

**Qué debes recordar**
- Una variable puede existir solo en la shell actual o exportarse al entorno.
- `PATH` determina dónde se buscan ejecutables.

---

### PATH
Es la variable que indica las rutas donde la shell buscará comandos.

**Qué debes entender**
- Si un comando no está en `PATH`, tendrás que usar su ruta completa.
- Un `PATH` mal configurado puede causar errores o riesgos de seguridad.

---

## 2. Scripting en shell

### Qué es un script
Es un archivo de texto con una secuencia de órdenes que la shell puede ejecutar.

**Para qué sirve**
- automatizar tareas
- repetir procesos
- encadenar comandos
- aplicar lógica simple

---

### Shebang
La primera línea de muchos scripts indica el intérprete que debe usarse.

Ejemplo:
```bash
#!/bin/bash
```

**Qué debes recordar**
- El shebang no es un comentario cualquiera: define el intérprete.

---

### Permiso de ejecución
Para ejecutar un script como programa, normalmente necesita permiso `x`.

**Qué debes entender**
- También puede ejecutarse llamando directamente al intérprete, aunque el archivo no sea ejecutable.

Ejemplo mental:
- `./script.sh` requiere permiso de ejecución
- `bash script.sh` usa el intérprete explícitamente

---

### Variables en scripts
Los scripts usan variables para guardar y reutilizar valores.

**Qué debes recordar**
- En shell, los espacios importan mucho.
- La expansión de variables usa `$VARIABLE` o `${VARIABLE}`.

---

### Parámetros posicionales
Los scripts pueden recibir argumentos:
- `$1`, `$2`, `$3`...
- `$0` suele ser el nombre del script
- `$#` número de argumentos
- `$@` lista de argumentos

**Qué debes recordar**
- Es un punto muy típico de LPIC-1.

---

### Códigos de salida
Todo comando devuelve un código al terminar.

- `0` suele significar éxito
- distinto de `0` indica error o condición especial

**Qué debes entender**
- Los scripts pueden usar estos códigos para decidir qué hacer después.

---

### Condicionales y bucles
La shell permite lógica básica:

- `if`
- `case`
- `for`
- `while`

**Qué debes recordar**
- LPIC no exige programación avanzada, pero sí entender scripts sencillos.

---

### Comillas simples y dobles
#### Comillas simples `'...'`
Toman el contenido de forma literal.

#### Comillas dobles `"..."` 
Permiten expansión de variables y algunas sustituciones.

**Qué debes entender**
- La diferencia es muy importante en scripts y en línea de comandos.

---

## 3. X11 y escritorios

### Qué es X11
Es un sistema de ventanas tradicional en Unix/Linux para entornos gráficos.

**Qué debes recordar**
- Separa cliente gráfico y servidor gráfico.
- Muchas herramientas y conceptos del examen se basan en X11, aunque existan tecnologías más modernas.

---

### Cliente y servidor X
- **Servidor X:** controla pantalla, teclado y ratón.
- **Clientes X:** aplicaciones gráficas que usan ese servidor.

**Qué debes entender**
- El servidor X no es “el programa remoto”, sino quien gestiona la visualización.

---

### Display
El display identifica la sesión gráfica.

Ejemplo típico:
```bash
:0
```

**Qué debes recordar**
- La variable `DISPLAY` indica a qué servidor X debe conectarse una aplicación gráfica.

---

### Gestor de pantalla vs entorno de escritorio vs gestor de ventanas
#### Gestor de pantalla
Muestra la pantalla de login gráfica.

#### Entorno de escritorio
Conjunto amplio de componentes gráficos, paneles, herramientas y configuración.

#### Gestor de ventanas
Controla el comportamiento y apariencia de las ventanas.

**Qué debes entender**
- Son conceptos relacionados, pero no equivalentes.

---

### Accesibilidad y localización gráfica
El examen puede tocar conceptos como:
- teclado
- idioma
- distribución del teclado
- configuraciones de accesibilidad
- ajustes visuales

---

## 4. Usuarios, grupos y administración de cuentas

### UID y GID
- **UID:** identificador numérico del usuario
- **GID:** identificador numérico del grupo principal

**Qué debes recordar**
- Linux trabaja internamente con IDs, no solo con nombres.

---

### Grupo principal y grupos suplementarios
Cada usuario tiene:
- un grupo principal
- cero o más grupos adicionales

**Por qué importa**
- Los permisos y accesos dependen de esta pertenencia.

---

### Cuenta de usuario vs identidad efectiva
Un proceso puede ejecutarse:
- con el usuario real que lo lanzó
- con una identidad efectiva diferente

**Qué debes entender**
- Esto conecta con `sudo`, `su`, SUID y control de privilegios.

---

### Skeleton o `/etc/skel`
Plantilla de archivos que se copian al crear un nuevo home de usuario.

**Qué debes recordar**
- Es útil para desplegar configuraciones iniciales.

---

### Contraseñas y shadow
La información sensible de autenticación se separa de `/etc/passwd` y suele almacenarse en `/etc/shadow`.

**Qué debes entender**
- Esto mejora la seguridad evitando exponer hashes a todos los usuarios.

---

### Caducidad de contraseñas
Una cuenta puede tener políticas de:
- duración máxima
- duración mínima
- aviso antes de caducar
- bloqueo por inactividad

**Qué debes recordar**
- LPIC pregunta por estas políticas y por herramientas para gestionarlas.

---

### Bloqueo de cuentas
Bloquear una cuenta no siempre significa borrar al usuario.

**Qué debes entender**
- Puede impedir login manteniendo archivos, UID y configuración.

---

## 5. Automatización y tareas programadas

### Cron
Sistema clásico para ejecutar tareas periódicas.

**Qué debes recordar**
- Puede haber crontab por usuario y crontab del sistema.
- Es una pieza muy típica del examen.

---

### Estructura temporal de cron
Las entradas cron suelen tener campos para:
- minuto
- hora
- día del mes
- mes
- día de la semana

**Qué debes entender**
- El orden de los campos importa mucho.
- Un error pequeño cambia completamente cuándo se ejecuta la tarea.

---

### Cron del sistema vs cron de usuario
#### Cron de usuario
Gestionado con `crontab -e`.

#### Cron del sistema
Definido en archivos como `/etc/crontab` o `/etc/cron.d/`.

**Qué debes recordar**
- En cron del sistema suele aparecer también el usuario con el que se ejecuta la tarea.

---

### Anacron
Permite ejecutar tareas periódicas en equipos que no están encendidos todo el tiempo.

**Qué debes entender**
- Es útil para portátiles o equipos que pueden estar apagados cuando tocaría una tarea cron.

---

### At
Sirve para ejecutar una tarea **una sola vez** en un momento futuro.

**Diferencia con cron**
- `cron`: tareas repetitivas
- `at`: tarea única programada

---

## 6. Localización e internacionalización

### Localización
Adapta el sistema al idioma, formato de fechas, moneda, teclado y otras convenciones regionales.

---

### Locale
Una locale define reglas culturales y lingüísticas del entorno.

Ejemplos:
- idioma
- orden alfabético
- formato de fecha
- formato numérico

**Qué debes recordar**
- La configuración regional afecta tanto a programas de consola como a herramientas gráficas.

---

### Juego de caracteres
Es la forma de representar texto digitalmente.

**Qué debes entender**
- Hoy es habitual trabajar con UTF-8.
- Problemas de codificación pueden causar caracteres extraños o errores en scripts y ficheros.

---

### Teclado y mapa de teclado
El mapa de teclado determina qué carácter produce cada tecla.

**Qué debes recordar**
- Puede configurarse en consola o en entorno gráfico.
- Es un punto sencillo pero frecuente en temarios.

---

## 7. Hora del sistema y sincronización

### Hora del sistema
El sistema necesita mantener fecha y hora correctas para:
- logs
- tareas programadas
- certificados
- autenticación
- auditoría

---

### Hora hardware y hora del sistema
#### Hardware clock (RTC)
Reloj mantenido por la máquina.

#### System clock
Reloj que usa el sistema operativo en ejecución.

**Qué debes entender**
- Linux puede sincronizar uno con otro.
- Si están mal configurados, aparecen desfases.

---

### Zona horaria
La zona horaria define cómo se interpreta la hora local respecto a UTC.

**Qué debes recordar**
- Cambiar la hora no es lo mismo que cambiar la zona horaria.

---

### Sincronización horaria
Suele hacerse con NTP o servicios equivalentes.

**Por qué importa**
- Si la hora deriva demasiado, fallan servicios y auditorías.

---

## 8. Logs y registro del sistema

### Qué es un log
Es un registro de eventos del sistema o de una aplicación.

**Para qué sirve**
- diagnosticar problemas
- auditar actividad
- detectar fallos
- investigar incidentes

---

### Syslog tradicional
Modelo clásico de registro en Linux.

**Qué debes entender**
- Muchos sistemas siguen usando `rsyslog` o mecanismos compatibles.
- Los logs suelen almacenarse en `/var/log/`.

---

### Journal de systemd
Systemd incorpora su propio sistema de registro.

**Qué debes recordar**
- Permite consultas estructuradas y filtrado por servicios, arranque, prioridades, etc.

---

### Logs de autenticación
Registran inicios de sesión, fallos y eventos relacionados con seguridad.

**Qué debes recordar**
- El nombre del archivo cambia según la distribución.

---

### Rotación de logs
Evita que los logs crezcan indefinidamente.

**Qué debes entender**
- La rotación puede comprimir, archivar y eliminar registros antiguos.

---

## 9. MTA, correo local y alias

### Qué es un MTA
Un **Mail Transfer Agent** gestiona envío y recepción de correo entre sistemas.

Ejemplos:
- Postfix
- Exim
- Sendmail

---

### Correo local del sistema
Linux puede usar correo interno para:
- avisos de cron
- mensajes administrativos
- notificaciones del sistema

---

### Alias de correo
Permiten redirigir correo local de una cuenta a otra.

**Ejemplo mental**
- correo enviado a `root` puede reenviarse a un usuario administrador real

---

### Qué debes entender para LPIC-1
No suelen pedir administración profunda de correo, pero sí:
- conceptos básicos de MTA
- función de alias
- ubicación general de buzones o archivos de configuración

---

## 10. Impresión

### Sistema de impresión
Linux puede gestionar impresoras locales o en red.

**Qué debes recordar**
- Históricamente existen varios sistemas, pero CUPS es el más habitual.

---

### Cola de impresión
Los trabajos de impresión suelen entrar en una cola antes de procesarse.

**Qué debes entender**
- Puede haber impresoras, colas, estados y trabajos pendientes.

---

## 11. Fundamentos de red

### Dirección IP
Identifica un host en la red.

#### IPv4
Formato clásico como `192.168.1.10`

#### IPv6
Formato más moderno y largo

---

### Máscara y prefijo
Definen qué parte de una dirección corresponde a red y qué parte a host.

**Qué debes recordar**
- Entender la idea de red/subred es importante aunque no se pidan cálculos muy avanzados.

---

### Gateway o puerta de enlace
Es el router o sistema al que un host envía tráfico destinado fuera de su red local.

---

### DNS
Traduce nombres de dominio a direcciones IP y viceversa.

**Qué debes entender**
- Un sistema puede tener conectividad IP pero fallar resolución DNS.
- Eso genera síntomas diferentes.

---

### Hostname
Es el nombre del sistema.

**Qué debes recordar**
- Puede resolverse localmente o mediante DNS.

---

### Interfaz de red
Representa una conexión de red del sistema:
- física
- virtual
- loopback
- puente
- túnel

---

### Configuración persistente de red
La red puede configurarse de forma temporal o persistente.

**Qué debes entender**
- Cambios hechos con ciertos comandos pueden perderse al reiniciar si no se guardan en la configuración persistente.

---

### Loopback
Interfaz local del propio sistema, normalmente `127.0.0.1` en IPv4.

**Qué debes recordar**
- Es clave para pruebas locales y servicios internos.

---

## 12. Resolución de problemas básicos de red

### Capas del problema
Cuando algo falla en red, conviene pensar por capas:

1. interfaz levantada o no
2. IP configurada o no
3. gateway correcto o no
4. conectividad IP o no
5. resolución DNS o no
6. servicio remoto accesible o no

**Qué debes entender**
- No todo fallo “de Internet” es el mismo tipo de fallo.

---

### Conectividad vs resolución
Ejemplo conceptual:
- si puedes llegar a `8.8.8.8` pero no a `google.com`, probablemente el problema es DNS
- si no llegas a ninguna IP, el problema puede ser de enlace o configuración básica

---

### Puertos y sockets
Los servicios de red escuchan en puertos.

**Qué debes recordar**
- El sistema puede tener conectividad, pero el servicio correcto no estar escuchando.

---

## 13. Seguridad del sistema

### Principio de mínimo privilegio
Cada usuario o proceso debe tener solo los permisos necesarios para su función.

**Qué debes entender**
- Es una idea fundamental de seguridad y administración.

---

### Superusuario root
`root` tiene control total del sistema.

**Qué debes recordar**
- Precisamente por eso no debe usarse sin necesidad.
- Es preferible delegar privilegios de forma controlada.

---

### sudo
Permite ejecutar acciones privilegiadas de forma controlada y auditada.

**Qué debes entender**
- No sustituye el concepto de root, pero reduce la necesidad de usarlo continuamente.

---

### PAM
**Pluggable Authentication Modules** es un sistema modular de autenticación.

**Qué hace**
- permite configurar cómo se autentica un usuario
- aplicar políticas
- integrar distintos métodos de acceso

**Qué debes recordar**
- Es un concepto importante aunque a este nivel no se profundice en todos sus módulos.

---

### TCP Wrappers
Mecanismo clásico de control de acceso basado en archivos como:
- `/etc/hosts.allow`
- `/etc/hosts.deny`

**Qué debes entender**
- Es una tecnología histórica, pero conviene reconocerla.

---

### Hardening básico
Consiste en reducir superficie de ataque:
- deshabilitar servicios innecesarios
- aplicar permisos correctos
- limitar accesos
- mantener software actualizado
- revisar logs

---

## 14. Cifrado y protección de datos

### Cifrado
Transforma datos legibles en datos protegidos.

#### Simétrico
La misma clave cifra y descifra.

#### Asimétrico
Se usa un par de claves: pública y privada.

---

### Hash
No es cifrado reversible.

**Para qué sirve**
- verificar integridad
- almacenar contraseñas de forma segura
- comparar datos

---

### Firma digital
Permite verificar autenticidad e integridad de un mensaje o archivo.

---

### SSH
Proporciona acceso remoto seguro y copia segura de archivos.

**Qué debes entender**
- Combina autenticación, cifrado y administración remota.
- Es una pieza central de la administración Linux actual.

---

### GPG
Herramienta para cifrado y firma de archivos o mensajes.

---

### Cifrado de disco o partición
Protege datos en reposo.

**Qué debes recordar**
- Si el soporte se roba o se pierde, los datos siguen protegidos si el cifrado está bien implementado.

---

## 15. Qué suele preguntarse realmente en el 102

En el examen 102 suelen aparecer preguntas del tipo:
- qué archivo carga una shell de login
- diferencias entre `.profile` y `.bashrc`
- significado de parámetros posicionales en scripts
- diferencia entre cron y at
- función de anacron
- qué hace un locale
- cómo distinguir un problema de DNS de uno de conectividad
- qué es PAM
- para qué sirve `sudo`
- qué registra un log de autenticación
- qué es un MTA
- qué es una cola de impresión
- diferencia entre clave pública y privada
- para qué sirve SSH o GPG

---

## 16. Cómo estudiar este bloque de conceptos

### Método recomendado
Para cada concepto, intenta asociar:

1. **definición breve**
2. **comando relacionado**
3. **archivo o ruta relacionada**
4. **ejemplo real de uso**
5. **error típico o confusión común**

Ejemplo:
- **Concepto:** cron del sistema
- **Comando relacionado:** `crontab`
- **Ruta relacionada:** `/etc/crontab`
- **Ejemplo real:** lanzar una copia de seguridad diaria
- **Confusión típica:** pensar que el formato de cron del usuario y el del sistema es idéntico

---

## 17. Resumen de prioridad alta para el 102

Domina especialmente estos conceptos:

- shell de login vs no-login
- variables de entorno y `PATH`
- scripting básico
- shebang
- parámetros posicionales
- comillas simples y dobles
- X11, display y entorno gráfico
- usuarios, grupos y shadow
- caducidad y bloqueo de cuentas
- cron, anacron y at
- localización y locale
- hora del sistema, zona horaria y sincronización
- syslog y journal
- MTA y alias de correo
- fundamentos de red
- DNS y troubleshooting básico
- root, sudo y PAM
- cifrado, hash, firma digital, SSH y GPG

---

## 18. Relación con el resto del proyecto

Este archivo complementa especialmente:

- `01_objetivos_desarrollados.md`
- `03_matriz_objetivo_comandos.md`
- `05_rutas_y_ficheros_clave.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`
- `08_conceptos_clave_101.md`

## Siguiente paso recomendado

Con `08` y `09` ya queda cerrada la parte conceptual principal del temario.  
El siguiente archivo natural del proyecto es:

- `10_ejercicios_practicos.md`

Ese documento será el puente entre teoría y práctica real.
