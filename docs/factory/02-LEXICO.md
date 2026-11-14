# Léxico y semántica canónica — Padre ↔ Formación

**Versión 0.1, audit parcial, NO copiar contratos del padre sin verificar SHA.** La misma palabra en dos repos no prueba la misma entidad. Los tipos de Formación son PROPOSED salvo prueba de código.

## Identidad, tenancy, agentes
- `tenantId`: empresa/ámbito de datos, opaco, verificado server-side. No es `owner`, `userId`, `sub` ni `actorId`.
- `owner`: ámbito legacy/canonical de algunas APIs del padre; bridge resuelve mapeo, nunca coerción.
- `Actor`: humano o agente, schema del padre en `packages/domain/src/actor.ts`.
- `HumanActor`: usuario con tenant/roles; la sesión JWT sola no prueba membership activa.
- `AgentActor`: `runtimeId`, `roleId`, `personaId?`, `kernelTurnId?`, `tenantId`. `agentActor` puede aceptar `actorId` como fallback de runtime; confirmar código.
- `PersonaRegistry.canStartWork(tenantId,personaId,{owner,sopId?})`: verificación parcial de activación/assignment/SOP; no autorización total.
- `TwinBinding`: **PROPOSED**, vínculo entre profesional de Formación y agente canónico, no registro paralelo de identidad.
- `WorkOrder`/`DelegationMandate`: **PROPOSED** mandato explícito con principal originador, scopes, propósito, expiración y presupuesto.

## Trabajo, eventos, evidencia
- `Task` ≠ `Job` ≠ `SOP` ≠ `Approval` ≠ `Event`.
- `correlationId`: identifica cadena causal empresarial y se propaga; `causationId`: evento que causa otro; `eventId`: evento nuevo único.
- `traceId` y `spanId`: telemetría técnica W3C/OTel, NO sustituye evento durable. `requestId`: request de entrada, no necesariamente cadena completa.
- `idempotencyKey`: clave de deduplicación de un efecto bajo tenant/capability/payload, no sinónimo de correlationId.
- `schemaVersion`: versión del envelope; el `SystemEvent` padre usa convención propia, verificar antes de mapear.
- `outcome_unknown`: resultado remoto ambiguo; reconciliar, no reintentar a ciegas.
- `EvidenceRecord`, `EffectReceipt`, `SourceRef`, `SourceHash`: prueba/refs y procedencia, no permiso.
- Estados de approvals observados en adapter padre: `awaiting_review`, `scheduled`, `executing`, `succeeded`, `failed`, `outcome_unknown`, `denied`, `cancelled`, `expired`. No introducir `approved` como estado nativo sin verificación.

## Formación y actualización
- `TrainingAgreement`: alcance formativo contractual, no autorización genérica de difusión.
- `LearningObjective`: resultado observable de aprendizaje, no KPI de marketing.
- `CompetencyMap`: competencias y prerequisitos, no perfil clínico ni ranking laboral.
- `Curriculum`/`CourseVersion`/`ContentVersion`: planes/curso/contenido con revisión y licencia.
- `Learner` ≠ `HumanActor`: un alumno no adquiere acceso empresarial por aparecer en un LMS.
- `Enrollment`: matrícula, no consentimiento de newsletter.
- `TutorSession`: tutoría; separar práctica y evaluación.
- `AssessmentSpec`, `Attempt`, `MasteryObservation`: reglas, intento, inferencia calibrada; no acreditación automática.
- `CompletionProposal`/`CredentialProposal`: propuestas sujetas a evidencia y revisión.
- `CompanyLearningProfile`, `TrainingNeedSignal`, `WeeklyLearningBrief`, `EducationalNewsletterRevision`, `LearningDeliveryIntent`, `AdoptionEvidence`: **PROPOSED NUEVO** para formación recurrente por empresa, no existen en el padre por presunción.
- `AuditFinding`: hallazgo de auditoría con procedencia, vigencia y revisión, no diagnóstico jurídico ni certeza.

## Nomenclatura de código
IDs opacos sin imponer UUID al padre; `*Id` identidad, `*Ref` referencia, `*Version` versión, `*Hash` integridad, `*At` timestamp. DTOs con Zod/JSON Schema en fronteras, discriminantes explícitos, enums cerrados y adapters versionados. `Proposal` ≠ `Intent` ≠ `Attempt` ≠ `Receipt`; `sent` ≠ `delivered` ≠ `read` ≠ `learned`. No convertir engagement en competencia.

## Fuentes y grado de certeza
`packages/domain/src/actor.ts`, `apps/server/src/engine/agents/personas/registry.ts`, `apps/server/src/engine/tenant.ts`, `apps/server/src/app.ts`, `apps/server/src/engine/assignments/adapters/approval-adapter.ts`: observación previa parcial del padre en SHA documentado. `docs/architecture/03-compatibilidad-agente.md` y `docs/research/parent-source-map.json`: mapas documentales. Contratos de eventos/SOP/DB/SDK requieren comprobación exhaustiva y tests. Toda discrepancia bloquea integración hasta ADR.
