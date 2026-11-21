# LeaderSource

Portal institucional, campus virtual de formación y oficina virtual de documentación para una organización de desarrollo de líderes, iglesias y ministerios.

**Estado:** las cinco fases están construidas y verificadas en un entorno de desarrollo. **No se ha desplegado ni auditado con personas usuarias.** Antes de publicar con datos reales lea `docs/08-seguridad.md`, `docs/05-accesibilidad.md` y `docs/07-despliegue-y-operacion.md`: dicen qué se probó y qué no.

## Empezar

```bash
npm install
# Base de datos: ver docs/02-fase3-desarrollo-funcional.md (bootstrap, migraciones y datos ficticios)
cp .env.example apps/web/.env.local     # completar variables
npm run dev                              # http://localhost:3000
npm test                                 # pruebas contra PostgreSQL real
npm run typecheck
```

## Qué hay

| Ruta | Contenido |
|---|---|
| `apps/web/` | Aplicación Next.js 16: portal público, campus, oficina virtual y administración. |
| `db/` | Migraciones SQL (0001 a 0019; no hay 0017), datos ficticios de desarrollo, rol de aplicación sin DDL y seguridad por filas. |
| `scripts/` | Copias de seguridad y restauración, mantenimiento, rotación de claves, comprobación de entorno, rendimiento. |
| `deploy/`, `apps/web/Dockerfile`, `docker-compose*.yml`, `.github/` | Despliegue, proxy inverso de ejemplo e integración continua (no probados en un proveedor real). |
| `prototype/` | Prototipo navegable de la Fase 2, con datos ficticios, independiente de la aplicación. |
| `docs/` | Documentación (ver abajo). |

## Documentación

| Documento | Contenido |
|---|---|
| `docs/01-diseno-conceptual.md` | Arquitectura, mapa del sitio, identidad visual, modelo de datos, roles, infraestructura. |
| `docs/02-fase3-desarrollo-funcional.md` | Ejecución local, módulos construidos, verificación. |
| `docs/03-fase4-integraciones.md` | SCORM 1.2/2004, xAPI, Rise 360 y Storyline 360, origen de contenido separado. |
| `docs/04-documentacion-tecnica.md` | **Punto de entrada técnico:** estructura, módulos, base de datos, autorización, pruebas, convenciones. |
| `docs/05-accesibilidad.md` | WCAG 2.2 AA: método, resultados y lista de comprobación manual. |
| `docs/06-rendimiento.md` | Mediciones, cuellos de botella y cómo repetirlas. |
| `docs/07-despliegue-y-operacion.md`, `docs/runbook.md` | Despliegue, copias de seguridad, mantenimiento, incidentes. |
| `docs/08-seguridad.md` | Revisión de seguridad: hallazgos, estado y riesgos aceptados. |

## Lo más importante que NO está probado

- Los recorridos de navegador (`apps/web/e2e/`) no cubren todavía paquetes con varios SCO, carga directa a S3 desde el navegador, PDF de certificados ni cmi5; esas funciones solo tienen pruebas de integración.
- Exportaciones reales de Articulate Rise 360 y Storyline 360 (todas las pruebas usan paquetes sintéticos).
- Un LRS real, una infraestructura gestionada con TLS, la imagen Docker y la integración continua.
- Accesibilidad con lector de pantalla y personas usuarias; una auditoría de seguridad humana.
- Directus no está integrado: las secciones «Quiénes somos», «Publicaciones» e «Historias» son páginas de contenido pendiente.
