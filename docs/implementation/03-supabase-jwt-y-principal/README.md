# FOR-C03 — Supabase JWT y principal

**SCAFFOLD, NOT READY.** No implementar basándose solo en este índice. Documento original: [docs/campaigns/03-supabase-jwt-y-principal.md](../../campaigns/03-supabase-jwt-y-principal.md). Factory: [reglas](../../factory/00-README.md), [pipeline](../../factory/01-PIPELINE.md), [léxico](../../factory/02-LEXICO.md), [ADTC](../../factory/03-TRACE-OBSERVABILITY.md), [producto semanal](../../factory/04-PRODUCTO-CONTINUO.md). Leer N−1, N y N+1 antes de actuar.

## Objetivo
Construir/verificar supabase jwt y principal para Formación empresarial, tutoría y aprendizaje verificable, preservando: JWT válido sin membresía/scope no autoriza; no user_metadata/default.

## Operación y contrato (PROPUESTOS)
`auth.verify` · campos `sub, tenant_id, membership, resourceACL, capability` · fuentes H01, S01, S02, P01. No asumir que existen en código. Dependencias: FOR-C02.

## Invariante
JWT válido sin membresía/scope no autoriza; no user_metadata/default

## Tareas originales para descomponer
- **FOR-C03-T01 Congelar fuentes, ámbito y autoridad** — Cotejar sub, tenant_id, membership, resourceACL, capability con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo. **Aceptación:** AuthorityMap y fixture explícitos; JWT válido sin membresía/scope no autoriza; no user_metadata/default. La ausencia de fuente genera pendiente, no un valor plausible.
- **FOR-C03-T02 Definir DTO y frontera de datos** — Diseñar esquema runtime para sub, tenant_id, membership, resourceACL, capability: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII. **Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.
- **FOR-C03-T03 Aplicar lógica determinista y revisión** — Implementar o documentar el paso `auth.verify` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno. **Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; TokenA con recursoB falla sin revelar metadatos. No eval/SQL/shell/HTTP genérico del LLM.
- **FOR-C03-T04 Adaptar con permisos mínimos** — Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `auth.verify`. **Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.
- **FOR-C03-T05 Vincular autorización y efectos** — Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key. **Aceptación:** Cambiar sub o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.
- **FOR-C03-T06 Ejecutar pruebas de negocio y fallo** — Preparar y ejecutar caso específico: TokenA con recursoB falla sin revelar metadatos. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `auth.verify`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad. **Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.
- **FOR-C03-T07 Registrar evidencia y cerrar gate** — Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente. **Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

## Gates no ejecutados
- FOR-C03-G01: TokenA con recursoB falla sin revelar metadatos — Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- FOR-C03-G02: Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta auth.verify. — Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

## Artefactos planeados, NO presentes por este listado
- `docs/implementation/c03/README.md`
- `docs/implementation/c03/EVIDENCE.md`
- `docs/implementation/c03/TESTS.md`
- `docs/implementation/c03/RISKS.md`

## Handoffs requeridos
- `HANDOFF-FREEBUFF.md`: patchsets, archivos, tests y riesgos
- `HANDOFF-CODEX.md`: auditoría independiente y pruebas negativas
- `HANDOFF-ARCHITECT-FOUNDER.md`: autoridad, contratos y decisión

**Gate BLOCKED** hasta inventario de código real al SHA, rutas/funciones exactas, patchsets, tres handoffs, tests y aprobación. Rollback original: Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.
