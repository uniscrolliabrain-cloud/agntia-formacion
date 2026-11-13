# Contrato distribuido de causalidad, IDs, observabilidad y reconstrucción

**ADTC v0.1 — propuesta, NO contrato desplegado.** Obligatorio para todos los nuevos adapters/skills/workers. El padre es autoridad del bus empresarial; Ciberseguridad consume/proyecta telemetría sin convertirse en dependencia síncrona crítica.

## Envelope lógico propuesto
```json
{
  "schemaVersion": "adtc/0.1",
  "eventId": "new-unique-id",
  "eventType": "formacion.learning_brief.proposed",
  "tenantId": "server-verified",
  "actorId": "verified-actor",
  "taskId": "canonical-task-ref-if-any",
  "correlationId": "stable-business-chain",
  "causationId": "parent-event-id-or-null",
  "requestId": "ingress-request-id",
  "traceId": "w3c-trace-id",
  "spanId": "current-span-id",
  "idempotencyKey": "effect-scope-key-or-null",
  "occurredAt": "2026-11-13T00:00:00Z",
  "source": "agntia-formacion",
  "resourceRefs": ["opaque-ref"],
  "evidenceRefs": ["sanitized-ref"],
  "payloadRef": "encrypted-access-controlled-ref"
}
```
No confundir este envelope con el `SystemEvent` real del padre; bridge debe mapear sus enums/campos verificados. No introducir campos en el bus sin contrato versionado.

## Reglas
1. Conservar `tenantId`, `correlationId` y principal/delegación verificables a lo largo de toda la cadena; en llamadas cross-tenant, registrar tenant origen y destino por separado, con mandato explícito.
2. Cada evento nuevo genera `eventId`; su `causationId` apunta al evento causante. Cada intento genera attemptId y spanId; un retry no crea otra intención empresarial.
3. `traceId` sigue W3C Trace Context y puede enlazar spans; no es fuente de verdad de auditoría durable. Correlation ID persiste incluso cuando se reinicia una traza.
4. Outbox transaccional, consumer inbox/dedupe, retries con presupuesto, dead-letter y reconciliación de `outcome_unknown`. Eventos sin consumidor o sin resultado generan alerta, no se pierden silenciosamente.
5. Audit append-only con esquema/versión/hash/refs, retención y ACL por tenant. Logs/OTel pueden muestrearse; evidencias críticas no.
6. Prohibido propagar contenido educativo, datos de empleados, PII, secretos, evaluaciones o datos sensibles a todos los repositorios. Usar refs, hashes, minimización, cifrado y accesos con propósito.
7. Export de observabilidad multitenant: filtros server-side y RLS/ACL; un tenant no puede inferir existencia de otro por trazas, métricas o búsquedas.
8. Ciberseguridad centraliza paneles, alertas, reconstrucción, costes, latencia, errores y seguridad de toda la familia; si observabilidad está caída, la operación de negocio conserva garantías y emite backlog durable.
9. Eventos con `schemaVersion` desconocida → cuarentena o adapter explícito; nunca parsear por similitud de nombres.
10. Replays de negocio deben separar simulación de efectos reales; no reenviar newsletters por replay de auditoría.

## Test matrix P0
- Correlación intacta al cruzar padre → Formación → Marketing → proveedor → receipt → padre.
- Evento hijo conserva causationId correcto; eventId/spanId distintos.
- Timeout de envío no dispara segundo email sin reconciliación.
- Job revocado antes del efecto se bloquea.
- Trace/metric/log de tenant A no visible a B, incluidos errores y cardinalidad.
- Observabilidad desconectada no detiene outbox de negocio ni pierde evidencia durable.
- Schema drift/duplicado/out-of-order/dead-letter visible y recuperable.
- Audit muestra input refs → decisiones → approvals → intent → attempt → receipt → output, sin exponer payloads indebidos.

## Métricas mínimas
`workflow_started_total`, `workflow_blocked_total`, `effect_outcome_unknown_total`, `outbox_lag_seconds`, `dead_letter_total`, `provider_latency_ms`, `model_cost_eur`, `newsletter_delivery_receipts_total`, `learning_evidence_count`; dimensiones tenant de cardinalidad acotada y con controles de acceso. Definir SLOs tras baseline real, no inventarlos.
