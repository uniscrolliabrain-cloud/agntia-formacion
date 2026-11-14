# FOR-C18 — LTI y lanzamiento

**DESIGN_ONLY · NOT_STARTED · 18/42.** [Campaña original](../../../campaigns/18-lti-y-lanzamiento.md). Esta rama es planificación, no implementación.

## Objetivo y autoridad
Construir/verificar lti y lanzamiento para Formación empresarial, tutoría y aprendizaje verificable, preservando: JWT LTI no sustituye Supabase ni tenant local sin mapping.

**Operación nominada:** `learning.lti.validate`. **Campos:** issuer, clientId, deploymentId, nonce, resourceLink. **Invariante:** JWT LTI no sustituye Supabase ni tenant local sin mapping. **Depende de:** FOR-C17.

## Ownership y archivos propuestos (validar antes de crear)
- Dominio/adaptador: `packages/adapters/src/lti.ts`.
- DTO y validación: `packages/contracts/src/18.ts` cuando proceda.
- API Hono: `apps/api/src/routes/18.ts` solo si operación realmente expuesta/autorizada.
- Tests: `tests/campaigns/018.test.ts`, fixtures `tests/fixtures/018/`.
- Evidencias originales: `docs/implementation/c18/README.md`, `docs/implementation/c18/EVIDENCE.md`, `docs/implementation/c18/TESTS.md`, `docs/implementation/c18/RISKS.md`.
- Reporte Freebuff en este mismo documento, evidencias extensas enlazadas.

## Patchsets y aceptación por tarea
### 018.01 — FOR-C18-T01: Congelar fuentes, ámbito y autoridad
**Acción:** Cotejar issuer, clientId, deploymentId, nonce, resourceLink con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** AuthorityMap y fixture explícitos; JWT LTI no sustituye Supabase ni tenant local sin mapping. La ausencia de fuente genera pendiente, no un valor plausible.

**Dependencia:** inicio. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.02 — FOR-C18-T02: Definir DTO y frontera de datos
**Acción:** Diseñar esquema runtime para issuer, clientId, deploymentId, nonce, resourceLink: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.

**Dependencia:** FOR-C18-T01. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.03 — FOR-C18-T03: Aplicar lógica determinista y revisión
**Acción:** Implementar o documentar el paso `learning.lti.validate` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Launch de deploymentB hacia tenantA rechazado. No eval/SQL/shell/HTTP genérico del LLM.

**Dependencia:** FOR-C18-T02. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.04 — FOR-C18-T04: Adaptar con permisos mínimos
**Acción:** Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `learning.lti.validate`.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.

**Dependencia:** FOR-C18-T03. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.05 — FOR-C18-T05: Vincular autorización y efectos
**Acción:** Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Cambiar issuer o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.

**Dependencia:** FOR-C18-T04. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.06 — FOR-C18-T06: Ejecutar pruebas de negocio y fallo
**Acción:** Preparar y ejecutar caso específico: Launch de deploymentB hacia tenantA rechazado. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `learning.lti.validate`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.

**Dependencia:** FOR-C18-T05. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 018.07 — FOR-C18-T07: Registrar evidencia y cerrar gate
**Acción:** Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente.

**Archivo primario:** `packages/adapters/src/lti.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

**Dependencia:** FOR-C18-T06. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.


## Wiring transversal
JWT Supabase+membresía → originTenant/targetTenant y mandato del twin → ACL alumno/curso/attempt → DTO Zod → policy/AuthorityMap → FSM/expectedVersion+aprobación → Postgres RLS+audit/outbox → worker scoped → adaptador Moodle/Open edX/LTI/xAPI tipado → receipt/reconciliación → bridge padre. Separar práctica de evaluación; no filtrar respuestas, no emitir certificados sin evidencia y autoridad. Derechos de contenidos, privacidad educativa y retención obligatorios. Ningún proveedor real se presupone disponible.

## Gates pendientes
- **FOR-C18-G01 / NOT_EXECUTED:** Launch de deploymentB hacia tenantA rechazado. **Esperado:** Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- **FOR-C18-G02 / NOT_EXECUTED:** Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta learning.lti.validate.. **Esperado:** Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

**Bloqueos:** Cross-tenant o secretos expuestos; Approval/mandato/scope ampliados sin autorización; Pérdida de historia o duplicación tras timeout; Conclusión sensible sin fuentes/revisión competente.

**Rollback:** Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.

## Reporte Freebuff (rellenar al terminar)
Estado: PENDING. SHA: PENDING. Archivos/diff: PENDING. Tests/fixtures: PENDING. Gates: PENDING. Incoherencias/decisiones: PENDING. Riesgos/deuda: PENDING. Aprendizajes para siguientes campañas: PENDING. Continuar autónomamente; Codex audita después de C42.
