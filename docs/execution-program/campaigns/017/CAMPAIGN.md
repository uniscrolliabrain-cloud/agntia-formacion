# FOR-C17 — Contenido H5P/Adapt

**DESIGN_ONLY · NOT_STARTED · 17/42.** [Campaña original](../../../campaigns/17-contenido-h5p-adapt.md). Esta rama es planificación, no implementación.

## Objetivo y autoridad
Construir/verificar contenido h5p/adapt para Formación empresarial, tutoría y aprendizaje verificable, preservando: Contenido activo aislado, sin scripts/red libres.

**Operación nominada:** `learning.interactive.preview`. **Campos:** packageHash, libraries, dependencies, licenseRefs. **Invariante:** Contenido activo aislado, sin scripts/red libres. **Depende de:** FOR-C16.

## Ownership y archivos propuestos (validar antes de crear)
- Dominio/adaptador: `packages/adapters/src/h5p-adapt.ts`.
- DTO y validación: `packages/contracts/src/17.ts` cuando proceda.
- API Hono: `apps/api/src/routes/17.ts` solo si operación realmente expuesta/autorizada.
- Tests: `tests/campaigns/017.test.ts`, fixtures `tests/fixtures/017/`.
- Evidencias originales: `docs/implementation/c17/README.md`, `docs/implementation/c17/EVIDENCE.md`, `docs/implementation/c17/TESTS.md`, `docs/implementation/c17/RISKS.md`.
- Reporte Freebuff en este mismo documento, evidencias extensas enlazadas.

## Patchsets y aceptación por tarea
### 017.01 — FOR-C17-T01: Congelar fuentes, ámbito y autoridad
**Acción:** Cotejar packageHash, libraries, dependencies, licenseRefs con originales, contrato del tenant y versiones de fuente/proveedor. Registrar qué es hecho, declaración, inferencia o desconocido; revisar alcance territorial/temporal y reglas del módulo.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** AuthorityMap y fixture explícitos; Contenido activo aislado, sin scripts/red libres. La ausencia de fuente genera pendiente, no un valor plausible.

**Dependencia:** inicio. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.02 — FOR-C17-T02: Definir DTO y frontera de datos
**Acción:** Diseñar esquema runtime para packageHash, libraries, dependencies, licenseRefs: tipos, límites, IDs opacos, enums, fechas y versión. Conservar los campos nativos aplicables y declarar nuevos los del servicio. Aislar tenant/proyecto/recurso y minimizar PII.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Round-trip y rechazo de extra/valor inválido; referencias cruzadas no son posibles; source/actor/updatedAt y EvidenceRef preservados donde correspondan.

**Dependencia:** FOR-C17-T01. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.03 — FOR-C17-T03: Aplicar lógica determinista y revisión
**Acción:** Implementar o documentar el paso `learning.interactive.preview` mediante guards, estados y expectedVersion/CAS. Separar propuesta del modelo de cálculo/decisión verificables. LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El estado final, el protegido y los motivos de bloqueo son comprobables; Paquete malicioso o licencia insuficiente queda cuarentena. No eval/SQL/shell/HTTP genérico del LLM.

**Dependencia:** FOR-C17-T02. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.04 — FOR-C17-T04: Adaptar con permisos mínimos
**Acción:** Comprobar versión/edición/ACL de backend si esta fase lo usa; fields/métodos allowlist y binding de servidor. Si es fase local/documental no añadir HTTP. Normalizar errores y limitar IO/tamaño/tiempo/coste de `learning.interactive.preview`.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Unknown/unsupported/forbidden no se simulan como éxito; cero HTTP con principal o conexión no autorizados; prueba fake no habilita capability real.

**Dependencia:** FOR-C17-T03. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.05 — FOR-C17-T05: Vincular autorización y efectos
**Acción:** Crear preview sin efecto remoto, diff/hash de datos y revisión; identificar quién acepta el resultado y quién puede ejecutar. Si hay efecto, exigir policy/approval/mandato vigentes y un único intent durable con idempotency key.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** Cambiar packageHash o materialidad del payload invalida la autorización aplicable. Replay igual no duplica; distinto contenido con misma key da conflicto.

**Dependencia:** FOR-C17-T04. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.06 — FOR-C17-T06: Ejecutar pruebas de negocio y fallo
**Acción:** Preparar y ejecutar caso específico: Paquete malicioso o licencia insuficiente queda cuarentena. Añadir A/B/P, humano/agente/colaborador, revocación, dato sin fuente, cambio concurrente y crash pertinente a `learning.interactive.preview`. Verificar ausencia de efectos prohibidos: Una evaluación recibe respuesta filtrada o un alumno deB aparece en analyticsA; se emite certificado sin evidencia/autoridad.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** El contrato estricto exige resultado correcto y trayectoria segura. Test fallido crítico bloquea; sin entorno se registra NOT_VERIFIED, nunca PASS por un mock.

**Dependencia:** FOR-C17-T05. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.

### 017.07 — FOR-C17-T07: Registrar evidencia y cerrar gate
**Acción:** Guardar SHA/diff, versiones, fixture antes/después, actor/mandato/correlación, fuentes y receipts mínimos. Registrar tests reales y coste/latencia cuando existan. Actualizar riesgos, rollback y siguiente dependencia sin escribir en agente.

**Archivo primario:** `packages/adapters/src/h5p-adapt.ts`. Separar DTO/servicio/adaptador/worker/test según arquitectura real, registrar imports y exports. No crear HTTP para tareas documentales.

**Aceptación:** EVIDENCE/TESTS/RISKS y decisión de gate revisables; ninguna cifra, firma, actividad o integración inventadas. Mantener fuera del repo público PII, credenciales y originales restringidos.

**Dependencia:** FOR-C17-T06. **Verificación:** fixture positivo, rechazo cross-tenant y permisos, revocación, cambios concurrentes y timeout/replay si hay efectos; guardar SHA/comando/resultado.


## Wiring transversal
JWT Supabase+membresía → originTenant/targetTenant y mandato del twin → ACL alumno/curso/attempt → DTO Zod → policy/AuthorityMap → FSM/expectedVersion+aprobación → Postgres RLS+audit/outbox → worker scoped → adaptador Moodle/Open edX/LTI/xAPI tipado → receipt/reconciliación → bridge padre. Separar práctica de evaluación; no filtrar respuestas, no emitir certificados sin evidencia y autoridad. Derechos de contenidos, privacidad educativa y retención obligatorios. Ningún proveedor real se presupone disponible.

## Gates pendientes
- **FOR-C17-G01 / NOT_EXECUTED:** Paquete malicioso o licencia insuficiente queda cuarentena. **Esperado:** Resultado y estado protegido coherentes con invariante, revisión/receipt donde correspondan.
- **FOR-C17-G02 / NOT_EXECUTED:** Principal/mandato inválido, recurso o conexión de otro tenant, o versión cambiada intenta learning.interactive.preview.. **Esperado:** Fail-closed antes de leer/actuar remotamente; sin fuga o ampliación de scope, con intento auditado.

**Bloqueos:** Cross-tenant o secretos expuestos; Approval/mandato/scope ampliados sin autorización; Pérdida de historia o duplicación tras timeout; Conclusión sensible sin fuentes/revisión competente.

**Rollback:** Deshabilitar capacidad o flag y detener efectos nuevos; conservar audit, links, intents, snapshots y receipts. Restore probado con restricciones/supresiones reaplicadas; no borrar efectos remotos para fingir reversión.

## Reporte Freebuff (rellenar al terminar)
Estado: PENDING. SHA: PENDING. Archivos/diff: PENDING. Tests/fixtures: PENDING. Gates: PENDING. Incoherencias/decisiones: PENDING. Riesgos/deuda: PENDING. Aprendizajes para siguientes campañas: PENDING. Continuar autónomamente; Codex audita después de C42.
