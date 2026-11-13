# Arquitectura y autoridad

Propuesta TypeScript/Hono/pnpm con contratos runtime, core determinista, Postgres/Supabase, workers/outbox y adaptadores. Procesos especializados aislados cuando el dominio lo requiera; no importar servidor padre entero como librería ni duplicar su OS empresarial. No implementado.

```mermaid
flowchart TD
 U[Humano o portal externo] --> Auth[Supabase JWT y membership/ACL]
 P[agente: identidad canónica y runtime] --> B[Bridge privado y mandato]
 Auth --> API[API Hono nominada]
 B --> API
 API --> Core[Policy, revisiones, FSM y cálculo]
 Core --> DB[(Postgres: RLS, audit, inbox y outbox)]
 Core --> T[Twin: propuestas y explicación]
 T --> Core
 Core --> W[Worker: revalidación y reconciliación]
 W --> A[Backends/aplicaciones autorizados]
 Core --> AV[Anam: presencia acotada]
```

## Fronteras de confianza

OperadorP, tenantsA/B, proyectos/expedientes/recursos y principales son niveles distintos. Un registro de persona/cliente/alumno no es User ni membership. Compartir organización/marca/cohorte/nombre no comparte permiso. El operador y su agente actúan sobre targetTenant solo por delegación explícita; guardar Actor.tenantId de origen y scope de datos objetivo separados. No modificar Actor para simular pertenencia del cliente.

Cliente externo usa portal propio con idéntico Supabase/PEP y twin del padre. Puede contratar este servicio sin los otros ocho; módulos locales aprobados pueden cubrir funciones comunes. Un hermano ausente no justifica inventar saldo, revisión, dictamen, permiso profesional o dato. La duplicación funcional está permitida, con responsable único de efecto/campo por encargo.

## Dominio y autoridad

El contenido revisado y docente custodian enseñanza; LMS custodia matrículas/actividades por binding; evidencias/attempts son trazables; la competencia es inferencia calibrada, no un atributo clínico del alumno.

Objetos: `TrainingAgreement LearnerAuthority LearningObjective CompetencyMap ContentVersion Curriculum CourseVersion Cohort Enrollment AssessmentSpec QuestionRevision Attempt EvidenceRecord TutorSession MasteryObservation CompletionProposal CredentialProposal LRSStatement`. Estados propuestos de dominio: `needs_analysis, curriculum_draft, content_review, approved_course, enrolled, learning, practice, assessment_pending, evaluated_proposed, human_reviewed, completion_verified, withdrawn`. No son enums ya existentes en el padre. Mapear por EntityLink y registrar quién custodia original, proyección, revisión humana y prueba de resultado. Una conclusión aprobada puede volverse stale al cambiar fuente; conservar el snapshot aceptado y crear nueva revisión.

LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

## Módulos y datos

API/BFF con DTOs y scopes; servicios de negocio para fases9–32; repositorio tenant-scoped de objetos/versiones; policy/approval; adaptadores de datos; gateway de modelos; jobs/inbox/outbox/receipts; reports; presencia; SDK servidor. Tablas propuestas: agreements/work_orders, principals/bindings, domain_objects/revisions, source_documents/evidence_refs, external_links, provider_connections/capability_reports, proposals/approvals, intents/attempts/receipts, jobs/leases/cursors/conflicts, budgets/reservations, inbox/outbox/audit y snapshots. FKs/índices compuestos por tenant y recurso según cardinalidad. No API keys o JWT persistidos como datos de dominio.

Transacción local confirma estado/version/audit/idempotency/outbox; HTTP remoto no comparte esa transacción. Leases/fencing protegen coherencia local, no exactly-once remoto. Cursor avanza tras commit. Export/reindexación/restore conservan permisos, retención y estado sin reenviar efectos. Observabilidad no expone payloads de clientes.

## Modelo y revisión

El gateway solo permite modelos/configuraciones aprobados por tarea, idioma, región/retención y coste. El contexto mínimo se autoriza antes del retrieval y antes de responder. LLM no recibe credenciales, lista de tenants o tool genérica. Revisor LLM puede encontrar problemas; no puede certificar, atribuir condición profesional, ampliar presupuesto ni aprobar su propio efecto. La explicación cita hechos/fuentes y distingue inferencia.

Rota empresarial del padre; este repo expone trabajo/estado/eventos y timers técnicos pertinentes, sin segundo scheduler de empleados. Una tarea ofrecida necesita ACK real; un briefing informa acciones con evidencia, no simula actividad. Instalación/wiring en padre fuera de este encargo.
