# Producto, capacidades y límites

## Resultado para el cliente

Diseñar e impartir formación con objetivos, contenidos, prácticas y evidencia de aprendizaje, integrando LMS y tutores IA sin confundir ayuda con acreditación o vigilancia del alumno. El cliente contrata una especialidad con entregables revisables, no una simulación de personas trabajando. El avatar explica datos, fuentes, límites y bloqueos; el owner puede editar propuestas y aprobar el resultado concreto. Humanos y agentes generalistas usan el mismo servicio bajo permisos. Un cliente externo tiene portal propio y Supabase; no debe entrar en AgntiaPro o paneles ERP/LMS/CRM para obtener valor.

| Pilar | Valor previsto | Prueba exigida |
|---|---|---|
| Diagnóstico de necesidades y objetivos observables | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |
| Contenidos/licencias y diseño instruccional | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |
| LMS, cohortes, matrículas y rutas | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |
| Tutoría con agencia del alumno | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |
| Evaluación revisada y evidencias de progreso | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |
| Analítica, accesibilidad y entrega de aprendizaje | Trabajo específico con datos/objetivos del encargo | Fuentes, revisión, ACL, versión y receipt/artefacto verificables |

Estas capacidades son diseño, no features implementadas. Las 24 fases de dominio detallan objetos, invariantes y escenarios; se complementan con ocho fundaciones y diez fases de exposición/seguridad/operaciones hasta completar42. No instalar todos los backends para aparentar cobertura. Elegir un camino P0 funcional, conservar capacidades opcionales deshabilitadas hasta prueba real.

## Actores y datos

Organización operadora emplea al agente canónico del padre; tenant representa empresa cliente del SaaS; proyectos/materias/cohortes/cuentas son recursos internos; personas registradas en datos no se convierten en usuarios autorizados por importarlas. Usuario válido no ve todo el tenant: ACL por recurso/campo, representación y propósito cuando corresponde. Un mismo humano puede trabajar en varios tenants y debe seleccionar ámbito verificado explícitamente.

Entidades propuestas: `TrainingAgreement LearnerAuthority LearningObjective CompetencyMap ContentVersion Curriculum CourseVersion Cohort Enrollment AssessmentSpec QuestionRevision Attempt EvidenceRecord TutorSession MasteryObservation CompletionProposal CredentialProposal LRSStatement`. Sus IDs son del servicio salvo mapeo nativo declarado. El contenido revisado y docente custodian enseñanza; LMS custodia matrículas/actividades por binding; evidencias/attempts son trazables; la competencia es inferencia calibrada, no un atributo clínico del alumno. La fuente remota y el snapshot local tienen autoridad/frescura distintas. El modelo no rellena campos desconocidos para completar una pantalla; faltan datos significa pending/blocked, no falso éxito.

## Vertical inicial

Necesidad sintética → objetivos → currículo/curso versionado → matrícula sandbox → tutor con pistas → práctica → evaluación con rúbrica → revisión docente → completion propuesta/evidencia → reporte sin acreditación oficial automática.

Usar empresas/personas/documentos sintéticos y sink/entorno de prueba, con dos tenants y operador separado. Un borrador no es acto externo ni una certificación. Cualquier conector que falte se indica NOT_VERIFIED, sin presentar mock como instalación real. El piloto puede entregar conocimiento y propuesta útil aunque un efecto sensible quede deliberadamente fuera.

## Límites de efecto

Piloto para formación de adultos con datos sintéticos; sin matricular menores reales, emoción/biometría, proctoring invasivo, diagnóstico clínico, nota/certificado oficial o decisión laboral/admisión automatizada. Acreditación/bonificación requieren proceso y evidencia específicos, no promesa por usar LMS.

El tutor puede resolver por el alumno, filtrar respuestas o generar contenido erróneo; analytics de empleados puede convertirse en vigilancia o decisión significativa no autorizada. Las revisiones son actos humanos verificables ligados al payload y versión. No las fabrica un nombre de agente, un sí hablado o un campo approved=true. La aceptación comercial del servicio, el acceso a datos, la revisión editorial y la autorización de efecto son hechos distintos.

## Cooperación y evolución

Se admite duplicación funcional entre los nueve SaaS y el padre. ServiceAgreement/WorkOrder fija alcance, responsable y sistema ejecutor por efecto. Un módulo local acotado puede cubrir una función sin contratar un hermano, pero no inventa autorización profesional, saldo, dictamen o evidencia. Integrar no significa compartir todos los datos: contratos mínimos, propósito, ACK y trazabilidad.

La expansión exige nuevos permisos, pruebas y contratos cuando se habiliten datos reales, proveedores pagados o funciones reguladas. La campaña no garantiza paridad con líderes, precisión universal o disponibilidad jurídica de cada función. Producto completo significa capacidades verificadas en ámbito concreto con operación/recuperación y límites visibles, no una lista de logos.
