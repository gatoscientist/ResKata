# RESET-CORE-2026-002 — Inventario técnico inicial de Katarina

**Emite:** Katarina (reconocimiento técnico asistido por integración GitHub)  
**Fecha:** 2026-11-16  
**Repositorio:** gatoscientist/Katarina  
**Rama inspeccionada:** main  
**Mandato:** RESET-CORE-2026-002  
**Estado:** reconocimiento parcial persistido; no es inventario global certificado.

## 1. Alcance y método

Se consultaron los repositorios gatoscientist/Katarina, Softly, TITAN, Cytryna y Laboratorio-de-agentes. Se enumeraron ramas mediante búsqueda de ramas, PR mediante búsqueda de solicitudes, archivos modificados por PR y comparaciones de commits para las ramas no-main. Se leyó la orden canónica RESET-CORE-2026-002 y artefactos de investigación KAT-SOFTLY-FUTURE-BLOCKERS-2026-001 y KAT-006.

**Límite:** la integración disponible no expuso un listado completo de árbol de cada repositorio ni permitió verificar todos los archivos, instalaciones, permisos efectivos, herramientas, sesiones o instancias activas. Los inventarios de abajo son cobertura observada, no una declaración de inexistencia de activos no encontrados. No se ejecutaron cambios destructivos, fusiones, cierres de PR ni eliminación de ramas.

## 2. Repositorios y ramas observadas

| Repositorio | Ramas observadas | PR encontrados | Observación |
|---|---|---:|---|
| Katarina | main; kat-006-stage3-softly-2026-11-16 | 1 | PR #1 KAT-006 etapa 3 |
| Softly | main; fix/f03-recover-ledger; recovery/AUD-20261116-001 | 1 | PR #4 Audelinesay |
| TITAN | main | 3 | PR #1, #2 y #3 |
| Cytryna | main | 11 | PR #1 a #11 |
| Laboratorio-de-agentes | main; proposal/auditoria-reforma-normativa-2026-11-15 | 0 | Propuesta histórica en rama divergente |

La búsqueda de PR devuelve solicitudes históricas además de las abiertas; el estado exacto debe confirmarse con lectura individual de cada PR antes de resolverlos.

## 3. Katarina: ramas y KAT-006

PR #1: https://github.com/gatoscientist/Katarina/pull/1  
Rama: kat-006-stage3-softly-2026-11-16  
Head consignado en la descripción del PR: ab0b6405b464baa64b199201fe99d3482d082791  
Base declarada: f3c5004fd2a6aca8d6c0ba967b1b4c6a191158be

Comparación actual main...rama: divergida; 8 commits exclusivos por cada lado respecto del ancestro común. El diff de la rama contiene cuatro archivos nuevos:
- coordination/README.md
- coordination/task-coordination.md
- coordination/task.schema.json
- shared/KAT-006-ETAPA-3-ADAPTACION-2026-11-16.md

La adaptación documenta coordinación centrada en tareas, separación de mandato/owner/autoridad/aceptación, handoffs, estados y criterios. Conserva las tres dimensiones y la pregunta sistémica abierta sobre si la coordinación sistémica queda cubierta por orquestación o requiere capacidad independiente. El informe registra validación Draft 2020-12, fixture válido e inválido; no acredita runtime ni automatización.

**Tratamiento recomendado:** conservar los cuatro artefactos y sus commits; no fusionar todavía. Reconciliar los ocho commits exclusivos de main y los ocho de la rama, revisar conflictos y diferencias semánticas, solicitar contraste de Audeline y mantener la decisión de aceptación pendiente. No borrar la rama ni cerrar el PR mientras la clasificación no esté concluida.

## 4. Conocimiento arquitectónico previo en main

La línea main contiene ocho commits exclusivos respecto de la base declarada por KAT-006. El diff observado agrega:
- registro de reconocimiento RESET-CORE-2026-002;
- investigación KAT-SOFTLY-FUTURE-BLOCKERS-2026-001;
- informe final, investigación preliminar, matriz de riesgos, recomendaciones, registro de evidencia y contraste con Audeline;
- actualización de shared/README.md.

La investigación identifica quince hallazgos KFB-01 a KFB-15. Entre los prioritarios: bloqueo artificial por Runtime, confusión entre persistencia/recepción/activación, falta de verificación transversal de dependencias, responsabilidad ambigua, rutas/permisos y handoffs sin acuse. La coordinación sistémica aparece como pregunta arquitectónica abierta, no como decisión aprobada.

El índice shared/README.md marca el contraste con Audeline como pendiente por falta de evidencia recuperada de AUD-SOFTLY-INTEGRITY-2026-001. Estas investigaciones son conocimiento útil y deben preservarse como documentos históricos y recomendaciones, sin convertir propuestas en mandatos vigentes.

## 5. Inventario de PR relacionados

### TITAN
- PR #1, autonomía y comunicación entre agentes: modifica Titan.ps1 y contratos de PrimusPrivado, Primus, Secundus y Sensori. Capacidad potencialmente útil; requiere revisar permisos, límites de intercambios y pruebas de concurrencia antes de integrar.
- PR #2, deliberación/inferencia: modifica motor PowerShell, grafo de flujo, proveedores, reloj Primus, contratos, pruebas, workflow y registros de agentes. No asumir que todo el contenido es vigente; clasificar código, pruebas y registros por separado.
- PR #3, capacidades ejecutables por dominio: modifica Titan.ps1, src/CapacidadesTitan.ps1, src/RelojPrimus.ps1 y pruebas de contratos. Contiene controles de capacidades y permisos por estación. Preservar y validar, especialmente denegación por defecto y privilegio exclusivo de Princeps.

### Cytryna
- PR #1: corrección de revisión de cambios en archivos de proyecto externos; incluye regresión. Candidato a conservar.
- PR #2: configuración de proveedores/modelos, credenciales y API; antecedentes de configuración dinámica.
- PR #3: GUI inicial Tkinter; cerrada como reemplazada.
- PR #4: GUI Tauri 2 + React; arquitectura posterior reemplazada por decisión documentada en PR #7. Preservar como historia, no asumir vigencia.
- PR #5: integración de escritorio y configuración de modelos basada en Tkinter, declarada como rama de integración histórica.
- PR #6: inventario y orden del trabajo del motor, documentos y logs AGENTDEV.
- PR #7: decisión de coordinación que fija Tkinter/Python como MVP y actualiza ENTREGA_GUI.md, MOTOR.md y PENDIENTES.md. Relevante como decisión técnica.
- PR #8: logs append-only de entrega/decisión.
- PR #9: aclaración de vigencia histórica de GUI.md.
- PR #10: shell inicial Tkinter, documentación y logs AGENTGUI.
- PR #11: fachada segura CytrynaFacade, pruebas de contrato y límites explícitos de ejecución de herramientas.

**Tratamiento recomendado:** preservar decisiones y evidencia de PR #6–#11; revisar la secuencia y relaciones de reemplazo antes de resolver solicitudes. La fachada, pruebas y límites de seguridad son capacidades útiles que no deben perderse. La línea Tauri/React debe quedar histórica salvo evidencia contraria.

### Softly
- PR #4: establece Audelinesay/README.md, entregable/README.md e inbox/README.md. La descripción indica que conserva audsay/res/ y que el canal no activa sesiones ni concede permisos. La rama recovery/AUD-20261116-001 contiene esos tres archivos, con tres commits exclusivos respecto de main y 41 commits de main no contenidos en la rama según comparación. Reconciliar con main y preservar el canal antes de resolver PR.

- Rama fix/f03-recover-ledger: cinco commits exclusivos respecto del ancestro común y 293 commits de main por delante. Cambios observados en SOFTLY.md, registro de recuperación F03, índices de logs, softly-runtime/runtime.py y test_runtime.py. Requiere revisión técnica del cambio runtime y sus pruebas; no se debe integrar ni descartar por nombre de rama.

### Laboratorio-de-agentes
- proposal/auditoria-reforma-normativa-2026-11-15: un commit exclusivo y 170 commits de main por delante respecto del ancestro común. Añade README de propuesta de reforma normativa. Clasificar como propuesta histórica/documental; no conferirle autoridad sobre la orden RESET-CORE-2026-002.

## 6. Matriz preliminar de migración de capacidades

| Capacidad / conocimiento | Origen | Destino propuesto | Tratamiento |
|---|---|---|---|
| Coordinación task-centric y schema | Katarina PR #1 | Katarina | Conservar, reconciliar y auditar antes de integrar |
| Investigación KFB-01..15 y riesgos | Katarina main | Katarina / Softly como insumo | Preservar; contrastar con Audeline |
| Comunicación autónoma y contratos | TITAN PR #1 | Katarina, si sigue dentro del alcance | Extraer capacidad; no conservar identidad de agente |
| Deliberación, inferencia, grafo/proveedores | TITAN PR #2 | Katarina, según utilidad verificada | Revisar pruebas y dependencias |
| Política de capacidades y denegación por defecto | TITAN PR #3 | Katarina | Preservar y validar |
| Configuración de proveedores y credenciales | Cytryna PR #2/#5 | Katarina | Migrar capacidad y contratos, no identidad |
| GUI Tkinter MVP y handoff | Cytryna PR #7/#10 | Katarina | Preservar decisión y activos útiles |
| Fachada segura y pruebas | Cytryna PR #11 | Katarina | Alta prioridad de preservación |
| Revisión de archivos de proyecto externos | Cytryna PR #1 | Katarina | Candidato a integrar tras pruebas |
| Canal Audelinesay | Softly PR #4 | Softly | Conservar canal documental, sin inferir activación/permisos |
| Recuperación ledger/runtime F03 | Softly branch fix/f03-recover-ledger | Softly | Revisión de código y pruebas; no migrar a Katarina sin motivo |
| Propuesta reforma normativa | Laboratorio-de-agentes | Archivo histórico | Preservar como propuesta no normativa |

## 7. Activos a retirar o archivar: criterio, no ejecución

No se identificó evidencia suficiente para retirar físicamente identidades, instalaciones, herramientas, permisos o canales. La acción correcta en esta fase es:
- archivar PR y propuestas reemplazadas como evidencia histórica, una vez verificados sus reemplazos;
- retirar vigencia de mandatos o asignaciones obsoletos mediante registro explícito;
- migrar capacidades útiles sin conservar identidades subordinadas;
- no eliminar ramas ni repositorios hasta completar inventario, respaldos y verificación.

## 8. Riesgos y bloqueos

1. Katarina PR #1 y main están divergidos; integración directa insegura.
2. El diff de KAT-006 se basa en un commit anterior al avance documental de main; se requiere reconciliación de contenido.
3. Softly fix/f03-recover-ledger contiene cambios de runtime y pruebas, con divergencia extensa frente a main.
4. Softly recovery/AUD-20261116-001 contiene el canal Audelinesay que no debe perderse.
5. Cytryna tiene una secuencia histórica compleja de PR y decisiones de GUI que requiere clasificar reemplazos y dependencias.
6. No se verificaron todos los contratos, permisos efectivos, herramientas instaladas, canales completos, identidades referenciadas ni pendientes operativos.
7. El contraste de KFB con Audeline permanece pendiente en el índice consultado.
8. La orden requiere rama única main para repositorios activos; aún no hay evidencia para certificar consolidación en ninguno de los repositorios revisados.

## 9. Acciones siguientes

- Completar inspección de contratos, permisos, herramientas, canales y referencias de identidad en Katarina.
- Reconciliar PR #1 de Katarina con los ocho commits exclusivos de main, sin perder investigación ni adaptación task-centric.
- Solicitar a Audeline contraste independiente del inventario y de KFB.
- Entregar a Softly la matriz de capacidades y bloqueos.
- Continuar con inspección de repositorios y PR restantes; no ejecutar merges, cierres ni borrado de ramas hasta clasificar sus diffs y preservar evidencia.

## 10. Declaración de integridad del informe

Este documento registra lo efectivamente observado y separa recomendaciones de acciones ejecutadas. No certifica inventario global, auditoría, activación de sesiones ni consolidación. Ninguna rama adicional fue eliminada y ningún PR fue fusionado o cerrado durante este reconocimiento.
