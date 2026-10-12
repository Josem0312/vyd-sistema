# Sistema VyD

Sistema propio de VyD, distribuidora e importadora de libros (Perú, régimen Mype). El repositorio está recién creado: todavía no hay código ni stack definido. Este proyecto **no tiene relación** con el ERP de Alarinsa (`Josem0312/intranet`): no copiar su código, datos, configuración ni carpetas.

## Reglas importantes

- **Nunca commitear datos reales ni secretos.** Bases de datos, archivos subidos, sesiones y archivos de configuración con credenciales van en `.gitignore`. No pegar credenciales en el chat ni en el código.
- **Información para producción:** lo que el sistema necesitará al pasar a producción y no puede ir en git (datos de personas, valores de la empresa, estado de credenciales, archivos que se copian al servidor) se junta en la carpeta `produccion-vyd/`, **junto a este repo y fuera de él** (`../produccion-vyd/`). Es exclusiva de VyD: nunca usar ni mezclar la carpeta `produccion/` del ERP de Alarinsa. Al tocar algo que afecte a producción, leer y actualizar `../produccion-vyd/LEEME.md` y `../produccion-vyd/PENDIENTES-PRODUCCION.md`. No guardar credenciales ahí, solo dónde viven y su estado. Nunca copiar esa carpeta al repo.
- **Datos de desarrollo:** desarrollar con una instancia demo de datos ficticios. No asumir que los datos locales son los reales.
- Mantener el proyecto **fuera de OneDrive**: OneDrive rompe bases de datos locales, sesiones y `node_modules`.
- **Documentación:** el historial y el "por qué" de cada módulo viven en `docs/modulos/NN-tema.md` (un tema por archivo). Mantener un mapa del proyecto (`docs/MAPA-DEL-PROYECTO.md`) que ubique cada módulo, sus archivos, datos y pruebas, para leer solo lo necesario y no releer todo el repo en cada tarea. Si se crea o cambia un módulo, actualizar su archivo y el mapa en el mismo PR.

## Forma de trabajar

- Si hay dudas de negocio, proponer el diseño a Jose Maria **antes** de programar.
- Orden de trabajo: backend y pruebas primero, luego la interfaz, verificar en la instancia demo y al final documentar.
- Sin frameworks ni dependencias nuevas salvo necesidad clara.
- Correr las pruebas antes de abrir un PR.

## Convenciones

- Idioma: textos de la app, commits y documentación en **español**. Mensajes de commit sin tildes.
- Al referirse al usuario (chat, documentos, comentarios de código, PRs, commits), escribir siempre **Jose Maria**, nunca solo "Jose".
- Commits firmados por **Jose Maria Diaz La Puente**. Un cambio por commit, con mensaje descriptivo.
- Flujo de cambios: rama nueva -> commits -> Pull Request a `main` en `Josem0312/vyd-sistema`. No empujar directo a `main`.
- La rama de un PR se borra sola cuando el PR se fusiona o se cierra (workflow `borrar-rama-pr.yml`): no borrarla a mano ni pedir permiso para ello. Una rama borrada al cerrar sin fusionar se restaura desde la página del PR.
- **Fusión con squash y automática:** un PR abierto por Claude se fusiona solo (squash) cuando todas las pruebas pasan (locales y de CI) y GitHub lo marca limpio y sin conflictos, sin esperar el OK de Jose Maria. Si alguna prueba falla, se corrige antes; no se fusiona en rojo.
- **Antes de fusionar cualquier PR:** revisar sus archivos de texto en busca de datos sensibles (correos, DNI/RUC, IPs, contraseñas). Los binarios (PDF, imágenes) no se pueden revisar: si el PR trae alguno nuevo, avisar a Jose Maria antes de fusionar.
- **Copia local siempre al día:** después de cada commit que llegue a `main`, actualizar la copia local de Jose Maria (`git pull --ff-only`) sin esperar a que se pida; si el commit queda solo en una rama, hacer `git fetch`. Antes de actualizar, revisar `git status` y no sobrescribir cambios locales.
- **Sesiones largas:** cada mensaje reprocesa todo el historial. Avisar a Jose Maria cuando una sesión se haga larga (más de unas 40 interacciones, muchas lecturas de archivos grandes o un cambio de tema) y sugerir una sesión nueva, dejando antes todo listo y el contexto relevante guardado en memoria.
