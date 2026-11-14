# FOR-C33 — Reportes, dashboard e infografías

**DESIGN_ONLY · NOT_STARTED · 33/42.** [Campaña original](../../../campaigns/33-reportes-dashboard-e-infografias.md). Esta rama es planificación, no implementación.

## Objetivo y autoridad
Construir/verificar reportes, dashboard e infografías para Formación empresarial, tutoría y aprendizaje verificable, preservando: No inventar cifras/fechas/estado completado.

**Operación nominada:** `report.snapshot`. **Campos:** snapshotId, metricDefinition, sourceRefs, coverage, hash. **Invariante:** No inventar cifras/fechas/estado completado. **Depende de:** FOR-C32.

## Ownership y archivos propuestos (validar antes de crear)
- Dominio/adaptador: `apps/web/src/views/LearningDashboard.tsx`.
- DTO y validación: `packages/contracts/src/33.ts` cuando proceda.
- API Hono: `apps/api/src/routes/33.ts` solo si operación realmente expuesta/autorizada.
- Tests: `tests/campaigns/033.test.ts`, fixtures `tests/fixtures/033/`.
- Evidencias originales: `docs/implementation/c33/README.md`, `docs/implementation/c33/EVIDENCE.md`, `docs/implementation/c33/TESTS.md`, `docs/implementation/c33/RISKS.md`.
- Reporte Freebuff en este mismo documento, evidencias extensas enlazadas.

## Patchsets y aceptación por tarea
### 033.01 — FOR-C33-T01: Congelar fuentes, ámbito y autoridad
**Acción:** Cotejar snapshotId, metricDefinition, sourceRefs, coverage, hash con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** AuthorityMap y fixture explícitos; No inventar cifras/fechas/estado completado. La ausencia de fuente genera pendiente, no un valor plausible.

**Dependencia:** inicio. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.02 — FOR-C33-T02: Definir DTO y frontera de datos
**Acción:** Diseñar esquema runtime para snapshotId, metricDefinition, sourceRefs, coverage, hash: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.

**Dependencia:** FOR-C33-T01. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.03 — FOR-C33-T03: Aplicar lógica determinista y revisión
**Acción:** Implementar o documentar el paso `report.snapshot` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Dato tardío cambia revisión, no informe aceptado silenciosamente. No eval/SQL/shell/HTTP genérico del LLM.

**Dependencia:** FOR-C33-T02. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.04 — FOR-C33-T04: Adaptar con permisos mínimos
**Acción:** Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `report.snapshot`.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.

**Dependencia:** FOR-C33-T03. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.05 — FOR-C33-T05: Vincular autorización y efectos
**Acción:** Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Cambiar snapshotId o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.

**Dependencia:** FOR-C33-T04. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.06 — FOR-C33-T06: Ejecutar pruebas de negocio y fallo
**Acción:** Preparar y ejecutar caso específico: Dato tardío cambia revisión, no informe aceptado silenciosamente. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `report.snapshot`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.

**Dependencia:** FOR-C33-T05. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 033.07 — FOR-C33-T07: Registrar evidencia y cerrar gate
**Acción:** Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente.

**Archivo primario:** `apps/web/src/views/LearningDashboard.tsx`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

**Dependencia:** FOR-C33-T06. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.


## Wiring transversal
JWT Supabase+membresía → originTenant/targetTenant y mandato del twin → ACL alumno/curso/attempt → DTO Zod → policy/AuthorityMap → FSM/expectedVersion+aprobación → Postgres RLS+audit/outbox → worker scoped → adaptador Moodle/Open edX/LTI/xAPI tipado → receipt/reconciliación → bridge padre. Separar práctica de evaluación; no filtrar respuestas, no emitir certificados sin evidencia y autoridad. Derechos de contenidos, privacidad educativa y retención obligatorios. Ningún proveedor real se presupone disponible.

## Gates pendientes
- **FOR-C33-G01 / NOT_EXECUTED:** Dato tardío cambia revisión, no informe aceptado silenciosamente. **Esperado:** Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- **FOR-C33-G02 / NOT_EXECUTED:** Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta report.snapshot.. **Esperado:** Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

**Bloqueos:** Cross-tenant o secretos expuestos; Approval/mandato/scope ampliados sin autorización; Pérdida de historia o duplicación tras timeout; Conclusión sensible sin fuentes/revisión competente.

**Rollback:** Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.

## Reporte Freebuff (rellenar al terminar)
Estado: PENDING. SHA: PENDING. Archivos/diff: PENDING. Tests/fixtures: PENDING. Gates: PENDING. Incoherencias/decisiones: PENDING. Riesgos/deuda: PENDING. Aprendizajes para siguientes campañas: PENDING. Continuar autónomamente; Codex audita después de C42.
