# Plan de Backups

## Qué se respalda
Base de datos PostgreSQL en neon (tabla `tasks` y esquema completo).

## Frecuencia
Neon mantiene backups automáticos continuos mediante "Point-in-Time Restore",
con historial de hasta 7 días en el plan gratuito.

## Almacenamiento
Los backups se almacenan de forma gestionada en la infraestructura de Neon
(AWS US East 2, Ohio), separada de la aplicación desplegada en Railway.

## Procedimiento de recuperación
1. Entrar al dashboard de Neon → proyecto → pestaña "Restore".
2. Seleccionar el punto en el tiempo (fecha/hora) al que se desea volver.
3. Confirmar la restauración.
4. Verificar con `GET /health` que la app reconecta correctamente.
5. Confirmar integridad de datos con `GET /tasks`.

## Backup manual adicional (opcional)
\`\`\`bash
pg_dump "postgresql://usuario:password@host/neondb?sslmode=require" > backup_$(date +%F).sql
\`\`\`

## Restauración manual desde dump
\`\`\`bash
psql "postgresql://usuario:password@host/neondb?sslmode=require" < backup_2026-08-02.sql
\`\`\`