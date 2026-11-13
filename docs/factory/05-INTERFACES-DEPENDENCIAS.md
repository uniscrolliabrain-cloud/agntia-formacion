# Mapa de autoridad, servicios hermanos y adaptadores

## Invariante principal
Duplicación de conocimiento, interfaces y capacidades está permitida. **Efecto real único y autorizado por intención**; AuthorityMap por tenant, workflow, recurso, canal y versión. El padre conserva kernel, identidades canónicas, grafo, bus y SOPs; Formación puede ejecutar su lógica especialista por contrato y mandato, no crear un segundo kernel soberano.

## Cooperación
| Dominio | Fuente/rol preferente | Frontera |
|---|---|---|
| Formación | objetivos, currículo, tutoría, contenidos y evidencia | No envía sin canal autorizado |
| Marketing | campañas, entregabilidad, newsletters cuando delegado | No modifica competencias sin Formación |
| Redes | publicación social y community | No publica borrador sin aprobación |
| Clientes | CRM, tickets, preferencias y contacto | No convertir contacto en alumno autorizado |
| Gestoría + RRHH | rotas, fichajes, ausencias, vacaciones, nóminas y gestión laboral | Formación solo consume necesidades agregadas o datos autorizados |
| Finanzas | tesorería, pagos, Qonto/BBVA si licencias/mandatos permiten | No cobrar ni ordenar pagos desde Formación |
| Legal | RGPD, AI Act, revisión jurídica | Contenido educativo no es asesoría profesional definitiva |
| Ciberseguridad | observabilidad transversal, seguridad y auditoría | Telemetría no habilita lectura indiscriminada de datos |
| Branding/Diseño/Vídeo | identidad, diseño web, producción audiovisual | Artefactos por encargo con derechos y aprobación |
| Comunicación (futuro) | por definir | No reservar autoridad sin contrato |

## Adaptadores
Puerto tipado `LearningContentPublisher`, `NewsletterDeliveryPort`, `LMSPort`, `KnowledgeSourcePort`, `IdentityBridgePort`, `EvidenceSinkPort` (**PROPOSED**). Implementaciones posibles: Moodle, Open edX, H5P, LTI/xAPI, email provider, CRM, Airtable, Google Drive, APIs de cliente y MCP cuando se autoricen. Cada adapter declara: capability, tenantBinding, scopes, data residency, consent, rateLimit, cost, timeout, retries, idempotency, reconciliation, sourceOfTruth, health, circuitBreaker, audit. No asumir que MCP es seguro ni que el proveedor permite todas las mutaciones.

## Canales
Chat propio, Anam, teléfono, WhatsApp, correo y portal pueden invocar la misma capacidad, pero necesitan identidad/consentimiento apropiados a cada canal. La voz del avatar no es autorización de una acción sensible por sí sola.

## Bridge padre
Contratos canónicos por SHA, versionado semántico y test de compatibilidad. Eventos de Formación a bus padre mediante mapping, no introducir enums por adivinación. Datos empresariales con provenance/ACL; minimizar eventos con payload refs, hashes y timestamps. Rechazar llamadas cross-tenant sin delegación explícita. Integración de Marketing y Formación para newsletter debe definir dueño del envío antes de implementar.
