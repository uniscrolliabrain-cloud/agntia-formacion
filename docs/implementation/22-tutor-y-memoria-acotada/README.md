# FOR-C22 — Tutor y memoria acotada

**SCAFFOLD, NOT READY.** Documento original: [campaña](../../campaigns/22-tutor-y-memoria-acotada.md). Lectura obligatoria: [factory](../../factory/00-README.md), [pipeline](../../factory/01-PIPELINE.md), [léxico](../../factory/02-LEXICO.md), [ADTC](../../factory/03-TRACE-OBSERVABILITY.md), [formación continua](../../factory/04-PRODUCTO-CONTINUO.md), N−1/N/N+1.

## Objetivo
Construir/verificar tutor y memoria acotada para Formación empresarial, tutoría y aprendizaje verificable, preservando: Sin memoria compartida entre clientes o alumnos.

## Operación y datos propuestos
`learning.tutor.propose` · sessionScope, learnerGoal, allowedHints, retention. Dependencias: FOR-C21. Fuentes: H01, S01, S02, P01. No asumir implementación.

## Invariante
Sin memoria compartida entre clientes o alumnos

## Tareas originales a granularizar
- **FOR-C22-T01 Congelar fuentes, ámbito y autoridad** — Cotejar sessionScope, learnerGoal, allowedHints, retention con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo. **Aceptación:** AuthorityMap y fixture explícitos; Sin memoria compartida entre clientes o alumnos. La ausencia de fuente genera pendiente, no un valor plausible.
- **FOR-C22-T02 Definir DTO y frontera de datos** — Diseñar esquema runtime para sessionScope, learnerGoal, allowedHints, retention: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII. **Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.
- **FOR-C22-T03 Aplicar lógica determinista y revisión** — Implementar o documentar el paso `learning.tutor.propose` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno. **Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Pregunta adversarial intenta obtener evidencias de otro alumno. No eval/SQL/shell/HTTP genérico del LLM.
- **FOR-C22-T04 Adaptar con permisos mínimos** — Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `learning.tutor.propose`. **Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.
- **FOR-C22-T05 Vincular autorización y efectos** — Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key. **Aceptación:** Cambiar sessionScope o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.
- **FOR-C22-T06 Ejecutar pruebas de negocio y fallo** — Preparar y ejecutar caso específico: Pregunta adversarial intenta obtener evidencias de otro alumno. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `learning.tutor.propose`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad. **Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.
- **FOR-C22-T07 Registrar evidencia y cerrar gate** — Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente. **Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

## Gates no ejecutados
- FOR-C22-G01: Pregunta adversarial intenta obtener evidencias de otro alumno — Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- FOR-C22-G02: Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta learning.tutor.propose. — Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

## Artefactos previstos (no creados)
- `docs/implementation/c22/README.md`
- `docs/implementation/c22/EVIDENCE.md`
- `docs/implementation/c22/TESTS.md`
- `docs/implementation/c22/RISKS.md`

## Handoffs pendientes
`HANDOFF-FREEBUFF.md` · `HANDOFF-CODEX.md` · `HANDOFF-ARCHITECT-FOUNDER.md`.

**BLOCKED** hasta verificar rutas reales, contratos, patchsets por fichero, tests, gates y tres handoffs. Rollback: Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.
