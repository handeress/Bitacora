# Bitácora de obra

App instalable (Android, Chrome) para llevar las tareas de obra por proyecto. Funciona sin internet; los datos y las fotos viven solo en el celular.

Dirección: https://handeress.github.io/Bitacora/ (activar GitHub Pages desde la rama `main`).

## Fase 1 (esta versión)

- Tareas por proyecto, agrupadas por tema, con estado Pendiente / En proceso / Terminado.
- Ficha: qué hay que hacer, respuesta, medidas tomadas (nombre, valor, unidad), fotos, responsable, fecha límite e historial de cambios de estado.
- Anotar tarea rápida desde la lista.
- Copiar la lista del proyecto como texto para pegarla en el chat.
- Respaldo completo en un archivo `.json` (con fotos), sumar datos y restaurar.

## Fase 2 (en curso)

- Ficha con pasos, materiales y medidas por tomar.
- Sincronización con el repo privado `Bitacora-datos` (llave de GitHub guardada solo en el celular): la app sube `app/tareas.json` y `app/fotos/<id>.jpg`, y suma lo que Claude deja en `claude/entrada/*.json` (mismo formato del respaldo).

- Modo visita: recorrido de tareas abiertas con marca de revisada, observaciones nuevas y cierre (clima, personal, nota). Las visitas van en `app/tareas.json`.

## Fase 3

- Color de referencia por proyecto (franja del encabezado y títulos), editable en Más → Proyectos.
- Cambio de proyecto desde la ficha de la tarea.
- Diario: línea de tiempo por obra con tareas nuevas, cambios de estado y visitas.

- Las entradas de Claude pueden traer `"borrar": [ids]` para quitar tareas (desde la versión 3.1).

## Versión 4.0

- Tipo de tarea (lo que sigue), prioridad, sesión de trabajo y marca Para Claude; barra de filtros en una fila con paneles.
- Entradas nuevas de Claude en `claude/buzon/` con `"min"` (versión mínima de formato; hoy 4) y `"cambios": [{id, campos, nota}]` para cambiar solo algunos campos de una tarea.

## Versión 5.0

- La tarea es un elemento que se completa instalado en obra. Etapas con tipo (incluye Transportar); el tipo de la tarea y el estado se calculan de la primera etapa sin hacer (estado se puede fijar a mano y volver a automático). Plantillas de etapas.
- `docs`: enlaces a planos y documentos en Drive (el archivo vive solo en Drive; la tarea guarda el enlace).
- Buzón con `"min": 5` para usar etapas con tipo y `docs`.

## Versión 6.0

- Varios aparatos (celular y PC) con la misma llave: cada sincronización baja `app/tareas.json`, junta tarea por tarea (gana la más reciente por `actualizado`), aplica lápidas de borrado (`borradas`) y baja las fotos que falten; después sube el estado junto. `aplicadas` registra qué archivos del buzón ya se aplicaron, para que un aparato nuevo no los repita. Si otro aparato subió al mismo tiempo, se reintenta.
- Sincroniza cada minuto mientras la app está abierta.

## Pendiente

- Informe de visita en PDF (lo arma Claude desde `Bitacora-datos`).
- Fase 3: diario, cierre del día e informe PDF.

## Archivos

- `index.html`: toda la app.
- `sw.js`: modo sin internet. Subir `CACHE` (`bitacora-v2`, …) en cada cambio.
- `manifest.json`, `icono-192.png`, `icono-512.png`: instalación.

## Reglas

- El repositorio es público: aquí no van datos de obras ni de clientes, solo código.
- Los ids de proyecto son los de `proyectos.json` de Obras-base.
- Después de un cambio: abrir con internet, cerrar y volver a abrir.
