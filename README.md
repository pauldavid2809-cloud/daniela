# Censo de la Misión · Parroquia "El Buen Pastor"

Webapp para el censo de la misión del **17 al 31 de julio de 2026** (Arquidiócesis de Maracaibo, Vicaría Episcopal Territorial Oeste). Registra las casas y personas visitadas para el seguimiento de la parroquia.

## Qué incluye

- **Censo**: registro de las casas visitadas y sus personas — enfermos, niños para Primera Comunión y Confirmación, personas vulnerables, bautizos pendientes, matrimonios por regularizar y unción/comunión a enfermos. Los datos se comparten entre todos los teléfonos (Supabase). Cada persona tiene estado de seguimiento (pendiente / en proceso / atendido) y botón de WhatsApp directo. Si se registra sin señal, queda guardado en el teléfono y se envía al recuperar conexión.
- **Stats**: estadísticas del censo en vivo — totales por categoría, por sector, por día, y la tabla categoría × sector para el seguimiento post-misión. Incluye un botón para descargar un PDF con estas estadísticas.

## Cómo usarla

Es una página estática, sin dependencias: abre `index.html` en el navegador, o publícala con GitHub Pages.

## Conectar el Censo (Supabase, gratis, ~15 min)

1. Crear un proyecto en [supabase.com](https://supabase.com) (plan Free). Hacerlo pocos días antes de la misión: los proyectos gratuitos se pausan tras ~7 días sin uso (se reactivan desde el dashboard).
2. En el proyecto: **SQL Editor → New query**, pegar el contenido de [`supabase.sql`](supabase.sql) y ejecutar. Esto crea los sectores, las tablas del censo y las políticas de seguridad (nadie puede borrar registros de verdad, solo ocultarlos).
3. **Project Settings → API**: copiar la *Project URL* y la *anon public key*, y pegarlas en [`config.js`](config.js).
4. Para agregar un sector nuevo: SQL Editor → `insert into sectores (nombre) values ('Nombre del sector');`

**Privacidad**: el censo guarda nombres, direcciones y teléfonos. Sin inicio de sesión, cualquiera que tenga el enlace puede verlos: no difundir la URL fuera de quienes deban tener acceso (equipo misionero y parroquia), y exportar/limpiar los datos al terminar la misión.
