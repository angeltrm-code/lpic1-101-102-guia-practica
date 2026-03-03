# Contributing

## Proposito del repositorio
Este repositorio mantiene una guia practica modular para preparar LPIC-1 (101 y 102).
El objetivo es que el material sea didactico, navegable y facil de mantener en el tiempo.

## Como proponer mejoras
1. Revisa primero el indice maestro y el archivo relacionado con tu cambio.
2. Haz cambios pequenos, enfocados y faciles de revisar.
3. Explica en el commit que problema resolviste y por que.
4. Prioriza mejoras de claridad, navegacion, practica y consistencia editorial.

## Estilo de escritura
- Escribe en tono didactico, directo y orientado a practica real.
- Usa encabezados consistentes (`##` para secciones, `###` para subapartados).
- Manten listas cortas y legibles.
- Evita parrafos largos y repeticiones innecesarias.
- Conserva el orden pedagogico del material (de base a repaso).

## Regla de cambios minimos
- No hagas reescrituras masivas si no son estrictamente necesarias.
- Manten el contenido tecnico base; mejora forma y usabilidad.
- Si un cambio afecta varias secciones, divide en commits pequenos.
- No introduzcas cambios colaterales fuera del alcance de la tarea.

## Politica de backups locales
Antes de editar un archivo existente, crear backup.
Los backups se guardan SIEMPRE dentro de `_bak/`.
`_bak/` es local y esta en `.gitignore` (no se sube a GitHub).

## Convenciones de nombres de archivos
- Los documentos principales usan prefijo numerico `00` a `13`.
- Usa `snake_case` en nombres de archivo.
- Mantiene extensiones `.md` para contenido de guia.
- Evita renombrar archivos existentes sin motivo claro.

## Checklist rapido antes de commit
- El cambio es pequeno y trazable.
- El markdown mantiene estructura consistente.
- Los enlaces relativos funcionan.
- No hay archivos `.bak*` en la raiz del repo.
- Los backups locales quedaron dentro de `_bak/`.

## Alcance de esta guia
Estas reglas aplican a contribuciones de documentacion y practica LPIC-1 dentro de este repo.
Si una mejora requiere romper estas normas, justificalo explicitamente en el commit.
