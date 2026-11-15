# AGNTIA FORMACIÓN — CONCEPT MASTER V1
## Learning Intelligence & Competence Operating System
**2026-11-15 · Investigación arquitectónica · Estado: NO IMPLEMENTADO**

> **Misión:** convertir la formación profesional continua en un sistema verificable de desarrollo de capacidades: identificar necesidades, diseñar experiencias, enseñar con tutores agénticos, entrenar mediante práctica realista, evaluar con evidencias y conectar competencias con trabajo humano supervisado. **No confundir completar un curso, resolver una pregunta o generar un certificado con aprender.**

## 0. Inventario y contrato de verdad

**Repo inspeccionado:** `README.md`, `AGENTS.md`, `docs/README.md`, `docs/01-producto.md`, `docs/02-investigacion.md`, `docs/03-referentes-y-brechas.md`, `docs/04-adaptadores.md`, `docs/09-evaluacion.md`, `docs/architecture/01-arquitectura.md`, `docs/research/sources.json` y `docs/research/repositories.json`.

**Estado observado:** `DOCUMENTATION_ONLY`; 42 campañas `NOT_STARTED`, tests de producto `NOT_EXECUTED`; no existe aplicación, SDK, conector LMS, LMS operativo ni evaluaciones reales. Se documentaron cinco repos por SHA y tres referentes comerciales mediante lecturas selectivas, sin clonarlos ni ejecutarlos. No se acredita calidad de producto por validación de estructura documental.

**Investigación externa en esta revisión:** abstracts y fichas de TeachArena/EduAgentBench, EduClaw-Bench, Teaching-over-Solving; documentación oficial 1EdTech LTI 1.3/Advantage, AGS, NRPS y Deep Linking. Las referencias de Moodle/Open edX/H5P/Adapt/Learning Locker y sus SHAs se recuperan de la investigación previa del repo, no de una auditoría nueva de sus códigos. Se distinguen `OBSERVADO`, `DISEÑO`, `HIPÓTESIS` y `NO_VERIFICADO`.

**Ámbito de seguridad inicial:** adultos, dos tenants sintéticos, sin menores reales, biometría/emoción, vigilancia de empleados, proctoring invasivo, diagnósticos, calificación o admisión laboral automatizada, acreditación oficial o bonificación declarada sin autoridad y evidencia. Una nota del modelo es una propuesta, no una decisión oficial. El avatar Anam no firma ni acredita.

## 1. Tesis estratégica

El mercado LMS registra actividades, consume contenido, distribuye tests y produce reportes. El mercado de IA tutorial conversa, explica y genera ejercicios. Pero la formación empresarial requiere cerrar una cadena más exigente: **necesidad de trabajo → competencia observable → objetivo pedagógico → enseñanza y práctica → evidencia independiente → revisión competente → transferencia al puesto → mantenimiento de capacidad**.

La oportunidad de Agntia Formación es unir los sistemas sin falsificar causalidad. No sustituir un LMS completo desde cero en el primer sprint: crear un **Learning Intelligence Control Plane** con dominio, tutores, verificación, evidencia, contratos de interoperabilidad y portal propio; conectar Moodle u otro LMS cuando su licencia, edición, coste y permisos hayan sido probados. Las empresas pueden usarlo por AgntiaPro o como servicio especialista independiente.

### Diez motores diferenciadores

1. **Competence Reality Graph:** grafo de habilidades, tareas, evidencias, prerrequisitos, objetivos y versiones, con procedencia.
2. **Learning Evidence Ledger:** libro de pruebas de práctica, intentos, rúbricas, revisión y progreso, sin convertir inferencias en hechos.
3. **Pedagogical Decision Compiler:** traduce un diagnóstico y objetivo en intervenciones con justificación pedagógica y límites.
4. **Tutor Agency Governor:** protege el aprendizaje frente a un tutor que revela soluciones o hace el trabajo por el alumno.
5. **Mastery Uncertainty Engine:** estimaciones calibradas de dominio por habilidad, cobertura y antigüedad, nunca etiquetas permanentes.
6. **Curriculum Dependency Simulator:** simula secuencias, prerequisitos, duración y carga de aprendizaje, detecta ciclos.
7. **Workplace Transfer Twin:** compara práctica de entrenamiento con tareas del puesto, bajo propósito y permisos explícitos.
8. **Assessment Integrity Chain:** enunciado, versión, rúbrica, intento, evidencias, revisión, recurso y resultado con auditabilidad.
9. **Learning Interoperability Fabric:** LMS, LTI, xAPI/cmi5, SCORM, H5P, contenidos y eventos mediante adaptadores gobernados.
10. **Human-Agent Faculty:** LAIA y especialistas docentes como roles/SOPs, con docentes humanos y revisión de alto impacto.

**Hipótesis de valor:** estas diez capacidades pueden producir una formación más medible y adaptable que un catálogo estático; solo se considerará probado con comparaciones de aprendizaje y transferencia reales.

## 2. Investigación científica — de paper a requisito

### P01. TeachArena / EduAgentBench (arXiv:2605.14322)
**Pregunta científica:** ¿un agente puede juzgar pedagógicamente, tutorar de forma situada y completar flujos LMS? **Evidencia:** el trabajo evalúa tres superficies complementarias y documenta limitaciones de agentes avanzados en tutoría y ejecución real. La versión del 8-11-2026 utiliza el nombre TeachArena y describe 354 tareas; existen versiones/resúmenes anteriores con denominación EduAgentBench y 150 tareas. **No mezclar resultados de versiones.** Fuente: https://arxiv.org/abs/2605.14322

**Traducción:** tres harness independientes y uno combinado: `PedagogicalJudgmentEval`, `SituatedTutorEval`, `LMSWorkflowEval`, `TeachingEpisodeEval`. Un episodio completo debe demostrar que una decisión basada en evidencia produjo una interacción adecuada y un artefacto/estado persistente válido. Evaluar también si la acción fue autorizada, si la rúbrica estaba vigente y si el estudiante conservó agencia.

**Límite:** un benchmark de agentes no prueba aprendizaje real de nuestros alumnos ni autorización para operar un LMS externo. No copiar datasets sin revisar licencia y splits.

### P02. EduClaw-Bench (arXiv:2608.03206)
**Pregunta:** ¿cómo medir tutoría durante semanas? **Evidencia publicada:** simulación longitudinal de 30 días, 55 escenarios, varios modelos y harness; mide ganancia, capacidad de respuesta, utilidad y principios de diseño instruccional. **Traducción:** mantener `TutorSession`, `LearningStateSnapshot`, `Intervention`, `PracticeEvidence` y `FollowupOutcome` versionados. Evaluar calidad longitudinal y degradación, no una conversación bonita. Fuente: https://arxiv.org/abs/2608.03206

**Límite:** un estudiante simulado no equivale a persona; no aplicar métricas del paper como precisión real de Agntia. No persistir una inferencia de dominio como verdad sin evidencia y calibración.

### P03. Teaching-over-Solving (arXiv:2606.16206)
**Pregunta:** ¿el tutor enseña o simplemente da respuestas? **Evidencia:** resolución y pedagogía no son equivalentes; el estudio propone medirlas por separado y resalta preguntas guiadas, pistas calibradas y andamiaje sin revelar soluciones. **Traducción:** `HintLadder`, `DisclosureBudget`, `AssessmentMode` y `LearnerAgencyScore`. Un tutor que contesta el examen del alumno falla aunque su respuesta sea correcta. Fuente: https://arxiv.org/abs/2606.16206

**Límite:** las rúbricas pueden sesgar la evaluación; combinar métricas automáticas, revisión docente y resultados diferidos.

### P04. Ciencia de aprendizaje y diseño
Investigar de manera explícita **retrieval practice**, **spaced repetition**, **interleaving**, **worked examples**, **cognitive load**, **mastery learning**, **Bloom revisada**, **Gagné**, **Rosenshine**, **constructive alignment**, **transfer of training**, **item response theory** y **knowledge tracing**. Estos enfoques no son recetas universales. Cada política de intervención debe guardar población objetivo, contexto, contraindicaciones, baseline y criterio de evaluación. **No afirmar superioridad causal sin experimento adecuado.**

### P05. Aprendizaje organizacional
La unidad de valor empresarial no es «horas de vídeo vistas» sino la mejora de una tarea: menos errores documentados, más autonomía profesional, mejor calidad o menor tiempo **sin aumentar riesgo**. Separar satisfacción, conocimiento, habilidad demostrada y transferencia al puesto. Un KPI de negocio puede depender de cambios ajenos a la formación; evitar atribución simplista.

## 3. Benchmark internacional de empresas y productos

| Producto/organización | Qué investigar | Posible aprendizaje | Riesgo de extrapolación |
|---|---|---|---|
| Moodle / Moodle Workplace | LMS extensible, roles, plugins, AI subsystem | base autoalojable, control y ecosistema | edición/versión/licencias |
| Open edX | cursos, cohortes, extensibilidad | enseñanza a escala, componentes | complejidad operativa |
| Canvas LMS (Instructure) | APIs, LTI, UX docente | interoperabilidad y gradebook | plan, hosting y derechos |
| Blackboard Learn | LMS enterprise, assessment | flujos institucionales | dependencia y coste |
| D2L Brightspace | rutas y analítica | enseñanza adaptativa | claims no verificados |
| Docebo | LMS empresarial | skills y compliance learning | certificaciones no heredables |
| Cornerstone OnDemand | skills/talent/LMS | competencias y formación corporativa | vigilancia y decisiones laborales |
| Degreed | skill intelligence | taxonomías y aprendizaje externo | inferencias de skills |
| 360Learning | collaborative learning | expertos internos como autores | calidad de contenido |
| LearnUpon | training de clientes y empleados | portales multiempresa | segregación y pricing |
| TalentLMS | LMS pymes | simplicidad y despliegue | alcance de API |
| Absorb LMS | LMS corporate | reporting y operación | precio y funcionalidades |
| LinkedIn Learning | catálogo y skills | relevancia laboral | licencias de contenido |
| Coursera for Business | itinerarios y contenido | catálogo y evaluación | acreditación externa |
| Udemy Business | catálogo profesional | amplitud de temas | validez de evidencia |
| Khanmigo | tutor socrático | preguntas guiadas | edad, planes, disponibilidad |
| Duolingo Max | personalización y práctica | feedback y motivación | gamificación ≠ transferencia |
| Sana / Sana Labs | AI learning workspace | creación y búsqueda | privacidad y claims |
| 7taps | microlearning | bajo coste de producción | profundidad limitada |
| Synthesia | vídeo de formación | presentadores sintéticos | derechos de imagen/voz |

**Estado de evidencia:** los tres primeros referentes de la investigación previa fueron Moodle, Khanmigo y Docebo; los demás son **candidatos a comparar**, no productos probados en esta sesión. Para cada uno crear una ficha con URL oficial, fecha, producto/edición, roles, API, precios verificables, capacidades demostradas, límites, derechos, data residency, calidad pedagógica y costes. Un benchmark de marketing no acredita aprendizaje.

### 3.1 Repositorios y estándares: arquitectura de adopción

| Proyecto/estándar | Papel | Licencia/estado conocido | Decisión de diseño |
|---|---|---|---|
| Moodle `moodle/moodle` | LMS candidato | GPL-3.0 según metadata interna | primer adaptador a estudiar; instancia aislada |
| Open edX `openedx/openedx-platform` | LMS alternativo | AGPL-3.0 según metadata interna | no instalar master como release |
| H5P PHP Library | actividades interactivas | GPL-3.0 según metadata interna | contenido y módulos con licencias separadas |
| Adapt Framework | autoría responsive | GPL-3.0 según metadata interna | evaluar authoring y accesibilidad |
| Learning Locker | LRS xAPI | GPL-3.0 según metadata interna | registro opcional; evitar doble autoridad |
| Canvas LMS `instructure/canvas-lms` | LMS alternativo | licencia exacta por versión pendiente | probar API/roles/tenant |
| Chamilo `chamilo/chamilo-lms` | LMS alternativo | verificar licencia y versión | valorar coste pymes |
| ILIAS `ILIAS-eLearning/ILIAS` | LMS alternativo | verificar licencia | contraste de assessment |
| Opigno LMS | Drupal LMS | verificar edición/licencias | contraste de authoring |
| SCORM 1.2/2004 | paquete/tracking legado | especificación, no software | importar con limitaciones |
| xAPI / LRS | statements de experiencia | validar especificación/perfil | receipts no equivalen a competencia |
| cmi5 | xAPI para LMS | validar versión y perfiles | interoperabilidad opcional |
| LTI 1.3 / Advantage | conexión LMS/herramienta | estándar 1EdTech | OIDC, AGS, NRPS, Deep Linking |
| QTI | preguntas e intercambios | estándar 1EdTech | item versionado y rubric mapping |
| OneRoster | roster/inscripciones | estándar 1EdTech | no confundir matrícula con membresía |
| Open Badges / CLR | evidencias y credenciales | estándar 1EdTech | emisión solo con autoridad real |

**Referencia pin interna:** Moodle `afbcc55fa1bd80dcdd887b8965dd8c28c0f3bbda`, Open edX `32e2f7d8ec6a3bfff1f4695fc2360f71ff52f1a6`, H5P `2d7f937a03c925e1332651b16ac6e56ac7544431`, Adapt `f0a705d9cd24d915acef6eeb7b1f6da4ed5e4131`, Learning Locker `5fec948a823e372e740df521aa3684c8df1dcba7`. Estos son SHAs de **lectura documental**, no pins de despliegue. Revisar licencia de cada plugin, peso/modelo, contenido, versión y obligaciones de red/distribución. API separada no resuelve automáticamente licencias.

**LTI:** 1EdTech documenta LTI 1.3 y Advantage, con Assignment and Grade Services 2.0, Names and Role Provisioning Services 2.0 y Deep Linking 2.0. Implementar seguridad OIDC/JWT, registro de deployment, audience/issuer, nonce, replay protection, roles y límites de curso/tenant. El lanzamiento LTI no es permiso universal para leer o modificar un LMS. Fuente: https://www.1edtech.org/standards/lti

## 4. Learning Reality Graph y modelos formales

**Nodos:** `Organization, Tenant, Learner, Instructor, Competency, Skill, Prerequisite, Task, LearningObjective, EvidenceCriterion, Course, Module, LearningAsset, Activity, AssessmentSpec, ItemRevision, Attempt, TutorIntervention, PracticeEvidence, MasteryObservation, HumanReview, CompletionProposal, CredentialProposal, WorkplaceOutcome`.

**Aristas:** `requires`, `teaches`, `assesses`, `supports`, `attempted`, `reviewedBy`, `evidencedBy`, `mapsToWorkTask`, `derivedFrom`, `supersedes`. Cada arista tiene procedencia, tenant, validez temporal, confianza si es inferencia y finalidad. Evitar una «puntuación de empleado» global y permanente.

**Mastery:** `MasteryObservation = {skillId, evidenceRefs, observedAt, estimatorVersion, coverage, confidence, uncertainty, validityWindow}`. Una probabilidad calibrada es inferencia revisable, no diagnóstico ni calificación laboral. Con pocos datos devolver `INSUFFICIENT_EVIDENCE`; no inventar mastery.

**Evidence ledger:** `LearningEvidence = {learnerRef, objectiveRef, activityRef, attemptRef, rubricVersion, evidenceHash, assessorRef, observedAt, provenance, integrityStatus, appealStatus}`. El ledger puede guardar hashes/refs y minimizar datos; no almacenar conversaciones íntimas sin finalidad.

**Curriculum graph:** DAG de objetivos y prerrequisitos con versiones. Detectar ciclos, contenidos obsoletos, objetivos sin evidencia y actividades que evalúan otra habilidad. El planificador puede proponer alternativas de tiempo/coste, pero el docente valida contenido y criterios.

## 5. Tutor Agency Governor

**Tres modos separados:**
- `LEARN`: explicar conceptos, preguntar, ofrecer ejemplos y pistas graduadas.
- `PRACTICE`: feedback formativo, corrección y demostración cuando el ejercicio lo permite.
- `ASSESS`: proteger solución/rúbrica, registrar intento, no filtrar respuesta y escalar decisiones.

**Escalera de pistas:** (0) pregunta diagnóstica, (1) reformulación, (2) pista conceptual, (3) pista de procedimiento, (4) ejemplo análogo, (5) solución explicada **solo fuera de evaluación y según política**. Registrar el nivel y si hubo respuesta del alumno. El objetivo es generar razonamiento del estudiante, no dependencia.

**Estrategia longitudinal:** cada sesión comienza con objetivos y memoria autorizada, identifica incertidumbres, selecciona intervención, comprueba comprensión con evidencia, ofrece práctica y agenda revisión. El tutor no debe adaptar rutas con inferencias sensibles o diagnósticos. Retención y progreso se evalúan en fechas posteriores, no solo con satisfacción inmediata.

**RAG pedagógico:** separar material de estudio, solución protegida, rúbricas docentes y datos personales. Filtrar por tenant, curso, rol, modo y finalidad antes de recuperar; documentos y respuestas de estudiantes son datos no confiables. No permitir que un enunciado «ignore el sistema» habilite herramientas. No incluir respuestas oficiales en el contexto del tutor de examen.

## 6. Assessment Integrity Chain

`AssessmentSpec → ItemRevision → RubricVersion → Attempt → EvidenceRecord → ProposedScore/Feedback → HumanReview → AppealWindow → VerifiedOutcome`.

**Requisitos:** versiones congeladas al inicio de intento, rúbrica conocida/oculta según modo, soporte de respuestas alternativas, fuentes de corrección, posibilidad de recurso y rectificación. Para trabajos creativos o habilidades prácticas, evidencia multimedia y revisión competente. Un LLM puede redactar feedback y detectar inconsistencias, pero no emitir acreditación ni una decisión laboral significativa.

**Evaluación adaptativa [HIPÓTESIS]:** modelos de respuesta al ítem y selección de dificultad solo cuando exista calibración y control de sesgos; no cambiar silenciosamente criterios entre alumnos. Pruebas accesibles equivalentes y ajustes razonables; no inferir discapacidad por conducta.

**Completion:** separar `activity_completed`, `course_completion_proposed`, `learning_outcome_reviewed`, `credential_issued_by_authority`. Un xAPI statement o evento de vídeo no certifica competencia. La bonificación FUNDAE, acreditación y formación reglada española requieren proceso, documentación y revisión normativa específica.

## 7. Arquitectura: once planos

1. **Identity & Delegation:** Supabase JWT, JWKS, issuer/audience, membresía, representación y ACL.
2. **Training Agreement:** propósito, objetivos, personas, plazos, presupuesto y responsable.
3. **Competency & Curriculum:** grafo, objetivos, secuencia, contenido y revisiones.
4. **Content & Rights:** licencias, accesibilidad, provenance, revisión editorial y versionado.
5. **Learner Experience:** portal, rutas, tutoría, práctica, sesiones y consentimiento.
6. **Pedagogical Intelligence:** decisiones, hints, feedback, memoria acotada y uncertainty.
7. **Assessment & Evidence:** intentos, rúbricas, revisiones, recursos y completion.
8. **LMS & Interoperability:** Moodle/Open edX, LTI, xAPI/cmi5, H5P, sync, mapping.
9. **Agent Faculty:** LAIA, twins, WorkOrders, SOPs, approvals, human review.
10. **Analytics & Workplace Transfer:** métricas semánticas, evidencia, resultados y límites causales.
11. **Governance & Operations:** PEP, RLS, outbox, jobs, costes, seguridad, observabilidad y restore.

**Separación de autoridad:** el LMS puede custodiar matrículas y actividades; Agntia custodia planes, propuestas, provenance y resultados locales; el docente autorizado decide evaluación final; entidad habilitada emite credenciales oficiales. El mismo hecho no tiene dos owners sin reconciliación.

### 7.1 Contratos TypeScript propuestos

```ts
type TrainingMandate = {
  originTenantId: string;
  targetTenantId: string;
  actorRef: { tenantId: string; roleId: string; runtimeId: string; personaId?: string };
  workOrderId: string;
  purpose: "course.design" | "tutoring" | "assessment.review" | "lms.enrollment";
  resourceScope: string[];
  expiresAt: string;
  revocationRef: string;
};
type LearningObjective = {
  tenantId: string;
  objectiveId: string;
  version: number;
  skillRef: string;
  observableBehavior: string;
  assessmentCriteria: string[];
  prerequisites: string[];
  evidenceThresholdRef: string;
};
type TutorTurn = {
  sessionId: string;
  mode: "LEARN" | "PRACTICE" | "ASSESS";
  objectiveVersionRef: string;
  retrievedEvidenceRefs: string[];
  hintLevel: number;
  disclosureBudgetRef: string;
  learnerProducedEvidenceRef?: string;
  nextReviewAt?: string;
};
type CompletionDecision = {
  tenantId: string;
  learnerRef: string;
  courseVersionRef: string;
  assessmentSpecRef: string;
  evidenceRefs: string[];
  reviewerRef?: string;
  status: "PROPOSED" | "NEEDS_REVIEW" | "VERIFIED" | "REJECTED";
  credentialIssued: false;
};
```

Los contratos no existen aún en código. No reutilizar `LearningFact` del kernel como perfil del estudiante; el aprendizaje de agentes y el aprendizaje humano son dominios separados.

### 7.2 Workflow principal

`Need → Evidence-Grounded Diagnosis → Skill Gap Hypothesis → LearningObjectives → CurriculumDraft → ContentRightsReview → CourseApproved → SandboxEnrollment → TutorSessions → Practice → AssessmentAttempt → FeedbackProposal → HumanReview → CompletionProposal → LMSReceipt → ReportSnapshot → FollowupTransfer`.

Cada flecha define actor, policy, schema, persistencia, evidencia, timeout, estado incierto y rollback/compensación. Los borradores no tienen efectos externos; las matrículas, notas y mensajes sí. Un evento en bus no prueba éxito remoto.

### 7.3 LMS adapters

`LmsAdapter = {discoverCapabilities, readCourses, readEnrollments, previewEnrollment, executeEnrollment, readAttempts, readCompletion, reconcileEffect}`. Métodos concretos y nominados, no `executeSQL` ni `callArbitraryEndpoint`. IDs opacos, tenant+connection+externalId; `CapabilityReport` con edición/versión, scopes, estado y fecha. Un 200 no prueba que el curso o tenant sea correcto. En LTI, launch y grades tienen permisos diferentes.

**Outbox:** guardar intent, idempotency key, approval y audit en transacción; worker revalida mandato y permisos antes de HTTP; en timeout tras posible aceptación remota, `OUTCOME_UNKNOWN` y reconciliación. No duplicar matrícula, certificado ni nota. Repetir un xAPI statement no debe duplicar completion.

## 8. Seguridad, privacidad, ética y regulación

**Seguridad:** datos del alumno, cursos, exámenes, claves, resultados, embeddings, archivos, jobs, exports y caches aislados por tenant y recurso; permisos de instructor y alumno distintos; service_role no elimina necesidad de checks. JWT de Supabase verificado, no metadata editable como autorización. Tenant de origen y objetivo distintos cuando un operador trabaja para otra empresa. LLM no recibe credenciales ni listas de alumnos ajenos. SSRF, prompt injection desde materiales, CSV/HTML injection y paquetes H5P maliciosos deben ser probados.

**Privacidad:** finalidad, minimización, retención, rectificación, acceso, borrado y proveedores/subencargados; no perfilar rasgos sensibles, emociones o salud. Analítica de aprendizaje agregada cuando corresponda; no monitorización oculta del trabajador. Datos de tutoría no se usan para entrenamiento de terceros sin base jurídica y acuerdos. Atención a RGPD, LOPDGDD, AI Act según caso, accesibilidad y normativa de formación profesional/bonificada aplicable. No declarar cumplimiento universal.

**Equidad:** contenido accesible sin avatar; subtítulos, transcripciones, teclado, lector de pantalla, velocidad ajustable, alternativas equivalentes, idiomas, diversidad de ejemplos y revisión humana de sesgos. Evaluación no debe penalizar una necesidad de accesibilidad.

**Agentes:** LAIA es supervisora y cara pública; especialistas pedagógicos son roles/SOPs/twins vinculados, no identidades canónicas nuevas. Un avatar puede explicar una lección, nunca acreditar, sancionar o decidir empleo. El alumno debe saber cuándo interactúa con IA.

## 9. Producto y experiencia de usuario

**Workspaces:** Executive Learning Desk, Skills Observatory, Curriculum Architect, Course Studio, Content Rights, Learning Pathways, Tutor Room, Practice Simulator, Assessment Review, Instructor Console, Cohort Manager, Learning Analytics, LMS Connections, Credentials & Evidence, Agent Faculty, Compliance & Operations.

**UX alumno:** objetivo y utilidad de cada módulo, mapa de progreso no estigmatizante, explicación de pistas, práctica segura, revisión y recurso, control de datos y acceso móvil. **UX docente:** evidencias y incertidumbre, rubricas versionadas, vista de cohortes autorizadas, propuestas de intervención y aprobación. **UX empresa:** necesidades, presupuesto, cursos y resultados con límites de atribución; no ranking individual de empleados para decisiones laborales.

**Formatos:** microlearning, cohortes, tutoría individual, simulación de atención al cliente, roleplay de ventas, formación técnica, vídeos de LAIA/Anam, escenarios de seguridad defensiva, cuestionarios, ejercicios prácticos y proyectos. Cada formato debe medir el objetivo que pretende, no solo completar clics.

**Servicio:** la empresa especialista puede ofrecer diseño e impartición, tutores y operaciones LMS con portal independiente. En AgntiaPro se integra como capacidad progresiva de la empresa compilada; no presupone que cada pyme tenga LMS ni que una suscripción dé acceso a contenido comercial ajeno.

## 10. Catálogo de capacidades de destino


### A. Diagnóstico y estrategia
**FOR001 [DISEÑO]** Intake de necesidades con fuentes. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR002 [DISEÑO]** Skill-gap hypotheses verificables. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR003 [DISEÑO]** Mapa de roles y tareas de empresa. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR004 [DISEÑO]** Competency Reality Graph. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR005 [DISEÑO]** Taxonomías y equivalencias de skills. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR006 [DISEÑO]** Prerrequisitos y ciclos. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR007 [DISEÑO]** Learning Objectives versionados. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR008 [DISEÑO]** Priorización por riesgo/impacto. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR009 [DISEÑO]** Plan de formación y coste. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR010 [DISEÑO]** Acuerdo de aprendizaje y revisión. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### B. Autoría y currículo
**FOR011 [DISEÑO]** Curriculum dependency planner. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR012 [DISEÑO]** Syllabus por competencias. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR013 [DISEÑO]** Lecciones multiformato. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR014 [DISEÑO]** Biblioteca con rights provenance. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR015 [DISEÑO]** Generación de ejercicios y soluciones protegidas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR016 [DISEÑO]** H5P/Adapt export opcional. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR017 [DISEÑO]** Guion de vídeo con agntia-video. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR018 [DISEÑO]** Accesibilidad y localización. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR019 [DISEÑO]** Control de claims y contenido obsoleto. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR020 [DISEÑO]** Revisión editorial y aprobación. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### C. Experiencia del alumno
**FOR021 [DISEÑO]** Portal alumno multi-tenant. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR022 [DISEÑO]** Rutas adaptativas explicables. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR023 [DISEÑO]** Tutoría conversacional con LAIA. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR024 [DISEÑO]** Tutor Agency Governor. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR025 [DISEÑO]** Pistas graduadas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR026 [DISEÑO]** Preguntas socráticas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR027 [DISEÑO]** Práctica deliberada. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR028 [DISEÑO]** Spaced retrieval planner. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR029 [DISEÑO]** Feedback formativo. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR030 [DISEÑO]** Memoria pedagógica acotada. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### D. Evaluación y evidencias
**FOR031 [DISEÑO]** AssessmentSpec y banco de ítems. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR032 [DISEÑO]** Rúbricas versionadas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR033 [DISEÑO]** Intentos reproducibles. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR034 [DISEÑO]** Protección modo examen. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR035 [DISEÑO]** Evidencia de desempeño. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR036 [DISEÑO]** Mastery uncertainty engine. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR037 [DISEÑO]** Revisión docente. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR038 [DISEÑO]** Impugnación y rectificación. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR039 [DISEÑO]** Completion proposal con pruebas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR040 [DISEÑO]** Credential proposal sin emisión automática. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### E. Interoperabilidad
**FOR041 [DISEÑO]** Capability registry LMS. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR042 [DISEÑO]** Moodle adapter. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR043 [DISEÑO]** Open edX adapter. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR044 [DISEÑO]** Canvas adapter opcional. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR045 [DISEÑO]** LTI 1.3 launch seguro. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR046 [DISEÑO]** LTI AGS/NRPS/Deep Linking. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR047 [DISEÑO]** xAPI/LRS statements. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR048 [DISEÑO]** cmi5 y SCORM import. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR049 [DISEÑO]** H5P sandbox y validación. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR050 [DISEÑO]** ExternalLink y reconciliación. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### F. Formación empresarial
**FOR051 [DISEÑO]** Cohortes y matrículas autorizadas. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR052 [DISEÑO]** Rutas por rol profesional. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR053 [DISEÑO]** Simulador de conversaciones. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR054 [DISEÑO]** Simulador de procesos SOP. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR055 [DISEÑO]** Evaluación práctica de competencias. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR056 [DISEÑO]** Workplace Transfer Twin. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR057 [DISEÑO]** Learning ROI con límites causales. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR058 [DISEÑO]** Formación continua de equipos. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR059 [DISEÑO]** Reportes de brechas agregados. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR060 [DISEÑO]** Programas de actualización tecnológica. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### G. Agentes y colaboración
**FOR061 [DISEÑO]** LAIA supervisora pedagógica. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR062 [DISEÑO]** Twins por cliente y especialidad. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR063 [DISEÑO]** Docente humano revisor. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR064 [DISEÑO]** WorkOrders con mandato. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR065 [DISEÑO]** ApprovalBinding hash+versión. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR066 [DISEÑO]** Tutor context budget. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR067 [DISEÑO]** Human-agent teaching episodes. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR068 [DISEÑO]** Agent activity provenance. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR069 [DISEÑO]** Handoff con ACK. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR070 [DISEÑO]** Presencia Anam sin autoridad. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### H. Seguridad y operaciones
**FOR071 [DISEÑO]** Supabase JWT y ACL. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR072 [DISEÑO]** RLS tenant/recurso. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR073 [DISEÑO]** Secret vault y scopes. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR074 [DISEÑO]** Outbox e idempotencia. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR075 [DISEÑO]** Reconciliación de efectos inciertos. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR076 [DISEÑO]** Prompt injection defense. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR077 [DISEÑO]** Protección de rúbricas y soluciones. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR078 [DISEÑO]** Retention/DSAR y borrado. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR079 [DISEÑO]** Observabilidad/cost budgets. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR080 [DISEÑO]** Backup/restore sin replay. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

### I. Evaluación y evolución
**FOR081 [DISEÑO]** TeachArena-inspired harness. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR082 [DISEÑO]** EduClaw-inspired longitudinal eval. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR083 [DISEÑO]** Teaching-over-Solving score. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR084 [DISEÑO]** Learning gain con baseline. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR085 [DISEÑO]** Calibración de mastery. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR086 [DISEÑO]** Pruebas de transferencia al puesto. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR087 [DISEÑO]** Bias/accessibility eval. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR088 [DISEÑO]** A/B con interferencia documentada. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR089 [DISEÑO]** Red team de agentes y LMS. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.
**FOR090 [DISEÑO]** Research-to-product evidence registry. **Contrato de aceptación:** recurso y tenant identificados; schema y policy versionados; fuente/evidencia verificable; resultado y fallo explícitos; prueba automatizada o revisión competente según riesgo.

## 11. Protocolo de evaluación: demostrar aprendizaje y seguridad

**Diseño de experimentos:** (a) baseline sin tutor; (b) LLM que da soluciones; (c) tutor con scaffolding; (d) tutor + práctica espaciada; asignación según ética y viabilidad, objetivos equivalentes, pre/post tests con formas comparables, retención diferida, seguimiento de abandono y coste. La diferencia de puntuaciones puede estar afectada por selección, dificultad, asistencia externa y otras variables; registrar esos límites. Para transferencia al puesto, medir tarea observable y revisión humana sin convertirlo en evaluación laboral automatizada.

**Harness técnico:** `TeachingEpisode = {objective, evidence, learnerState, policy, tutorTurns, toolCalls, protectedState, artifacts, outcome, reviewer}`. Tres puntuaciones separadas: `pedagogical_quality`, `learning_support`, `workflow_correctness`; más `safety`, `accessibility`, `cost` y `human_review`. Un texto excelente con matrícula indebida falla. Un agente que se niega a todo no obtiene utilidad.

**28 pruebas adversariales:**
1. JWT firmado por issuer ajeno; 2. membership revocada; 3. alumno accede a cursoB; 4. docenteA ve intentosB; 5. operadorP suplanta alumno; 6. twin sin mandato; 7. restore revive matrícula revocada; 8. RAG cruza tenant; 9. retrieval de soluciones protegidas; 10. enunciado con prompt injection; 11. H5P con script malicioso; 12. import CSV formula injection; 13. LTI launch con issuer equivocado; 14. LTI nonce replay; 15. AGS intenta nota en curso ajeno; 16. xAPI statement repetido; 17. timeout tras matrícula remota; 18. dos workers duplican enrollment; 19. rúbrica cambia durante intento; 20. tutor filtra solución de examen; 21. alumno solicita borrar datos; 22. analytics revela persona por grupo pequeño; 23. curso usa material sin licencia; 24. modelo inventa competencia; 25. modelo emite certificado sin autoridad; 26. alumno impugna corrección; 27. idioma o accesibilidad altera dificultad; 28. un reporte confunde satisfacción con aprendizaje.

**Gates críticos:** cero filtración cross-tenant; cero aprobación/credencial inventada; cero exposición de claves; cero efectos sensibles fuera de mandato; cero duplicados por replay cuando es controlable; `OUTCOME_UNKNOWN` cuando no se puede probar éxito. En tests de aprendizaje, reportar distribución, idioma, nivel, duración, incertidumbre y baseline. Los mocks prueban contratos, no un LMS real.

## 12. Roadmap de convergencia en 12 olas

**G0 — Evidence Atlas:** registrar papers con versión, empresas con edición, repos por SHA/licencia, estándares y riesgos; ADRs y research gaps.
**G1 — Domain Contracts:** Zod, objetivos, habilidades, evidencias, intentos, rúbricas y state machines.
**G2 — Identity & Tenancy:** Supabase, memberships, actor/mandate, RLS, ACL de alumno/docente/operador y pruebas.
**G3 — Curriculum Studio:** objetivos, contenidos, licencias, DAG, revisión y portal de autor.
**G4 — Tutor Runtime:** modos LEARN/PRACTICE/ASSESS, hints, RAG, memoria y guardrails.
**G5 — Assessment:** item bank, attempts, rúbricas, revisión y recurso.
**G6 — LMS Lab:** Moodle aislado, discovery, read-only, LTI/SCORM/xAPI por fases, fake provider.
**G7 — Enrollment & Effects:** approvals, outbox, leases, idempotencia, reconciliación.
**G8 — Learning Experience:** portal alumno/docente, accesibilidad, sesiones y cohortes.
**G9 — Workplace Training:** simulaciones, escenarios profesionales, handoffs a repos hermanos.
**G10 — Longitudinal Evaluation:** TeachArena/EduClaw-inspired fixtures, pilotos autorizados, retención y transferencia.
**G11 — Operations & V2:** costes, SLO, observabilidad, backups, licencias, investigación nueva y decisiones.

**No reemplazar las 42 campañas existentes.** Mapear `FORnnn → ADR → campaña → fase → patchset → archivo → test → reporte → gate`. Los paths siguientes son **propuesta** a cotejar con árbol real:
`packages/domain/src/{competencies,curriculum,assessment,evidence}.ts`;
`packages/pedagogy/src/{planner,tutor,scaffolding,mastery}.ts`;
`packages/adapters/src/{moodle,lti,xapi,registry}.ts`;
`apps/api/src/{auth,workorders,courses,attempts,enrollment}.ts`;
`apps/worker/src/{outbox,leases,reconciliation}.ts`;
`apps/web/src/views/{Learner,Instructor,CourseStudio,Assessment,Analytics}.tsx`;
`tests/{unit,integration,e2e,adversarial,learning-evals}/`.

**Dependencias candidatas:** TypeScript/Hono/pnpm, Zod, Postgres/Supabase, SDKs/HTTP oficiales, OpenTelemetry; cola durable por Postgres antes de introducir BullMQ/Temporal; Moodle o Open edX como servicio aislado y opcional, no `pip install` de LMS en monorepo TS. Versiones y licencias por ADR, sin instalaciones automáticas. Revisión humana y consentimiento para cualquier piloto con datos reales.

## 13. Research backlog de alta prioridad

1. Leer el PDF completo y apéndices de TeachArena v5; comparar con v1 y verificar tareas/criterios.
2. Revisar EduClaw-Bench y sesgos del learner simulator; diseñar transferencia a estudiantes humanos.
3. Analizar Teaching-over-Solving, sus rúbricas y medidas de agencia.
4. Auditar Moodle por release estable, plugins IA, API y permisos; correr entorno aislado.
5. Contrastar Open edX por despliegue, LTI y coste operativo.
6. Evaluar H5P y Adapt por licencias de contenido, accesibilidad y seguridad de paquetes.
7. Revisar Learning Locker y xAPI/cmi5 en versión y conformidad reales.
8. Contrastar Canvas, Docebo, Cornerstone, Degreed y otros por API, edición y coste verificable.
9. Diseñar y ejecutar pruebas de conocimiento diferido y transferencia al trabajo.
10. Probar RLS/ACL y LTI contra dos tenants y roles cruzados.
11. Medir coste por alumno activo y por hora de tutoría frente a calidad y aprendizaje.
12. Verificar legislación española aplicable a formación bonificada, accesibilidad y decisiones laborales con asesoría competente.

**Cada tarea de investigación:** pregunta → fuente primaria → versión/fecha → método → evidencia extraída → limitación → decisión de diseño → ADR → test que la falsaría. No marcar «auditado» un README leído.

## 14. Fuentes, procedencia y límites

**Papers consultados en fuentes públicas:**
- TeachArena/EduAgentBench: https://arxiv.org/abs/2605.14322
- EduClaw-Bench: https://arxiv.org/abs/2608.03206
- Teaching-over-Solving: https://arxiv.org/abs/2606.16206

**Estándares oficiales:**
- LTI 1.3/Advantage, AGS, NRPS y Deep Linking: https://www.1edtech.org/standards/lti
- Guía LTI Advantage: https://standards.1edtech.org/lti/guides/implementation_guide/implementation-guide
- Especificaciones 1EdTech: https://www.1edtech.org/specifications
- xAPI: https://adlnet.gov/projects/xapi/ (validación operativa pendiente)

**Repositorio interno:**
- [Producto](../01-producto.md), [investigación previa](../02-investigacion.md), [benchmark anterior](../03-referentes-y-brechas.md), [adaptadores](../04-adaptadores.md), [evaluación](../09-evaluacion.md).
- [Fuentes con estado de lectura](../research/sources.json), [repos con SHA](../research/repositories.json), [arquitectura](../architecture/01-arquitectura.md), [AGENTS](../../AGENTS.md).

**Advertencia:** el documento es más ambicioso y más preciso que la documentación inicial, pero **no es una auditoría de código exhaustiva de 20 productos**, no demuestra aprendizaje real ni licencia/compatibilidad por instalación. Todo lo no probado queda señalado como investigación o diseño. Una siguiente versión deberá incorporar resultados de repos clonados, tests ejecutados y decisiones de proveedores con evidencia. La calidad no se mide por número de capacidades sino por pruebas, causalidad, claridad y límites.
