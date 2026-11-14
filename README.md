# Bitácora de obra

App instalable (Android, Chrome) para llevar las tareas de obra por proyecto. Funciona sin internet; los datos y las fotos viven solo en el celular.

Dirección: https://handeress.github.io/Bitacora/ (activar GitHub Pages desde la rama `main`).

## Fase 1 (esta versión)

- Tareas por proyecto, agrupadas por tema, con estado Pendiente / En proceso / Terminado.
- Ficha: qué hay que hacer, respuesta, medidas tomadas (nombre, valor, unidad), fotos, responsable, fecha límite e historial de cambios de estado.
- Anotar tarea rápida desde la lista.
- Copiar la lista del proyecto como texto para pegarla en el chat.
- Respaldo completo en un archivo `.json` (con fotos), sumar datos y restaurar.

## Pendiente

- Fase 2: buzón de Claude (listas de visita preparadas en el chat) y modo visita.
- Fase 3: diario, cierre del día e informe PDF.

## Archivos

- `index.html`: toda la app.
- `sw.js`: modo sin internet. Subir `CACHE` (`bitacora-v2`, …) en cada cambio.
- `manifest.json`, `icono-192.png`, `icono-512.png`: instalación.

## Reglas

- El repositorio es público: aquí no van datos de obras ni de clientes, solo código.
- Los ids de proyecto son los de `proyectos.json` de Obras-base.
- Después de un cambio: abrir con internet, cerrar y volver a abrir.
