# 00 — Índice maestro del proyecto LPIC-1

> Este archivo actúa como **punto de entrada** del proyecto de estudio LPIC-1.  
> Su objetivo es dejar todos los `.md` organizados, con una descripción clara y un **orden recomendado de lectura, práctica y repaso**.

**Temario base:** LPIC-1 101-500 y 102-500 (versión 5.0)  
**Última revisión del repo:** 2026-03-03

[Volver a README](README.md)

## Objetivo del proyecto

Construir un conjunto de documentos modulares en Markdown para preparar los exámenes **LPIC-1 101 y 102**, cubriendo:

- objetivos oficiales
- comandos
- rutas y ficheros clave
- conceptos fundamentales
- ejercicios prácticos
- laboratorios guiados
- material de repaso
- autoevaluación

La idea es que el proyecto sirva tanto para:

- **estudiar teoría**
- **practicar en terminal**
- **repasar antes del examen**
- **identificar huecos reales de preparación**

---

## Estructura general del proyecto

El proyecto queda organizado en cuatro grandes capas:

### 1. Base documental
Material que define el temario y el inventario básico de comandos.

### 2. Trazabilidad y referencia técnica
Material que conecta objetivos con comandos y recopila rutas, sintaxis y opciones.

### 3. Base conceptual y práctica
Material para entender la teoría y practicarla en entorno real.

### 4. Consolidación y repaso
Material para repasar rápido y medir el estado real de preparación.

---

## Archivos del proyecto

### [00_indice_maestro.md](00_indice_maestro.md) — Índice general del proyecto
Mapa de navegación del proyecto LPIC-1. Explica qué contiene cada archivo y en qué orden conviene usarlo.

### [01_objetivos_desarrollados.md](01_objetivos_desarrollados.md) — Objetivos desarrollados
Desarrollo de los objetivos oficiales de LPIC-1 (101 y 102), organizado por examen, tema y objetivo.

### [02_comandos_agrupados.md](02_comandos_agrupados.md) — Comandos agrupados
Listado de comandos agrupados por áreas funcionales, con explicación breve.

### [03_matriz_objetivo_comandos.md](03_matriz_objetivo_comandos.md) — Matriz objetivo → comandos
Relaciona cada objetivo oficial con los comandos, archivos y utilidades que conviene reconocer o practicar.

### [04_matriz_comando_objetivo.md](04_matriz_comando_objetivo.md) — Matriz comando → objetivo
Matriz inversa para estudiar cada comando y ver en qué objetivos del temario encaja.

### [05_rutas_y_ficheros_clave.md](05_rutas_y_ficheros_clave.md) — Rutas y ficheros clave
Guía de rutas, directorios y archivos importantes para LPIC-1, con explicación breve y prioridad de estudio.

### [06_comandos_con_sintaxis_y_ejemplos.md](06_comandos_con_sintaxis_y_ejemplos.md) — Comandos con sintaxis y ejemplos
Guía práctica de comandos con sintaxis base, ejemplos y notas de uso.

### [07_opciones_frecuentes.md](07_opciones_frecuentes.md) — Opciones frecuentes
Resumen de flags y opciones cortas/largas que más se repiten en comandos habituales del examen.

### [08_conceptos_clave_101.md](08_conceptos_clave_101.md) — Conceptos clave 101
Resumen teórico guiado de la parte conceptual del examen 101.

### [09_conceptos_clave_102.md](09_conceptos_clave_102.md) — Conceptos clave 102
Resumen teórico guiado de la parte conceptual del examen 102.

### [10_ejercicios_practicos.md](10_ejercicios_practicos.md) — Ejercicios prácticos
Colección de ejercicios por bloques para practicar en terminal los contenidos del temario.

### [11_labs_guiados.md](11_labs_guiados.md) — Labs guiados
Mini laboratorios paso a paso, reproducibles, para practicar LPIC-1 en una VM.

### [12_chuleta_repaso_rapido.md](12_chuleta_repaso_rapido.md) — Chuleta de repaso rápido
Documento condensado para refrescar comandos, conceptos y rutas clave antes de examen o práctica.

### [13_checklist_preparacion_lpic1.md](13_checklist_preparacion_lpic1.md) — Checklist de preparación
Checklist de autoevaluación para medir progreso, detectar huecos y planificar repaso.

### Simulacros tipo examen
Preguntas y casos prácticos que imitan el formato real LPIC-1, con soluciones al final.

- [simulacros/simulacro_101.md](simulacros/simulacro_101.md) — Simulacro del examen 101
- [simulacros/simulacro_102.md](simulacros/simulacro_102.md) — Simulacro del examen 102
- [simulacros/plantilla_correccion.md](simulacros/plantilla_correccion.md) — Plantilla de corrección


---

## Orden recomendado de estudio y uso

### Fase 1 — Entender qué entra en LPIC-1
Empieza por aquí si todavía estás construyendo el mapa mental del temario:

1. `01_objetivos_desarrollados.md`
2. `02_comandos_agrupados.md`

**Objetivo de esta fase**
- entender qué se pide
- reconocer bloques del examen
- empezar a ver vocabulario técnico

---

### Fase 2 — Conectar teoría y comandos
Cuando ya conoces el temario, pasa a la relación entre objetivos y utilidades:

3. `03_matriz_objetivo_comandos.md`
4. `04_matriz_comando_objetivo.md`

**Objetivo de esta fase**
- saber qué comandos se asocian a cada objetivo
- detectar comandos transversales
- construir trazabilidad entre teoría y práctica

---

### Fase 3 — Construir referencia técnica
Después, consolida el material técnico de consulta rápida:

5. `05_rutas_y_ficheros_clave.md`
6. `06_comandos_con_sintaxis_y_ejemplos.md`
7. `07_opciones_frecuentes.md`

**Objetivo de esta fase**
- dominar rutas importantes
- recordar sintaxis útil
- reconocer flags muy frecuentes

---

### Fase 4 — Construir comprensión conceptual
Cuando ya tengas una base operativa, afianza la teoría:

8. `08_conceptos_clave_101.md`
9. `09_conceptos_clave_102.md`

**Objetivo de esta fase**
- entender el porqué de los comandos y ficheros
- preparar preguntas teóricas de examen
- evitar estudio puramente mecánico

---

### Fase 5 — Pasar a práctica real
Después de teoría y referencia, toca operar en terminal:

10. `10_ejercicios_practicos.md`
11. `11_labs_guiados.md`

**Objetivo de esta fase**
- practicar por bloques
- automatizar acciones habituales
- ganar soltura real en VM o laboratorio

---

### Fase 6 — Consolidar y medir progreso
La última fase es la de repaso y autoevaluación:

12. `12_chuleta_repaso_rapido.md`
13. `13_checklist_preparacion_lpic1.md`

**Objetivo de esta fase**
- repasar rápido
- detectar lagunas
- planificar refuerzo
- medir si estás listo o no

---

## Orden recomendado si ya tienes conocimientos previos

Si ya manejas Linux a nivel básico y no quieres empezar tan desde cero, este orden suele ser más eficiente:

1. `12_chuleta_repaso_rapido.md`
2. `13_checklist_preparacion_lpic1.md`
3. `03_matriz_objetivo_comandos.md`
4. `05_rutas_y_ficheros_clave.md`
5. `06_comandos_con_sintaxis_y_ejemplos.md`
6. `10_ejercicios_practicos.md`
7. `11_labs_guiados.md`

---

## Orden recomendado si tu prioridad es practicar

Si tu prioridad es menos teoría y más terminal:

1. `06_comandos_con_sintaxis_y_ejemplos.md`
2. `07_opciones_frecuentes.md`
3. `10_ejercicios_practicos.md`
4. `11_labs_guiados.md`
5. `12_chuleta_repaso_rapido.md`
6. `13_checklist_preparacion_lpic1.md`

Y usar como apoyo puntual:
- `05_rutas_y_ficheros_clave.md`
- `08_conceptos_clave_101.md`
- `09_conceptos_clave_102.md`

---

## Relación entre documentos

### Núcleo teórico
- `01_objetivos_desarrollados.md`
- `08_conceptos_clave_101.md`
- `09_conceptos_clave_102.md`

### Núcleo técnico
- `02_comandos_agrupados.md`
- `05_rutas_y_ficheros_clave.md`
- `06_comandos_con_sintaxis_y_ejemplos.md`
- `07_opciones_frecuentes.md`

### Núcleo de trazabilidad
- `03_matriz_objetivo_comandos.md`
- `04_matriz_comando_objetivo.md`

### Núcleo práctico
- `10_ejercicios_practicos.md`
- `11_labs_guiados.md`

### Núcleo de consolidación
- `12_chuleta_repaso_rapido.md`
- `13_checklist_preparacion_lpic1.md`

---

## Qué aporta cada tipo de documento

### Objetivos
Te dicen **qué entra**.

### Matrices
Te dicen **cómo se conecta**.

### Rutas y comandos
Te dicen **qué debes reconocer y usar**.

### Conceptos
Te dicen **por qué funciona así**.

### Ejercicios y labs
Te dicen **cómo practicarlo de verdad**.

### Chuleta y checklist
Te dicen **qué recuerdas y qué te falta**.

---

## Propuesta de uso semanal

### Semana tipo de estudio
- **Día 1:** objetivos + conceptos
- **Día 2:** comandos + sintaxis
- **Día 3:** rutas + opciones frecuentes
- **Día 4:** ejercicios prácticos
- **Día 5:** labs guiados
- **Día 6:** repaso con chuleta + checklist
- **Día 7:** repetir lo que peor llevas

---

## Señal de que el proyecto está funcionando bien

Sabrás que este proyecto te está ayudando de verdad si notas que:

- cada vez consultas menos la teoría básica
- resuelves más ejercicios sin mirar apuntes
- entiendes mejor por qué usar un comando u otro
- relacionas rutas, comandos y conceptos sin esfuerzo
- puedes hacer varios labs casi de memoria
- la checklist va acumulando más `[x]` y menos `[~]`

---

## Próximos usos posibles de este proyecto

A partir de aquí, este conjunto de `.md` puede servir para:

- montar un repositorio de estudio
- convertirlo en un manual más grande
- generar una guía PDF o DOCX
- construir un plan de estudio semanal
- usar los simulacros incluidos para medir preparación
- crear tarjetas de memorización o flashcards
- hacer una versión resumida por examen 101 / 102

---

## Estado del proyecto

Con este índice, el proyecto base queda **estructurado y navegable**.  
Ya tienes una colección modular que cubre:

- objetivos oficiales
- comandos y opciones
- rutas y ficheros
- conceptos 101 y 102
- ejercicios
- laboratorios
- repaso
- checklist

## Cierre

Este archivo debe mantenerse como **entrada principal** del proyecto.  
Si en el futuro añades más `.md`, conviene actualizarlos aquí para conservar una visión global limpia y ordenada.
