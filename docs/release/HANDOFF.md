# Handoff para la IA implementadora · agntia-formacion

2026-11-13. Encargo actual: **solo documentación**, no implementación. Trabajar en `uniscrolliabrain-cloud/agntia-formacion`. **No modificar `/agente` ni repos hermanos.** La carpeta local es `/workspace/agntia-formacion`; en otra máquina obtener checkout de GitHub. Las rutas de implementación de las campañas son propuestas, no archivos ya existentes.

## Intención y acuerdos

Diseñar e impartir formación con objetivos, contenidos, prácticas y evidencia de aprendizaje, integrando LMS y tutores IA sin confundir ayuda con acreditación o vigilancia del alumno. El servicio es una empresa SaaS especialista que puede servir a clientes externos o integrados, con humanos responsables y presencia por Anam. Se permiten funciones solapadas con padre/hermanos, con AuthorityMap por encargo y un ejecutor de cada efecto. El agente canónico vive en padre, twin aquí; no crear nuevo registro soberano de empleados. Todos los modos JWT Supabase, membership/ACL y scopes end-to-end. La UI externa no requiere UI AgntiaPro, pero mantiene vínculo del especialista al padre.

## Antes de codificar con autorización posterior

Leer README/producto/arquitectura/twins/contratos/seguridad/evaluación/fuentes/licencias. Congelar SHA propio/padre/upstreams e instrucciones locales. Padre observado `54b8d5407a8576459448c4d059a877297d18ca7a`; mapa selectivo con lecturas heredadas y nuevas, no auditoría o suite. Cotejar cualquier cambio antes de adaptar. Índice default12/catálogo16 no implica12 runtimes activos; confirmar catálogo/revisión, no copiar memoria default ni crear agentes para compensar.

Conservar Actor/runtimeId/roleId/personaId/kernelTurnId, provenance y assignedBy/To. Outcome/VerificationResult/CapabilityContract tienen semánticas distintas: verified/confidence/idempotency declarados no fabrican autorización o garantía real. LearningFact procedural del padre no es perfil clínico/educativo del cliente. FormSpec chip no concede acceso. Nuevos DTOs de dominio se declaran nuevos; SystemEvent host schemaVersion string1.0/emittedAt/owner/source permitido, no enum inventado.

## Orden

[42 campañas](../campaigns/README.md) y [manifest](../campaigns/campaign.json). C01–C08 fundaciones; C09–C32 los24 módulos del dominio; C33–C42 reportes/UI/SDK/host/cooperación/coste/seguridad/E2E/ops/aceptación.294 tareas con aceptación,84 escenarios; todo NOT_STARTED/NOT_EXECUTED. No plazo ficticio. Gate bloqueado no se vuelve PASS por tener un mock o un documento que diga lo esperado.

## Núcleo específico

LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

El contenido revisado y docente custodian enseñanza; LMS custodia matrículas/actividades por binding; evidencias/attempts son trazables; la competencia es inferencia calibrada, no un atributo clínico del alumno. Estados de dominio propuestos: `needs_analysis, curriculum_draft, content_review, approved_course, enrolled, learning, practice, assessment_pending, evaluated_proposed, human_reviewed, completion_verified, withdrawn`. Entidades: `TrainingAgreement LearnerAuthority LearningObjective CompetencyMap ContentVersion Curriculum CourseVersion Cohort Enrollment AssessmentSpec QuestionRevision Attempt EvidenceRecord TutorSession MasteryObservation CompletionProposal CredentialProposal LRSStatement`. La IA implementadora debe fijar cardinalidad, types, invariantes y pruebas por fase, sin depender de texto libre para representar dinero, permisos o hechos. Desempeño observable, retención/transferencia cuando se midan y cobertura; separar resolver tarea de ayudar a aprender. Tiempo en pantalla/engagement no son competencia o certificación.

Vertical: Necesidad sintética → objetivos → currículo/curso versionado → matrícula sandbox → tutor con pistas → práctica → evaluación con rúbrica → revisión docente → completion propuesta/evidencia → reporte sin acreditación oficial automática.

## Adaptadores

Elegir un camino de piloto, no instalar todos. Moodle/Adapt/LearningLocker/H5P library GPL-3.0 según metadatos, pero módulos y contenido H5P tienen licencias propias. Open edX redirige a openedx/openedx-platform, AGPL-3.0 según repo; no instalar rama master como release. LTI/xAPI son contratos a verificar; la página ADL xAPI no respondió y ese gate queda pendiente. SHAs de referencia son de ramas observadas, no digests/release aprobados; revisar licencia/edición/datos/pesos/plugins y permisos. Si falta red/Docker/cuenta, unit/contratos locales y gate real NOT_VERIFIED. No demos ajenas o datos reales para aparentar éxito. La UI del backend no es producto obligatorio para el cliente.

## Invariantes

Piloto para formación de adultos con datos sintéticos; sin matricular menores reales, emoción/biometría, proctoring invasivo, diagnóstico clínico, nota/certificado oficial o decisión laboral/admisión automatizada. Acreditación/bonificación requieren proceso y evidencia específicos, no promesa por usar LMS. El tutor puede resolver por el alumno, filtrar respuestas o generar contenido erróneo; analytics de empleados puede convertirse en vigilancia o decisión significativa no autorizada.

Preview local sin writes, firma o gasto. Approval atada al hash/revisión/tenant/recipient/alcance/policy/rights/coste/expiry; cambio material invalida. Modelo y avatar no aprueban, compran o adquieren condición profesional. Mandato y autorización se revalidan en cada job; actor de origen y target separados. No URL/método/SQL/HTTP/shell genéricos. No memoria compartida de clientes o secretos al modelo.

Commit local/outbox/audit/key atómico y HTTP separado. Timeout después de posible efecto: reconciliar, no reintentar ciego o por otro proveedor. Restore reaplica supresiones/restricciones y no reenvía historia. Datos faltantes/conflict/stale visibles; fuentes, versión y evidence antes de conclusión. No paridad mundial/cumplimiento/certeza universal.

## Evidencias y checkpoints

Informar tras 5/10/15/20/25/30/35/40/42. Fases PASS/BLOCKED/NOT_VERIFIED con SHA/PR/diff, entorno/versiones, tests ejecutados/pasados/fallidos/skipped, fixtures inicial/final, estado protegido, receipts/correlación sanitizados, coste y riesgos. Cero tests de producto ejecutados en esta entrega. No contar84 escenarios planeados como84tests. Logs públicos sin tokens/PII/originales restringidos.

## Entrega y expansión

Demo sintética A/B/P con fuentes, propuesta/revisión, efecto permitido o artefacto, receipt y reporte reproducible; E2E/fallos/revocación/restore, capacidades reales por versión/edición/rol, manuales/coste/límites. SDK/Hono y patch de wiring se preparan aquí; instalación/cambio en agente requiere otro encargo. Producción/datos reales/efectos regulados o compras después de aceptación explícita del owner. Entregar pendientes como pendientes, con responsable, sin maquillar alcance.
