# V3.2.26 — Publicación controlada para dos equipos

**Estado:** LISTA PARA PUBLICACIÓN DE PRUEBA, NO ESTABLE. Fecha: 2026-11-03.

## Paquete revisado y validado
- Archivo: `CONTROL_FINANCIERO_CBI_V3.2.26_UPDATE_CANDIDATA_NO_INSTALAR.zip`
- SHA-256: `d4809e7d93c7ee76a5d669ee981873a5ffc67234071bd2b1f75780229f0123e8`
- Tamaño: 1.464.879 bytes
- Contenido: `index.html`, `main.js`, `preload.js`, `package.json`
- Validación SHA-256 y estructura: APROBADA en Edge / Windows
- Actualización y restauración con Electron en copia aislada: APROBADA (resultado mostrado en Windows)
- Conciliación manual, corrección, reversión, historial, saldos: verificados previamente por el usuario con copia Excel de laboratorio.

## Restricciones de la liberación
- La V3.2.25 sigue siendo la versión oficial.
- Las conciliaciones e historial son locales a cada computador. **Regla operativa acordada:** conciliaciones reales en equipo 2; equipo 1 se emplea para configuración y pruebas. No se implementa sincronización entre equipos en esta liberación.
- No subir Excel, usuarios, claves ni respaldos a GitHub.
- La actualización no debe sobrescribir el Excel maestro en OneDrive.
- No copiar datos ni decisiones de laboratorio a producción.
- La dependencia de XLSX por CDN puede requerir conectividad; se debe comprobar en el escenario operativo.
- Confirmar versión y acceso al Excel en cada computador y resguardar rollback.

## Plan de publicación e instalación
1. Crear GitHub Release etiquetada `v3.2.26-rc-final`, marcada **Pre-release**; subir el ZIP candidato verificado. Este paso **no está hecho**.
2. Confirmar la descarga del asset público y volver a comprobar el SHA-256.
3. Hacer ensayo manual de instalación/actualizador en equipo 1 en ventana controlada, con respaldo previo y copia Excel; validar usuarios, Excel, valores y reversión.
4. Comprobar compatibilidad y disponibilidad del segundo equipo; actualizarlo en ventana sin actividad, con Excel cerrado y respaldo local.
5. Solo tras aprobación explícita de ambos ensayos, crear Release final `v3.2.26` con asset aprobado y cambiar `main/control_financiero_update.json` desde V3.2.25 a V3.2.26 utilizando la URL real del Release y su SHA real.
6. Validar la lectura y funcionamiento desde el botón de actualizaciones en ambos equipos. Conservar V3.2.25 para recuperación.

**No se han realizado los pasos 1 a 6 de publicación/instalación en producción.**