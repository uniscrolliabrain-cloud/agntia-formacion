# FOR-C31 — Analítica de aprendizaje

**DESIGN_ONLY · NOT_STARTED · 31/42.** [Campaña original](../../../campaigns/31-analitica-de-aprendizaje.md). Esta rama es planificación, no implementación.

## Objetivo y autoridad
Construir/verificar analítica de aprendizaje para Formación empresarial, tutoría y aprendizaje verificable, preservando: Tiempo/engagement no equivalen competencia; sin ranking laboral oculto.

**Operación nominada:** `learning.analytics.snapshot`. **Campos:** metricDefinition, cohortScope, coverage, masteryEvidence. **Invariante:** Tiempo/engagement no equivalen competencia; sin ranking laboral oculto. **Depende de:** FOR-C30.

## Ownership y archivos propuestos (validar antes de crear)
- Dominio/adaptador: `packages/analytics/src/learning.ts`.
- DTO y validación: `packages/contracts/src/31.ts` cuando proceda.
- API Hono: `apps/api/src/routes/31.ts` solo si operación realmente expuesta/autorizada.
- Tests: `tests/campaigns/031.test.ts`, fixtures `tests/fixtures/031/`.
- Evidencias originales: `docs/implementation/c31/README.md`, `docs/implementation/c31/EVIDENCE.md`, `docs/implementation/c31/TESTS.md`, `docs/implementation/c31/RISKS.md`.
- Reporte Freebuff en este mismo documento, evidencias extensas enlazadas.

## Patchsets y aceptación por tarea
### 031.01 — FOR-C31-T01: Congelar fuentes, ámbito y autoridad
**Acción:** Cotejar metricDefinition, cohortScope, coverage, masteryEvidence con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** AuthorityMap y fixture explícitos; Tiempo/engagement no equivalen competencia; sin ranking laboral oculto. La ausencia de fuente genera pendiente, no un valor plausible.

**Dependencia:** inicio. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.02 — FOR-C31-T02: Definir DTO y frontera de datos
**Acción:** Diseñar esquema runtime para metricDefinition, cohortScope, coverage, masteryEvidence: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.

**Dependencia:** FOR-C31-T01. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.03 — FOR-C31-T03: Aplicar lógica determinista y revisión
**Acción:** Implementar o documentar el paso `learning.analytics.snapshot` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Muestra pequeña se agrega/minimiza sin identificar alumnos. No eval/SQL/shell/HTTP genérico del LLM.

**Dependencia:** FOR-C31-T02. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.04 — FOR-C31-T04: Adaptar con permisos mínimos
**Acción:** Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `learning.analytics.snapshot`.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.

**Dependencia:** FOR-C31-T03. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.05 — FOR-C31-T05: Vincular autorización y efectos
**Acción:** Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Cambiar metricDefinition o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.

**Dependencia:** FOR-C31-T04. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.06 — FOR-C31-T06: Ejecutar pruebas de negocio y fallo
**Acción:** Preparar y ejecutar caso específico: Muestra pequeña se agrega/minimiza sin identificar alumnos. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `learning.analytics.snapshot`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.

**Dependencia:** FOR-C31-T05. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 031.07 — FOR-C31-T07: Registrar evidencia y cerrar gate
**Acción:** Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente.

**Archivo primario:** `packages/analytics/src/learning.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

**Dependencia:** FOR-C31-T06. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.


## Wiring transversal
JWT Supabase+membresía → originTenant/targetTenant y mandato del twin → ACL alumno/curso/attempt → DTO Zod → policy/AuthorityMap → FSM/expectedVersion+aprobación → Postgres RLS+audit/outbox → worker scoped → adaptador Moodle/Open edX/LTI/xAPI tipado → receipt/reconciliación → bridge padre. Separar práctica de evaluación; no filtrar respuestas, no emitir certificados sin evidencia y autoridad. Derechos de contenidos, privacidad educativa y retención obligatorios. Ningún proveedor real se presupone disponible.

## Gates pendientes
- **FOR-C31-G01 / NOT_EXECUTED:** Muestra pequeña se agrega/minimiza sin identificar alumnos. **Esperado:** Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- **FOR-C31-G02 / NOT_EXECUTED:** Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta learning.analytics.snapshot.. **Esperado:** Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

**Bloqueos:** Cross-tenant o secretos expuestos; Approval/mandato/scope ampliados sin autorización; Pérdida de historia o duplicación tras timeout; Conclusión sensible sin fuentes/revisión competente.

**Rollback:** Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.

## Reporte Freebuff (rellenar al terminar)
Estado: PENDING. SHA: PENDING. Archivos/diff: PENDING. Tests/fixtures: PENDING. Gates: PENDING. Incoherencias/decisiones: PENDING. Riesgos/deuda: PENDING. Aprendizajes para siguientes campañas: PENDING. Continuar autónomamente; Codex audita después de C42.
