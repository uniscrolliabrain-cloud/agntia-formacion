# Pipeline síncrono escalonado — Freebuff / Codex / Arquitecto + Founder

## Roles y propiedad
**Freebuff** implementa exclusivamente en `feat/for-cNN-...`; prepara patchsets, tests, fixtures, migraciones, rollback y evidencias. **Codex** revisa SHA congelado sin editar la rama de Freebuff; corre typecheck/lint/tests, negativos y contratos, y emite findings. **ChatGPT + founder** ejercen arquitectura, arbitraje de contratos, diseño transversal y aprobación humana final. El arquitecto no simula aprobación del founder.

## Estados
`NOT_STARTED → SPEC_READY → READY → IMPLEMENTING → READY_FOR_REVIEW → REVIEWING → VERIFIED → ARCH_REVIEW → FOUNDER_APPROVAL → MERGED`; alternativas `BLOCKED`, `CHANGES_REQUESTED`, `NOT_VERIFIED`, `FAILED`. Nunca traducir `NOT_EXECUTED` a PASS.

## Cadencia
Freebuff N puede solaparse con Codex N−1 **solo si** no consume un contrato pendiente de N−1. Arquitecto puede preparar N+1 sin autorizar ejecución. Gate de dependencia: un merge verificado o contrato estable explícitamente versionado. Checkpoints cada cinco campañas y cuando cambie una frontera de autoridad/tenant.

## Artefactos por campaña
`README.md` (scope, dependencias, invariantes, contexto N−1/N/N+1), `PATCHSETS.md` (archivo exacto, crear/modificar, firma, wiring, tests, migración, rollback), `HANDOFF-FREEBUFF.md`, `HANDOFF-CODEX.md`, `HANDOFF-ARCHITECT-FOUNDER.md`, `ACCEPTANCE.md`, `EVIDENCE.md`, `REVIEW.md`, `DECISION.md`. Solo crear archivos de resultados al tener resultados reales; no rellenar PASS ficticios.

## Handoff Freebuff
Entradas: SHA de base, mapa de archivos y contratos, owner de superficies, dependencias, prohibiciones. Salidas: diff, commits, comandos/exit codes, tests, screenshots si procede, riesgos, rollback y notas de migración. No modificar otro repo sin autorización.

## Handoff Codex
Entradas: SHA inmutable, objetivos/gates, fixtures y tests negativos. Salidas: informe con severidad P0–P3, reproducción, cobertura y estado. Rechazar cross-tenant, bypass, efectos duplicados, pérdidas de evidencia, filtraciones, schema drift y dependencias no resueltas.

## Handoff Architect/Founder
Arquitecto: semántica, autoridad, APIs/eventos, integración, riesgos y decisión técnica. Founder: aceptación o rechazo explícito de merge, permisos externos, gastos, deploys y cambios en el padre. Merge != deploy.

## Bloqueos
Sin entorno verificable, tests críticos, principal verificado, mandato, approval, budget, proveedor sandbox o evidencia de reconciliación → BLOCKED/NOT_VERIFIED. No confiar en mocks para afirmar producción. El revisor debe poder reproducir el proceso con un solo handoff y sin preguntas arquitectónicas abiertas.
