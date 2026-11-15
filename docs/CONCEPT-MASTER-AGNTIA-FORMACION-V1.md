# CONCEPT MASTER — AGNTIA FORMACIÓN

**Versión:** 1.0 · **Fecha:** 2026-11-15 · **Serie:** 04/14 · **Estado:** arquitectura objetivo documental

> Fuente de dirección estratégica, subordinada a evidencia real de código y pruebas. DOCUMENTATION_ONLY: ninguna capacidad del catálogo es una afirmación de implementación.

## 01. Identidad, visión y resultado

Agntia Formación es una empresa especializada en diseñar, impartir, acompañar y evaluar aprendizaje profesional verificable. Opera como SaaS de especialidad para clientes externos y como middleware de AgntiaPro. No es un chatbot que genera diplomas: ofrece programas versionados, práctica real, evidencias de progreso, revisión docente y medición de transferencia. El alumno conserva agencia; los agentes no suplantan a docentes, acreditadores ni responsables laborales.

## 02. Estado real de partida

Baseline documental del 13-11-2026: DOCUMENTATION_ONLY. No hay aplicación, SDK, proveedores conectados ni tests de producto ejecutados. El repositorio declara 42 campañas NOT_STARTED, 294 tareas y 84 escenarios NOT_EXECUTED. Los documentos docs/01-producto.md, docs/architecture/*, docs/contracts/01-contratos.md y docs/campaigns/* constituyen el contrato de diseño existente. La validación de documentos no equivale a software verificado. No modificar el repositorio padre /agente sin autorización.

## 03. Producto y segmentos

Casos de uso: onboarding de empleados, capacitación comercial, actualización de procedimientos, formación de clientes, competencias digitales, formación técnica, capacitación en cumplimiento con supervisión y academia corporativa. Primer piloto restringido a adultos y datos sintéticos. Modelo de prestación: diagnóstico → objetivos medibles → itinerario → contenidos → matrícula sandbox → tutoría → práctica → evaluación → revisión humana → evidencia y reporte. La bonificación o acreditación oficial no está incluida por defecto.

## 04. Capacidades objetivo: 72

01 diagnóstico de necesidades; 02 intake de objetivos; 03 mapa de competencias; 04 análisis de brechas; 05 prerequisitos; 06 diseño instruccional; 07 currículo versionado; 08 cursos; 09 lecciones; 10 microlearning; 11 contenidos multiformato; 12 gestión de derechos; 13 revisión editorial; 14 bibliografía; 15 RAG educativo; 16 generación asistida de materiales; 17 traducción revisada; 18 accesibilidad; 19 contenidos interactivos; 20 H5P; 21 Adapt; 22 Moodle; 23 Open edX; 24 LTI; 25 xAPI; 26 LRS; 27 cohortes; 28 matrícula; 29 catálogo; 30 calendarios; 31 seguimiento de actividades; 32 tutor conversacional; 33 tutor avatar Anam; 34 tutor de voz; 35 memoria acotada por alumno; 36 pistas graduadas; 37 rutas adaptativas; 38 práctica guiada; 39 simulaciones; 40 ejercicios de aplicación; 41 feedback formativo; 42 banco de preguntas; 43 versionado de ítems; 44 rúbricas; 45 evaluación; 46 evaluación práctica; 47 integridad de intentos; 48 revisión docente; 49 apelaciones; 50 evaluación de transferencia; 51 mastery observada; 52 propuestas de completion; 53 credenciales propuestas; 54 verificación de evidencias; 55 analítica individual autorizada; 56 analítica agregada; 57 dashboards; 58 reportes; 59 exportación; 60 privacidad; 61 retención; 62 auditoría; 63 multiidioma; 64 identidad multitenant; 65 ACL de recurso; 66 contratos de servicio; 67 integración con agentes; 68 workflows SOP; 69 notificaciones; 70 presupuestos de modelos; 71 observabilidad; 72 operación y recuperación. Todas son capacidades OBJETIVO, no features disponibles.

## 05. Arquitectura propuesta

Portal/AgntiaPro → Supabase JWT verificado + membership + ACL → API TypeScript/Hono → core determinista (policy, estados, evaluaciones, evidencias, approvals) → Postgres/Supabase RLS, outbox, jobs y audit → adaptadores LMS/LRS/contenidos → SDK servidor. El modelo propone tutoría y material; el core verifica permisos, versiones, rúbricas y resultados. El avatar Anam es interfaz, nunca autoridad. La integración con el padre usa contrato privado, delegación verificable y ACK; no importa todo el runtime del padre como librería.

## 06. Autoridad, tenants y delegación

Distinguir operador, tenant cliente, cohortes, cursos, alumnos, recursos y campos. Una persona importada del LMS no se convierte en principal autorizado. El agente canónico reside en AgntiaPro; un twin local mantiene su identidad vinculada y capacidades limitadas. DelegationMandate define actor original, tenant origen, tenant objetivo, WorkOrder, recursos, propósito, derechos, presupuesto, expiración y revocación. AuthorityMap por efecto/campo evita dobles escrituras entre hermanos y padre. Sin mandato: DENY.

## 07. Entidades y contratos

TrainingAgreement, WorkOrder, LearnerAuthority, LearningObjective, CompetencyMap, ContentVersion, Curriculum, CourseVersion, Cohort, Enrollment, AssessmentSpec, QuestionRevision, Attempt, EvidenceRecord, TutorSession, MasteryObservation, CompletionProposal, CredentialProposal, LRSStatement, ProviderConnection, CapabilityReport, ApprovalBinding, OperationIntent, Receipt y AuditEvent. Envelope con schemaVersion, operationId, actor verificado, tenant resuelto por servidor, capability nominada, correlationId, idempotencyKey, expectedVersion, dryRun y payload validado. Los DTOs nunca aceptan tenant/role del prompt como autoridad.

## 08. SOPs pedagógicos

SOP-A intake y diagnóstico; SOP-B objetivos y competencias; SOP-C currículo y prerequisitos; SOP-D contenidos y licencia; SOP-E revisión editorial; SOP-F publicación LMS tras autorización; SOP-G matrícula sandbox; SOP-H sesión tutor; SOP-I práctica con pistas; SOP-J evaluación con rúbrica congelada; SOP-K revisión docente y apelación; SOP-L completion propuesta con evidencia; SOP-M reporte; SOP-N mejora curricular basada en resultados agregados. Cada SOP define precondiciones, inputs, permisos, estados, idempotencia, revisión, artefactos, eventos, fallos y compensación/reconciliación.

## 09. Tutoría y memoria

El tutor favorece comprensión y autonomía: pregunta, orienta, da pistas graduadas y verifica comprensión sin entregar respuestas protegidas durante evaluación. Mantener separación estricta práctica/examen, rúbrica y answer keys. Memoria de sesión por finalidad, curso, alumno y consentimiento/base adecuada; no inferir diagnósticos, rasgos sensibles ni aptitud laboral de métricas de engagement. RAG autoriza documentos antes de recuperar y antes de responder. Fuentes y versiones visibles.

## 10. Evaluación y certificación

Competencia = inferencia calibrada con cobertura, fecha, rúbrica, evidencia y confianza; no atributo absoluto. Completion requiere criterios versionados, intentos íntegros, evidencia LMS y revisión cuando proceda. CredentialProposal no emite certificado oficial. Un cambio en ítem, rúbrica, curso, fuente o permisos invalida propuestas dependientes; conservar el snapshot histórico sin sobrescribirlo. Apelaciones humanas y trazabilidad de decisiones.

## 11. Seguridad, privacidad y ética

Deny-by-default; RLS y ACL por recurso, Storage, Realtime, búsqueda vectorial, exportaciones y backups. Prevención de BOLA/IDOR, prompt injection, SSRF, filtración de respuestas, replay y suplantación de docentes. Sanitizar HTML/SVG/CSV y archivos, antivirus/cuarentena, secretos solo servidor, egress allowlist, audit append-only, backups cifrados y restauración que reaplique revocaciones. No menores reales, reconocimiento emocional, biometría, proctoring invasivo, diagnóstico clínico ni decisiones laborales/admisión automatizadas en piloto.

## 12. UX y presencia de agentes

Portal responsive con vista alumno, tutor, docente/revisor, responsable de formación y operador. Chat y Anam opcionales, accesibles y sustituibles por texto. Estados reales: pendiente, propuesta, revisión, bloqueado, ejecutando, verificado. Laia supervisa la experiencia en AgntiaPro; el especialista local realiza tutoría con permisos delegados. No mostrar actividad ficticia, no inventar duraciones ni presentar el avatar como prueba de acreditación.

## 13. Integraciones y límites

Priorizar un solo LMS para el vertical inicial (selección por licencia, despliegue, API, ACL y coste medidos); Moodle/Open edX como adaptadores alternativos, no ambos obligatorios. H5P/Adapt para contenidos, LTI para launches autorizados, xAPI/LRS para evidencia de actividad. Discovery de versiones/ediciones/permisos y CapabilityReport por instalación. Sin conector probado: UNSUPPORTED/NOT_VERIFIED, nunca simulación etiquetada como integración real.

## 14. Roadmap vigente y gates

Conservar exactamente C01–C42 de docs/campaigns/README.md y su manifest: C01–C08 fundaciones; C09–C32 dominio; C33–C42 portal, SDK, puente, seguridad, observabilidad, operación y aceptación. Gates por campaña y checkpoints cada cinco. Primer vertical E2E: necesidad sintética→objetivos→curso versionado→matrícula sandbox→tutor con pistas→práctica→evaluación con rúbrica→revisión humana→completion propuesta→reporte. No habilitar todos los backends para aparentar cobertura.

## 15. Pruebas y aceptación

Fixtures de operadorP, tenantA/B, alumnos con nombres similares, roles distintos y permisos revocados. Tests de ACL cruzada, RLS, documentos, retrieval, replay xAPI, idempotencia de matrículas, examen sin answer leak, stale approval, crash tras commit remoto, backup/restore, privacidad, accesibilidad e idiomas. Criterios críticos: cero fugas entre tenants, cero secretos, cero aprobaciones inventadas, cero duplicados por replay y cero efectos sensibles fuera de mandato. Mocks no acreditan integración. Registrar PASS/FAIL/BLOCKED/NOT_VERIFIED y skipped.

## 16. Operación y observabilidad

Event bus con eventos versionados y correlación; jobs/outbox/inbox, retries acotados, DLQ, leases y fencing; revalidación de permiso antes de ejecutar. Métricas: objetivos cubiertos, progresión basada en evidencias, tasa de revisión, resultados de evaluación, transferencia medida, costes por alumno/curso, latencia tutor, fallos por proveedor, cobertura accesible, incidentes de privacidad y recuperación. No equiparar tiempo en pantalla con aprendizaje.

## 17. Relación con la estrategia AgntiaPro

Servicio vendible como especialidad autónoma o integrado en la compilación de una empresa cliente. Los agentes son interfaz; el trabajo se expresa en SOPs deterministas, permisos, evidencias y resultados. Formación puede enseñar el uso de AgntiaPro, procedimientos de empresa y competencias operativas; no presupone que cualquier cliente tenga acceso a todos los repos hermanos. El contrato define el responsable único de cada efecto.

## 18. Decisiones pendientes y evolución

Seleccionar LMS inicial por prueba comparativa; definir modelo de precios de la especialidad sin alterar tarifas generales de AgntiaPro; revisar base jurídica de datos de empleados y derechos de contenidos; determinar requisitos concretos de acreditación/bonificación solo al ampliar ámbito; fijar SLO y presupuesto tras medición. Versiones futuras del Concept Master se alimentarán de reports de las 42 campañas, pruebas y cambios regulatorios. No fusionar, desplegar ni modificar padre sin aprobación.

## Referencias canónicas existentes

- README.md y docs/README.md
- docs/01-producto.md
- docs/architecture/01-arquitectura.md
- docs/architecture/02-identidad-twins.md
- docs/architecture/03-compatibilidad-agente.md
- docs/architecture/04-runtime.md
- docs/contracts/01-contratos.md
- docs/05-seguridad-privacidad.md
- docs/09-evaluacion.md
- docs/campaigns/README.md y docs/campaigns/campaign.json
- docs/release/PILOT-ACCEPTANCE.md

## Control de cambios

V1.0: Concept Master con 72 capacidades objetivo, 19 secciones, integración del roadmap vigente de 42 campañas, contratos, seguridad y criterios de aceptación. No se ha ejecutado el producto ni modificado /agente.
