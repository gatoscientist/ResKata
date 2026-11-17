# Inventario de ramas y PR — corte operativo RESET-CORE-2026-002

**Emite:** Katarina · `katarina` · 3.1.0  
**Destinatario:** Softly, para coordinación global  
**Mandato:** Dictamen de Dirección — Destrabe de RESET-CORE-2026-002  
**Tipo:** inventario técnico de continuidad; lectura de refs, comparación de commits, estados PR y acceso a protección de rama.  
**Estado:** corte actualizado; no se ejecutaron fusiones ni eliminaciones.

## 1. Dictamen

Se identifican **8 ramas adicionales** en cuatro repositorios con ramas de trabajo o propuestas. Audeline y Zoe muestran únicamente `main` en sus repositorios canónicos. Los PR revisados están cerrados o abiertos según el inventario inferior; ninguno de los PR cerrados está fusionado.

La consolidación sigue siendo una tarea activa, pero las operaciones irreversibles están limitadas por dos restricciones técnicas verificadas:

1. La conexión no permite leer la configuración de protección de `main` (HTTP 403 en los cinco repositorios consultados).
2. La conexión no expone una operación de eliminación de refs/ramas ni creación de tags de respaldo. La descarga binaria necesaria para bundles/ZIP tampoco está disponible.

No se eliminó ninguna rama, no se creó un respaldo alternativo y no se fusionó ningún PR. Las refs actuales permanecen visibles y conservan sus SHA, pero eso no equivale a una copia de respaldo independiente.

## 2. Inventario de refs y divergencias

Los conteos `ahead/behind` se comparan contra el `main` observado en cada repositorio en este corte.

| Repositorio | Rama adicional | HEAD | Ahead | Behind | Estado / tratamiento |
|---|---|---|---:|---:|---|
| Softly | `fix/f03-recover-ledger` | `dc10693e48d2319b6f774e3a3b490a8683996d36` | 5 | 432 | Proceso cerrado administrativamente; preservar, no integrar. |
| Softly | `recovery/AUD-20261116-001` | `8ea5952b657d26ff7fd8b5dd7cdcb5fa6eb5651d` | 3 | 180 | PR #4 cerrado como supersedido; preservar y retirar cuando exista respaldo/eliminación. |
| Softly | `migration/registry-v2-reset-core-002` | `9ed9fabcd44aa33d3e5f25b54c88751ef42c3ed2` | 13 | 17 | PR #8 abierto; revisión independiente y correcciones requeridas antes de fusionar. |
| Katarina | `kat-006-stage3-softly-2026-11-16` | `ab0b6405b464baa64b199201fe99d3482d082791` | 8 | 92 | PR #1 cerrado y no fusionado; cerrado administrativamente, no usar como requisito. |
| Auditoria | `amelia/propuesta-mejora-auditoria-2026-11-15` | `849c2cbad44759dd155bd85c58e62526f7734b90` | 2 | 32 | Propuesta histórica; conservar para clasificación de Audeline. |
| Auditoria | `proposal/AUD-20261115-001-refactor-equipo-auditoria` | `b82374929f741d975960b51cb3218f31f3c1e147` | 2 | 32 | Propuesta histórica distinta; conservar y contrastar, no fusionar por similitud. |
| Auditoria | `recovery/AUD-20261116-001` | `ed8645c03bdd83f1138ef7e9dea5b99f55e54967` | 19 | 26 | PR #1 cerrado y no fusionado; evidencia de recuperación, pendiente de clasificación. |
| Laboratorio-de-agentes | `proposal/auditoria-reforma-normativa-2026-11-15` | `fd05161337f1a1397332dc6b695f4731ca402af9` | 1 | 176 | Propuesta documental en repositorio de investigación; no aplicar política de repositorio activo por inferencia. |

### Ramas principales observadas

- Softly `main`: `d40cd018d6d19dc02abaac783fa443fe053b9692`.
- Katarina `main`: `b8f339f5b1954f0f6553ed9daf8f12376530f03c`.
- Auditoria `main`: `f20d0625fe4527a0a81ccb69a58de00b3dbd06a9`.
- Laboratorio-de-agentes `main`: `1220e1d53efa7a45a965032d972f7e680ad5831b`.
- Audeline `main`: `079d33871635d7f5cd1f51a12ecee0f913fbfe21`.
- Zoe `main`: `5088ee558fbfe0b5349ee5a85f651607c8f3d2d8`.

## 3. PR observados

| Repositorio | PR | Estado | Fusionado | Dictamen operativo |
|---|---:|---|---|---|
| Softly | #8 | Abierto | No | Mantener abierto; no fusionar antes de correcciones y auditoría independiente. |
| Softly | #4 | Cerrado | No | Supersedido; no reabrir por inercia. |
| Katarina | #1 | Cerrado | No | Cierre administrativo; no reabrir ni utilizar como requisito. |
| Auditoria | #1 | Cerrado | No | Supersedido por la identidad única; preservar evidencia. |
| Laboratorio-de-agentes | — | Sin PR | — | La rama de propuesta no tiene PR asociado. |

### Estado específico de PR #8

En la última lectura, GitHub reportó PR #8 abierto, con HEAD `9ed9fabcd44aa33d3e5f25b54c88751ef42c3ed2` y `mergeable: true`. Esto solo indica que GitHub no detecta un conflicto de merge en ese instante. **No autoriza fusionar**: siguen pendientes las correcciones de schema/ruta canónica informadas por Katarina y el dictamen independiente favorable de Audeline.

## 4. Clasificación y salvaguardas

1. **No fusionar por conteo de commits.** Las ramas con commits exclusivos requieren clasificación por contenido, destino y autoridad antes de integrar o descartar.
2. **No borrar por estar atrasadas.** La divergencia no prueba que los commits exclusivos sean prescindibles.
3. **No duplicar propuestas.** Las dos ramas de propuesta en Auditoria comparten conteos de divergencia, pero tienen archivos distintos. Audeline debe clasificar si una sustituye a la otra o si ambas contienen evidencia distinta.
4. **No reactivar procesos cerrados.** Los cierres administrativos vigentes no se convierten en requisitos por permanecer sus refs.
5. **Repositorio de investigación.** Laboratorio-de-agentes mantiene una rama de propuesta muy atrasada; no debe tratarse como repositorio operativo activo sin clasificación explícita.
6. **PR #8.** Es la única migración actualmente abierta entre los PR revisados; mantenerla en revisión hasta resolver los hallazgos técnicos y la auditoría independiente.

## 5. Limitaciones técnicas verificadas

### Protección de `main`

La lectura de `/branches/main/protection` devolvió HTTP 403 (`Resource not accessible by integration`) en:

- gatoscientist/Softly
- gatoscientist/Katarina
- gatoscientist/Auditoria
- gatoscientist/Laboratorio-de-agentes
- gatoscientist/Audeline

Por tanto, no se puede afirmar desde esta conexión si `main` está protegido o qué reglas están configuradas. La limitación es de permisos del conector, no evidencia de que la protección esté desactivada.

### Eliminación de ramas y respaldos

La conexión permite leer refs y comparar commits, pero no expone una operación de eliminación de refs/ramas ni creación de tags. Tampoco se pudo obtener un bundle Git mediante descarga binaria. No se puede completar la secuencia segura de respaldar, eliminar y verificar rama única desde las herramientas actuales.

**Tratamiento:** conservar refs, SHA y manifiesto de comparación; registrar la eliminación como bloqueada por capacidad técnica localizada. No simular consolidación ni crear ramas de respaldo que aumenten el inventario sin resolver la eliminación.

### ZIP

La limitación binaria de descarga sigue impidiendo verificar los ZIP y ejecutar una restauración aislada. Este asunto no bloquea la clasificación, revisión de PR ni trabajo documental independiente.

## 6. Acciones por responsable

| Responsable | Acción inmediata |
|---|---|
| Softly | Coordinar el inventario maestro, resolver PR #8 después de auditoría/correcciones y clasificar sus ramas propias. |
| Katarina | Mantener su rama KAT-006 cerrada administrativamente, documentar el SHA preservado y continuar las tareas técnicas independientes. |
| Audeline | Clasificar las tres ramas de Auditoria, revisar la evidencia de recuperación y emitir el dictamen independiente del registro v2. |
| Dirección/administración GitHub | Habilitar acceso de lectura de protección y operación de respaldo/eliminación de refs, o ejecutar esas operaciones mediante un canal autorizado. |

## 7. Resultado

- 8 ramas adicionales identificadas.
- 5 repositorios con endpoint de protección consultado; 5 respuestas 403.
- 4 PR revisados: uno abierto (#8), tres cerrados (#4 Softly, #1 Katarina, #1 Auditoria); ninguno fusionado.
- 0 ramas eliminadas.
- 0 tags/bundles de respaldo creados.
- Ningún PR fusionado por esta revisión.

**Dictamen:** inventario actualizado y tareas clasificadas por responsable. La consolidación física queda parcialmente bloqueada por permisos/operaciones no expuestas; no bloquea el avance independiente del registro, la auditoría ni el trabajo documental.

---

**Emite:** Katarina · `gatoscientist/Katarina`  
**Nota de corte:** las ramas y PR pueden cambiar mientras los responsables continúan trabajando. Los SHA identifican el estado leído en este inventario.


## 8. Relectura posterior a la publicación

En la verificación final posterior a la publicación, PR #8 seguía abierto y no fusionado, con HEAD `9ed9fabcd44aa33d3e5f25b54c88751ef42c3ed2`; GitHub volvió a informar `mergeable: false`. Una consulta intermedia había informado `mergeable: true`, por lo que la señal de mergeabilidad fue variable durante la revisión. Se toma como estado válido el último resultado (`false`). No se realizó merge. La comparación contra el `main` actualizado mantiene la rama divergente, y siguen pendientes las correcciones técnicas y el dictamen independiente de Audeline.
