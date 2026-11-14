# FOR-C01 — Patchsets de baseline documental (sin runtime)

**Objetivo:** preparar inventario reproducible; no escribir código, endpoints ni proveedores en esta fase. Los siguientes son ficheros futuros propuestos y deben comprobarse contra árbol real antes de ejecutar.

## P01 — Fuente de verdad y SHAs
Crear `docs/implementation/01-baseline-fuentes-y-alcance/BASELINE.md`: ownSHA, hostSHA, fecha, rama, paths existentes, scripts, licencias, permisos, test baseline. Leer `README.md`, `docs/research/parent-source-map.json`, `docs/campaigns/campaign.json`. Etiquetar CODE_VERIFIED/DOC_ONLY/PROPOSED.

## P02 — Matriz de contratos
Crear `docs/implementation/01-baseline-fuentes-y-alcance/PARENT-CONTRACT-MAP.md`: para cada `Actor`, `TenantService`, `SystemEvent`, `SOP`, `Task`, `Approval`, `Capability`, `Provenance`, incluir ruta, símbolo, firma, blob SHA, dependencia y compatibilidad con `docs/factory/02-LEXICO.md`. No importar código del padre a ciegas.

## P03 — Auditoría de documentación
Crear `docs/implementation/01-baseline-fuentes-y-alcance/DOC-DELTA.md`: comparar original 42 campañas con alcance semanal de Formación y ADTC; proponer ADR para nueva prioridad, sin reescribir manifiesto todavía. Marcar inconsistencias en rutas, referencias y contratos.

## P04 — Evidencias y gates
Crear `docs/implementation/01-baseline-fuentes-y-alcance/EVIDENCE.md`, `TESTS.md`, `RISKS.md`: comandos, salidas, tests, enlaces y riesgos reales. Validar que los 42 IDs de `campaign.json` tienen documento original y scaffold; confirmar que no se tocó `agente`, main ni proveedores.

## Gate
FOR-C01-G01: si hostSHA cambia, bloquear mapping hasta cotejar. FOR-C01-G02: rechazar principal/mandato ajeno, sin acceso externo. Cualquier prueba no ejecutada se marca NOT_VERIFIED. Rollback: revertir solo cambios documentales propios; conservar evidencia.
