# Aceptación del piloto · pendiente

Todos los puntos **NOT_EXECUTED**; este diseño no acredita producto o aceptación del owner.

| Gate | Evidencia mínima |
|---|---|
| Baseline | SHAs/instrucciones/fuentes/licencias y diferencias |
| Identidad/twin | Supabase JWT, membership/ACL, mandato canónico, scope y revocación |
| Persistencia | FK/RLS/roles reales, CAS/audit/outbox, restore |
| Datos | Fuentes, originales, hash/revisión, missing/stale/conflict explícitos |
| Dominio | Resultado y estado protegido conforme invariantes de cada módulo |
| Revisión | Humano/competencia/representación cuando aplique, approval exacta y vigente |
| Efecto | Intent/key/payloadHash/emisor único, receipt o incertidumbre visible |
| Seguridad | Dos tenants y recursos internos, secretos, prompt injection, SSRF |
| UI/AV | Responsive, accesibilidad/ES-EN-FR, Anam scoped o fallback texto |
| Operación | Backup/restore/rotación/retención/runbooks/costes medidos |
| Integración | Contratos API-SDK-host, fake separado de runtime real, padre intacto |

Vertical: Necesidad sintética → objetivos → currículo/curso versionado → matrícula sandbox → tutor con pistas → práctica → evaluación con rúbrica → revisión docente → completion propuesta/evidencia → reporte sin acreditación oficial automática.

Límite: Piloto para formación de adultos con datos sintéticos; sin matricular menores reales, emoción/biometría, proctoring invasivo, diagnóstico clínico, nota/certificado oficial o decisión laboral/admisión automatizada. Acreditación/bonificación requieren proceso y evidencia específicos, no promesa por usar LMS. Criterio particular: LearningObjective y AssessmentSpec versionados; hints por nivel con límite de disclosure y modo práctica/evaluación separados. MasteryObservation conserva skill, evidencia, fecha/modelo/confianza y cobertura, no certeza. Completion requiere reglas/cutoff y prueba de LMS/attempts revisados; CredentialProposal no emite acreditación. No reutilizar LearningFact de agentes como perfil clínico del alumno.

Ejecutar E2E A–I y escenarios de [evaluación](../09-evaluacion.md).0 fuga tenant/recurso,0 secretos centinela,0 approvals/competencia fabricadas,0 duplicado replay y0 efecto fuera de alcance. Un crítico fallido bloquea. p50/p95/coste/calidad/cobertura se miden con entorno/workload/versión; no objetivos ya alcanzados ficticios.

Capacidad opcional sin proveedor/licencia/permiso queda disabled y NOT_VERIFIED; no se oferta como soportada. Un mock PASS no acredita la instalación. Datos reales/producción/compras/wiring en padre necesitan otra autorización. El owner debe poder reconstruir un entregable desde fuente y actor hasta revisión/receipt y entender qué sigue pendiente.
