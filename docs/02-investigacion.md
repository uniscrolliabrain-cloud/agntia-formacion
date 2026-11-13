# Investigación y decisiones

Fuentes primarias consultadas selectivamente 2026-11-13; no revisión sistemática ni benchmarks reproducidos. El registro separa abstract/README/documentación/anuncio, acceso fallido y validación de runtime. Revalidar al implementar porque versiones, planes y leyes pueden cambiar.

| Paper | Decisión de diseño (inferencia propia) |
|---|---|
| P01: TeachArena · [arXiv](https://arxiv.org/abs/2605.14322) | Revisión8noviembre2026: juicio pedagógico, interacción y artefacto LMS se evalúan por separado y en conjunto. |
| P02: EduClaw-Bench · [arXiv](https://arxiv.org/abs/2608.03206) | Relación longitudinal y estado del aprendiz requieren evaluación más allá de una sesión; simulación no prueba aprendizaje humano. |
| P03: Teaching-over-Solving Diagnostic · [arXiv](https://arxiv.org/abs/2606.16206) | Separar resultados de resolución y apoyo pedagógico; pistas calibradas y agencia del estudiante, sin filtrar respuesta evaluada. |

No se trasladan scores, porcentajes, tamaños de muestra o eficacia de los autores a Agntia. Leer un abstract no demuestra replicación de método o licencia de sus datasets. Se diseñarán fixtures originales con datos sintéticos y criterios de estado/efecto/proceso; antes de incorporar harness/datos ajenos revisar licencia, splits, dependencia de modelos y términos.

## Conceptos propuestos

Evidence-to-Effect Ledger une fuente, versión, actor, mandato, propuesta, approval y resultado confirmado. Scope-bound Twin conserva una identidad canónica y especialización local por cliente sin memoria global. Reviewable Decision Contract define hechos, estado protegido, resultado y qué requiere humano/competencia. Son propuestas de ingeniería de esta entrega, no afirmación de novedad científica o patente.

Para Formación empresarial, tutoría y aprendizaje verificable, la decisión particular es: LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

## Referentes actuales

| Referencia | Patrón estudiado |
|---|---|
| V01: Moodle | Subsystem IA por plugins y versiones; docs5.0 no prueban capabilities de otra instalación o Moodle Workplace. |
| V02: Khanmigo | Patrón de tutor y apoyo docente; límites de acceso/edad/planes no se extrapolan a clientes. |
| V03: Docebo | Patrón LMS empresarial/readiness y rutas; no certificación o bonificación heredada. |

Las páginas oficiales describen oferta y novedades, no se probaron productos ni cuentas. No adoptar sus claims de cumplimiento, seguridad, productividad o certificaciones como propios. API/plan/edición/territorio y coste son gates de implementación. Fuentes no accesibles se registran, no sustituyen con una afirmación de capacidad. Algunas URLs cambian de ruta o versión: conservar el origen/redirect y no fijar un endpoint por memoria.

## Repos públicos

Se consultaron metadatos, SHA y README de los candidatos de [repositories.json](research/repositories.json). No son una auditoría completa ni se han instalado. Rama main/master/develop/hotfix no es un pin de release. Selección posterior por compatibilidad/licencia/recursos/ACL y evidencia con una instancia aislada. Moodle/Adapt/LearningLocker/H5P library GPL-3.0 según metadatos, pero módulos y contenido H5P tienen licencias propias. Open edX redirige a openedx/openedx-platform, AGPL-3.0 según repo; no instalar rama master como release. LTI/xAPI son contratos a verificar; la página ADL xAPI no respondió y ese gate queda pendiente.

## Fuentes jurídicas y de seguridad

Supabase JWT/RLS y Anam se estudiaron en documentación oficial; nunca credenciales ni sesiones reales. Normativa común y específica en Dxx requiere interpretación contextual, territorio/fecha y revisión humana. No prometer cumplimiento universal por importar una librería o tener un dashboard. Un uso no cubierto debe quedar unsupported/needs_review.

| Fuente específica | Qué exige al diseño |
|---|---|
| D01: [Formación empleo](https://www.boe.es/buscar/act.php?id=BOE-A-2015-9734) | Formación bonificada/acreditada exige proceso y condiciones aplicables; no se garantiza por generar un curso. |
| D02: [LTI](https://www.1edtech.org/standards/lti) | Estándar consultado; implementación/versiones/OIDC/deep linking y aislamiento necesitan pruebas. |
| D03: [xAPI](https://adlnet.gov/projects/xapi/) | Consulta agotó tiempo; no se declara interoperabilidad LRS hasta validar especificación vigente. |

Mantener preguntas abiertas: derechos/ediciones, fuente incompleta, verificación real de proveedor, operación humana y coste medido. El mapa del padre conserva lecturas heredadas y nuevas por el mismo SHA; no supone una relectura total. Cualquier divergencia futura se coteja antes del wiring. Nunca modificar el padre para que una prueba propia pase.
