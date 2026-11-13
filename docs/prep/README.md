# PREP — Inventario y conservación de documentación preexistente

**2026-11-13 | Estado: BASELINE DOCUMENTAL.** El repositorio NO está vacío: ya contiene README, documentos de producto/arquitectura/contratos/seguridad/UX/investigación, un manifiesto de **42 campañas / 294 tareas / 84 gates**, documentos por campaña, release y operations. Todos indican diseño, no código ejecutado. El tamaño 0 KB informado por el listado de GitHub NO implica ausencia de documentación.

## Fuentes actuales (no mover ni borrar)
- `README.md`; `docs/01-producto.md` a `docs/09-evaluacion.md`.
- `docs/architecture/01-arquitectura.md`, `02-identidad-twins.md`, `03-compatibilidad-agente.md`, `04-runtime.md`.
- `docs/contracts/01-contratos.md`; `docs/campaigns/README.md`, `campaign.json` y los 42 documentos originales.
- `docs/research/sources.json`, `repositories.json`, `parent-source-map.json`.
- `docs/release/HANDOFF.md`, `INFORME-AL-OWNER.md`, `PILOT-ACCEPTANCE.md`, `document-validation.json`; `docs/operations/RUNBOOK.md`.

## Diagnóstico
**Fortalezas:** límites, privacidad, LMS, tutor, evidencias, contratos propuestos, autoridad, trazabilidad, gates, fuentes y mapas al padre ya documentados. **Huecos respecto al alcance actual:** formación semanal por empresa, newsletter educativa, contenido hiperpersonalizado, auditoría tecnológica recurrente, actualización profesional/soft skills, cooperación Marketing/Redes/Clientes, observabilidad distribuida de toda la familia, handoffs diferenciados por campaña y patchsets exactos. No sustituir la documentación educativa por marketing genérico.

## Política de preservación
Este índice representa el área `prep/`. No se ha efectuado migración física para no romper rutas del manifiesto y enlaces relativos. Migración opcional posterior: inventario exhaustivo y snapshot por SHA → copiar → reescribir links/manifest → validar → borrar originales en commit separado. Hasta entonces, documentos originales = baseline; adendas `docs/factory/` = contrato de trabajo nuevo; conflictos se registran, no se silencian.

## Estado y limitaciones
Lectura selectiva por GitHub, sin checkout ni suite ejecutada. El SHA padre fijado en documentos originales es `54b8d5407a8576459448c4d059a877297d18ca7a`; **revalidar antes de código**. El alcance nuevo procede del founder; su incorporación a docs no equivale a funcionalidades existentes.
