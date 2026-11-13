# Adaptadores y licencias

Todos NOT_IMPLEMENTED/NOT_VERIFIED en runtime. [Repos por SHA](research/repositories.json); lectura de metadatos/README y licencias selectivas, no auditoría completa. No se han clonado/instalado ni usado cuentas demo ajenas. La elección de release/digest estable queda pendiente.

| ID | Repositorio | Licencia metadata | Uso/precaución |
|---|---|---|---|
| R01 | [moodle/moodle](https://github.com/moodle/moodle/tree/afbcc55fa1bd80dcdd887b8965dd8c28c0f3bbda) | GPL-3.0 | Candidato de dominio o referencia; capacidades/edición/ACL se verifican por instalación |
| R02 | [openedx/openedx-platform](https://github.com/openedx/openedx-platform/tree/32e2f7d8ec6a3bfff1f4695fc2360f71ff52f1a6) | AGPL-3.0 | Candidato de dominio o referencia; capacidades/edición/ACL se verifican por instalación |
| R03 | [h5p/h5p-php-library](https://github.com/h5p/h5p-php-library/tree/2d7f937a03c925e1332651b16ac6e56ac7544431) | GPL-3.0 | Candidato de dominio o referencia; capacidades/edición/ACL se verifican por instalación |
| R04 | [adaptlearning/adapt_framework](https://github.com/adaptlearning/adapt_framework/tree/f0a705d9cd24d915acef6eeb7b1f6da4ed5e4131) | GPL-3.0 | Candidato de dominio o referencia; capacidades/edición/ACL se verifican por instalación |
| R05 | [LearningLocker/learninglocker](https://github.com/LearningLocker/learninglocker/tree/5fec948a823e372e740df521aa3684c8df1dcba7) | GPL-3.0 | Candidato de dominio o referencia; capacidades/edición/ACL se verifican por instalación |

Moodle/Adapt/LearningLocker/H5P library GPL-3.0 según metadatos, pero módulos y contenido H5P tienen licencias propias. Open edX redirige a openedx/openedx-platform, AGPL-3.0 según repo; no instalar rama master como release. LTI/xAPI son contratos a verificar; la página ADL xAPI no respondió y ese gate queda pendiente.

La licencia de código no cubre automáticamente pesos/modelos, contenido de cursos, tipografías, plantillas, corpus judiciales, datos actuariales, plugins o servicios cloud. No copiar upstream por comodidad. API/proceso separado es arquitectura recomendada, no excepción jurídica universal. Leer obligaciones de modificación/distribución/servicio en red y compatibilidad antes de incorporar material.

## Registro y discovery

ProviderConnection por tenant/proyecto, endpointRef/secretRef solo servidor, versión/edición y binding remoto. No aceptar URL, base de datos, company/site/course/workspace, token o método libre desde un modelo. Bot mínimo por ámbito, rotación sin perder links y secretos externos. DNS/IP/redirect/tamaño/tiempo/egress protegidos. Public JSON minimizado, no credenciales/nombres internos innecesarios.

CapabilityReport distingue documented, verified_runtime, unknown, unsupported, forbidden y not_configured, con fecha/expiry/evidencia. Un200 con HTML/estructura errónea o empresa equivocada no es healthy. Sin permiso no se cae a admin; no crear registros reales para probar discovery. Unknown deshabilitado y advertencia útil. Cada versión/edición/modulo/rol puede invalidar el report.

## Lectura, staging y sincronización

ExternalLink por tenant/connection/model/externalId/localKind, IDs strings opacos, sourceHash/remoteVersion/mapperVersion. No mapear por nombre o posición. Import preview conserva warnings/campos pendientes/procedencia; aceptación local no fabrica revisión profesional, consentimiento o emisión remota. Repetición idéntica no duplica; cambio legítimo crea nueva revisión/conflicto según AuthorityMap.

Cursores/paginación estables con overlap si hace falta; watermark después de commit local. Barridos detectan archivado/borrado remoto sin destruir historia. Conflicto con dato revisado bloquea overwrite. Dos sistemas que reclaman autoridad por mismo campo/efecto deben acordarlo antes de bidireccionalidad, no last-write-wins silencioso.

## Escritura

Dry-run puro local; preview con diff/alcance/coste y aprobación cuando corresponda. Algunos endpoints llamados test envían o modifican estado: demostrar semántica antes de usarlos. Persistir intent/audit/key/outbox antes de HTTP; cada llamada remota tiene su transacción propia. Si el proveedor acepta y se pierde respuesta, reconciliar por referencia segura; si no existe, bloquear/escalar, no duplicar con otra key/proveedor. No delete/unlink/submit/post/execute genéricos al agente.

El piloto conserva este límite: Piloto para formación de adultos con datos sintéticos; sin matricular menores reales, emoción/biometría, proctoring invasivo, diagnóstico clínico, nota/certificado oficial o decisión laboral/admisión automatizada. Acreditación/bonificación requieren proceso y evidencia específicos, no promesa por usar LMS. Un backend faltante queda explícito; un fake útil no se ofrece como conector real. La UI del proveedor puede existir para administración interna, sin ser interfaz obligatoria del cliente. Feature flags detienen nuevas operaciones sin borrar evidencia/links ni simular rollback de efectos externos.
