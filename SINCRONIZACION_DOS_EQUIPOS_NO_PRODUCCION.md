# Sincronización de conciliaciones — diseño y estado (03-11-2026)

**Estado: PROTOTIPO / NO INTEGRADO / NO PUBLICAR COMO ESTABLE**

Se preparó y probó por separado un motor de eventos para conciliación manual, modificación de justificación y reversión. El prototipo conserva un evento por operación, usa referencias causales, detecta doble asignación documental y marca conflictos simulados entre equipos. Aprobó 11 pruebas automatizadas de Node.js en el entorno de desarrollo.

**Bloqueo identificado:** usar solamente una carpeta de OneDrive para sincronizar estos eventos NO ofrece atomicidad entre dos computadores ni garantía de recepción inmediata de cambios. Si ambos usuarios operan a la vez puede haber un conflicto temporal. El prototipo detecta el conflicto a posteriori y bloquea decisiones, pero no lo previene de manera transaccional.

**Decisión técnica propuesta para producción:** almacenamiento central transaccional y autenticado para decisiones e historial, con bloqueo de doble conciliación por movimiento y documento, auditoría de usuario/fecha, control de versión del evento, seguridad y recuperación. Mantener el Excel como fuente de cartolas y el saldo bancario tal como figura en ellas, sin recalcular ni escribir movimientos desde el módulo de sincronización.

**Pendiente:** proveedor y credenciales de servicio aprobados; integración con Electron; migración del historial previo (sin fusionar ensayos de laboratorio); pruebas simultáneas en dos Windows, offline/reconexión y rollback. Nunca subir datos financieros o perfiles personales a GitHub.

El manifiesto estable de `main` debe continuar en V3.2.25 hasta cumplir los controles.