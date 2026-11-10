# Control Financiero CBI V3.2.26 — Preparación de publicación (NO PRODUCCIÓN)

Estado al 03-11-2026: **CANDIDATA BLOQUEADA**, sin Release estable y sin actualización del manifiesto de `main`.

## Comprobaciones completadas
- Paquetes V3.2.25 y V3.2.26 comparados.
- Candidata de actualización interna de cuatro archivos (`index.html`, `main.js`, `preload.js`, `package.json`) preparada localmente.
- Sintaxis de scripts y estructura del ZIP aprobadas; versión de interfaz/manifest compatible en borrador.
- SHA-256 del ZIP candidato: `d4809e7d93c7ee76a5d669ee981873a5ffc67234071bd2b1f75780229f0123e8`.
- Se conserva el perfil original de Electron bajo el nombre de aplicación `Control Financiero CBI`.

## BLOQUEOS de publicación
1. La conciliación manual y su historial persisten en `localStorage` de CADA computador. No se sincronizan mediante el Excel de OneDrive. Esto puede producir estados diferentes entre los dos equipos. Diseñar persistencia compartida con control de conflictos y respaldo antes de usarlo en producción en ambos.
2. Probar en Windows la continuidad de usuarios, datos, conciliaciones y reversión, usando una copia de datos y perfil en un entorno realmente aislado.
3. Validar el actualizador interno al sustituir archivos y su rollback (fallo durante actualización).
4. Resolver dependencia de biblioteca XLSX descargada desde CDN y verificar carga sin conexión.
5. Resolver firma/confianza de instalación o mecanismo autorizado por Smart App Control, según la configuración del segundo equipo.
6. Verificar que el Excel compartido no sufra escrituras simultáneas incompatibles.

## Publicación segura posterior
- Mantener el manifiesto estable de `main` en **V3.2.25** hasta aprobar todo.
- Publicar primero la candidata como GitHub **pre-release** con ZIP y su SHA verificado; NO cambiar el manifiesto estable en esa etapa.
- Probar actualización y recuperación en el segundo equipo usando respaldos y copia de Excel.
- Recién después de aprobación, actualizar el manifiesto estable con URL de Release y SHA real.
- No subir al repositorio Excel, perfiles, claves ni historiales de usuario.

Este archivo es documentación del trabajo de preparación; no anuncia una versión lista para instalar.