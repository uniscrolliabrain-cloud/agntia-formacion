# Campaña de42 fases

Diseño para una implementación futura autorizada. **42 campañas,294 tareas,84 escenarios, NOT_STARTED/NOT_EXECUTED.** No plazo ficticio de siete días. No modificar agente. Fuentes/contratos no equivalen a capacidades probadas.

[Manifest estructurado](campaign.json): IDs/dependencias, campos, operaciones, invariantes, tareas/aceptación, gates, bloqueos y rollback. Rutas de artefactos son propuestas, no archivos existentes.

C01–C08 fundaciones; C09–C32 dominio; C33–C42 exposición/servicio/seguridad/operaciones/aceptación. Avance por gates con capacidades no verificadas deshabilitadas; un fake no pasa gate real. Checkpoints cada 5 y al final de 2.

| Fase | Documento | Estado | Checkpoint |
|---|---|---|---|
| 01 | [Baseline, fuentes y alcance](01-baseline-fuentes-y-alcance.md) | NOT_STARTED | — |
| 02 | [Autoridad por dominio y contrato SaaS](02-autoridad-por-dominio-y-contrato-saas.md) | NOT_STARTED | — |
| 03 | [Supabase JWT y principal](03-supabase-jwt-y-principal.md) | NOT_STARTED | — |
| 04 | [Twins y nomenclatura canónica](04-twins-y-nomenclatura-canonica.md) | NOT_STARTED | — |
| 05 | [DTOs, esquemas y errores](05-dtos-esquemas-y-errores.md) | NOT_STARTED | Informe |
| 06 | [Persistencia, RLS y migraciones](06-persistencia-rls-y-migraciones.md) | NOT_STARTED | — |
| 07 | [Mandatos, finalidad y aprobaciones](07-mandatos-finalidad-y-aprobaciones.md) | NOT_STARTED | — |
| 08 | [Secretos, discovery y aislamiento remoto](08-secretos-discovery-y-aislamiento-remoto.md) | NOT_STARTED | — |
| 09 | [Necesidades y objetivos](09-necesidades-y-objetivos.md) | NOT_STARTED | — |
| 10 | [Competencias y mapa](10-competencias-y-mapa.md) | NOT_STARTED | Informe |
| 11 | [Currículo y secuenciación](11-curriculo-y-secuenciacion.md) | NOT_STARTED | — |
| 12 | [Contenidos y licencias](12-contenidos-y-licencias.md) | NOT_STARTED | — |
| 13 | [Diseño instruccional](13-diseno-instruccional.md) | NOT_STARTED | — |
| 14 | [Validación de contenido](14-validacion-de-contenido.md) | NOT_STARTED | — |
| 15 | [Adaptador Moodle](15-adaptador-moodle.md) | NOT_STARTED | Informe |
| 16 | [Adaptador Open edX](16-adaptador-open-edx.md) | NOT_STARTED | — |
| 17 | [Contenido H5P/Adapt](17-contenido-h5p-adapt.md) | NOT_STARTED | — |
| 18 | [LTI y lanzamiento](18-lti-y-lanzamiento.md) | NOT_STARTED | — |
| 19 | [xAPI y LRS](19-xapi-y-lrs.md) | NOT_STARTED | — |
| 20 | [Cohortes y matrículas](20-cohortes-y-matriculas.md) | NOT_STARTED | Informe |
| 21 | [Rutas adaptativas](21-rutas-adaptativas.md) | NOT_STARTED | — |
| 22 | [Tutor y memoria acotada](22-tutor-y-memoria-acotada.md) | NOT_STARTED | — |
| 23 | [RAG educativo](23-rag-educativo.md) | NOT_STARTED | — |
| 24 | [Práctica y feedback](24-practica-y-feedback.md) | NOT_STARTED | — |
| 25 | [Banco de preguntas](25-banco-de-preguntas.md) | NOT_STARTED | Informe |
| 26 | [Rúbricas y evaluación](26-rubricas-y-evaluacion.md) | NOT_STARTED | — |
| 27 | [Evidencia de intentos](27-evidencia-de-intentos.md) | NOT_STARTED | — |
| 28 | [Revisión docente y recurso](28-revision-docente-y-recurso.md) | NOT_STARTED | — |
| 29 | [Completion y certificados](29-completion-y-certificados.md) | NOT_STARTED | — |
| 30 | [Accesibilidad e idiomas](30-accesibilidad-e-idiomas.md) | NOT_STARTED | Informe |
| 31 | [Analítica de aprendizaje](31-analitica-de-aprendizaje.md) | NOT_STARTED | — |
| 32 | [Retención y protección](32-retencion-y-proteccion.md) | NOT_STARTED | — |
| 33 | [Reportes, dashboard e infografías](33-reportes-dashboard-e-infografias.md) | NOT_STARTED | — |
| 34 | [Portal responsive, chat y Anam](34-portal-responsive-chat-y-anam.md) | NOT_STARTED | — |
| 35 | [SDK TypeScript, Hono y tools](35-sdk-typescript-hono-y-tools.md) | NOT_STARTED | Informe |
| 36 | [Bridge de agente y eventos](36-bridge-de-agente-y-eventos.md) | NOT_STARTED | — |
| 37 | [Cooperación y handoff empresarial](37-cooperacion-y-handoff-empresarial.md) | NOT_STARTED | — |
| 38 | [Modelos, coste y observabilidad](38-modelos-coste-y-observabilidad.md) | NOT_STARTED | — |
| 39 | [Privacidad y pruebas adversariales](39-privacidad-y-pruebas-adversariales.md) | NOT_STARTED | — |
| 40 | [Vertical E2E y fallos distribuidos](40-vertical-e2e-y-fallos-distribuidos.md) | NOT_STARTED | Informe |
| 41 | [Operaciones, CI, backup y release](41-operaciones-ci-backup-y-release.md) | NOT_STARTED | — |
| 42 | [Aceptación, evidencia y handoff final](42-aceptacion-evidencia-y-handoff-final.md) | NOT_STARTED | Informe |

Informe: SHA/PR/diff, versiones/entorno, fases PASS/BLOCKED/NOT_VERIFIED, tests realmente ejecutados/pasados/fallidos/skipped, fixtures/receipts/fuentes, costo/riesgos y siguiente dependencia. No contar escenarios planeados como tests. STOP ante fuga, bypass de autorización/revisión, secreto, doble efecto o pérdida de audit. Producción/pagos/firmas/actos regulados fuera de esta entrega.
