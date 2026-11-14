# FOR-C01 — Codex revisor independiente

Leer factory, léxico, ADTC, prep, originales C01/C02 y patchsets. Recibir SHA congelado de Freebuff; **no modificar rama de implementador**.

Comprobar (1) rutas/SHAs de ambos repos, (2) contratos Actor/Tenant/Events/Approval verificados en código, (3) ausencia de cambios en padre/main, (4) integridad de 42 IDs y enlaces, (5) no PII/secrets, (6) estados NOT_EXECUTED correctos, (7) diferencias producto semanal reflejadas, (8) correlación/causalidad coherentes con el padre, sin inventar enum nativo. Ejecutar validación documental si entorno disponible y registrar comandos/exit codes. Entregar REVIEW.md con findings P0–P3, pruebas reproducibles y decisión VERIFIED/BLOCKED/CHANGES_REQUESTED por SHA.
