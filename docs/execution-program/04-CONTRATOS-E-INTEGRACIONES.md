# Contratos y fronteras — Formación

Fuentes: `docs/contracts/01-contratos.md`, `docs/architecture/01-arquitectura.md`, `docs/architecture/02-identidad-twins.md`, `docs/architecture/03-compatibilidad-agente.md`, `docs/architecture/04-runtime.md`.

JWT+membresía+ACL alumno/curso/attempt, actor originTenant/targetTenant, twin bajo mandato. LearningObjective/AssessmentSpec versionados; PracticeAttempt distinto de GradedAttempt; no revelar respuestas ni hints de evaluación. MasteryObservation con evidencia/confianza/fecha y cobertura, no diagnóstico. Completion exige reglas y evidencia LMS/attempts, CredentialProposal no emite certificado por sí sola. LTI/OAuth/capabilities con permisos mínimos; xAPI receipts, dedupe e idempotencia. RLS/retención/PII educativa, revocación y derecho de contenido. No usar datos de alumno para perfilar salud ni filtrar entre tenants.
