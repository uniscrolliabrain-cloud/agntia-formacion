# FOR-C01 — Baseline, fuentes y alcance

**SCAFFOLD, NOT READY.** No implementar basándose solo en este índice. Documento original: [docs/campaigns/01-baseline-fuentes-y-alcance.md](../../campaigns/01-baseline-fuentes-y-alcance.md). Factory: [reglas](../../factory/00-README.md), [pipeline](../../factory/01-PIPELINE.md), [léxico](../../factory/02-LEXICO.md), [ADTC](../../factory/03-TRACE-OBSERVABILITY.md), [producto semanal](../../factory/04-PRODUCTO-CONTINUO.md). Leer N−1, N y N+1 antes de actuar.

## Objetivo
Construir/verificar baseline, fuentes y alcance para Formación empresarial, tutoría y aprendizaje verificable, preservando: No modificar agente ni convertir documentos en pruebas pasadas.

## Operación y contrato (PROPUESTOS)
`baseline.capture` · campos `hostSHA, ownSHA, sourceRef, version, permissions` · fuentes H01, S01, S02, P01. No asumir que existen en código. Dependencias: ninguna.

## Invariante
No modificar agente ni convertir documentos en pruebas pasadas

## Tareas originales para descomponer
- **FOR-C01-T01 Congelar fuentes, ámbito y autoridad** — Cotejar hostSHA, ownSHA, sourceRef, version, permissions con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo. **Aceptación:** AuthorityMap y fixture explícitos; No modificar agente ni convertir documentos en pruebas pasadas. La ausencia de fuente genera pendiente, no un valor plausible.
- **FOR-C01-T02 Definir DTO y frontera de datos** — Diseñar esquema runtime para hostSHA, ownSHA, sourceRef, version, permissions: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII. **Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.
- **FOR-C01-T03 Aplicar lógica determinista y revisión** — Implementar o documentar el paso `baseline.capture` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno. **Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Cambio del padre obliga cotejar antes de integrar. No eval/SQL/shell/HTTP genérico del LLM.
- **FOR-C01-T04 Adaptar con permisos mínimos** — Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `baseline.capture`. **Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.
- **FOR-C01-T05 Vincular autorización y efectos** — Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key. **Aceptación:** Cambiar hostSHA o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.
- **FOR-C01-T06 Ejecutar pruebas de negocio y fallo** — Preparar y ejecutar caso específico: Cambio del padre obliga cotejar antes de integrar. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `baseline.capture`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad. **Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.
- **FOR-C01-T07 Registrar evidencia y cerrar gate** — Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente. **Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

## Gates no ejecutados
- FOR-C01-G01: Cambio del padre obliga cotejar antes de integrar — Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- FOR-C01-G02: Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta baseline.capture. — Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

## Artefactos planeados, NO presentes por este listado
- `docs/implementation/c01/README.md`
- `docs/implementation/c01/EVIDENCE.md`
- `docs/implementation/c01/TESTS.md`
- `docs/implementation/c01/RISKS.md`

## Handoffs requeridos
- `HANDOFF-FREEBUFF.md`: patchsets, archivos, tests y riesgos
- `HANDOFF-CODEX.md`: auditoría independiente y pruebas negativas
- `HANDOFF-ARCHITECT-FOUNDER.md`: autoridad, contratos y decisión

**Gate BLOCKED** hasta inventario de código real al SHA, rutas/funciones exactas, patchsets, tres handoffs, tests y aprobación. Rollback original: Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.
