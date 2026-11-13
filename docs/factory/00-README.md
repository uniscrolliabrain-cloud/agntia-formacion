# Agntia Engineering Factory — perfil Formación

**factoryVersion: 0.1.0 | SPEC/DRAFT | 2026-11-13**

La fábrica estandariza documentación, semántica, identidades, observabilidad, handoffs y gates; **no impone la misma implementación ni las mismas 42 campañas a todos los repositorios**. En Formación se conservan las 42 campañas existentes y se enriquecen.

## Orden de lectura obligatorio (todos los roles)
1. `docs/factory/00-README.md`, `01-PIPELINE.md`, `02-LEXICO.md`, `03-TRACE-OBSERVABILITY.md`, `04-PRODUCTO-CONTINUO.md`, `05-INTERFACES-DEPENDENCIAS.md`.
2. `docs/prep/README.md` y documentos originales de arquitectura, contratos, producto, seguridad y fuentes.
3. `docs/campaigns/campaign.json` y campaña original.
4. `docs/implementation/NN-*/README.md` + los tres handoffs.
5. Documentación y resultados de campaña N−1, N y contexto de N+1; SHA del padre y diffs relevantes.
6. `docs/factory/06-READINESS-AUDIT.md` y decisiones abiertas.

## Jerarquía de evidencia
Código y pruebas ejecutadas al SHA > contratos fuente verificados > documentos del padre > docs del servicio > propuesta. Los documentos antiguos no prueban capacidad real. `PROPOSED`, `VERIFIED_CODE`, `VERIFIED_TEST`, `DOC_ONLY`, `STALE` y `UNKNOWN` son etiquetas obligatorias en mapas de contratos.

## Guardrails
Deny-by-default; fail-closed; tenant/ACL en cada acceso, job, RAG y export; autorización humana para efectos sensibles; LLM propone, kernel/policy dispone; persistencia durable, outbox, idempotencia, reconciliación de outcome_unknown; audit append-only; datos minimizados; no secret/PII en logs; no alterar padre, main ni desplegar sin aprobación del founder.

## Gobernanza
Un writer por superficie, rama por campaña, reviewer independiente por SHA congelado. Arquitecto resuelve conflictos de contratos; founder autoriza merges/cambios de alcance. Cada cambio semántico actualiza léxico/ADR y test de compatibilidad. Una campaña no está READY por tener scaffold.

## Reutilización
`factoryVersion` identifica versión de la plantilla; `domainProfile=formacion` identifica adaptaciones. Actualizaciones de factory requieren revisión de compatibilidad, nunca sobrescribir adendas locales automáticamente.
