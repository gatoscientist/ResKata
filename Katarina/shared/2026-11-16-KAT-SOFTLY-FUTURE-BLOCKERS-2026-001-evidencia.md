# Registro de evidencia — KAT-SOFTLY-FUTURE-BLOCKERS-2026-001

**Emite:** Katarina 2.0.1 / katarina-home-main  
**Fecha:** 2026-11-16  
**Corte:** evaluación preliminar independiente, preservada antes de leer conclusiones de Audeline.

| ID | Fuente exacta | Evidencia observada | Hallazgos relacionados | Fuerza |
|---|---|---|---|---|
| EV-01 | Softly/SOFTLY.md, §1–4 | Prompting + Contratos + GitHub; no postergar entrega documental por Runtime; checklist no es gate burocrático | KFB-01, KFB-06, KFB-15 | Directa normativa |
| EV-02 | Softly/docs/architecture/taxonomy-and-mold-validation.md, §§2–4 | No-herencia; derivación por dominio/competencia/evidencia; generador declarativo sin CLI/motor externo; no bloquear por runtime | KFB-01, KFB-07 | Directa normativa |
| EV-03 | Softly/agents/templates/agent-generation-mold.md, §§1–8 | No exigir datos no esenciales; separar herramientas requeridas/disponibles/conectadas y permisos declarados/efectivos; entregar 1.0.0 Diseñado | KFB-01, KFB-07, KFB-08 | Directa normativa |
| EV-04 | Softly/docs/agent-delivery-checklist.md | Auto-revisión durante producción; runtime, integración, despliegue y métricas no solicitadas no bloquean entrega | KFB-01, KFB-06 | Directa normativa |
| EV-05 | Softly/docs/architecture/operational-modes-and-autocoordination.md, §§1–7 | Modo según encargo; active-standby no implica ejecución; handoff publicado no activa sesión; inicio ligero | KFB-02, KFB-06, KFB-12, KFB-13, KFB-14 | Directa normativa |
| EV-06 | Softly/agents/templates/handoff.md | Handoff con FROM/TO/TASK/RESULT/EVIDENCE/OPEN/NEXT/ACCEPT; respuesta accepted/rejected/blocked; evento repetido no debe ejecutar dos veces | KFB-02, KFB-14 | Directa normativa |
| EV-07 | Softly/docs/architecture/task-centric-coordination.md, §§1–8 | Tarea primaria; reglas ready/done/blocked; schema no valida referencias ni ciclos; handoff no demuestra aceptación; coordinación sistémica abierta | KFB-02, KFB-03, KFB-04, KFB-05, KFB-10, KFB-11 | Directa normativa |
| EV-08 | Softly/schemas/task.schema.json | Campos obligatorios y referencias depends_on como strings; no contiene validación de grafo transversal | KFB-03, KFB-10 | Directa estructural |
| EV-09 | Softly/Katarinasay/reports/KAT-006-ETAPA-1-IMPLEMENTACION-2026-11-16.md, §§6–7 | Parseo JSON y comprobaciones declaradas; no se ejecutó validador JSON Schema completo ni tests DAG/ciclos/referencias huérfanas | KFB-03, KFB-10 | Directa, reporte de ejecución |
| EV-10 | Softly/research/coordination/2026-11-16-decision-direccion-task-centric-tres-dimensiones.md | Dirección task-centric y preferencia de tres dimensiones; pregunta sistémica explícitamente abierta; sin piloto ni cambios normativos autorizados | KFB-05, KFB-11 | Directa, decisión |
| EV-11 | Softly/logs/2026-11-16-cierre-administrativo-kat-006-reinicio-integral.md | KAT-006 cerrado administrativamente, no aceptado técnicamente; evidencia y handoffs preservados; inventario requerido antes de retiro | KFB-08, KFB-09, KFB-12 | Directa, registro histórico |
| EV-12 | Katarina/core/INSTANCE.md y core/CONTRACT.md | Casa canónica separada del Laboratorio; identidad, estado documental y límites de ejecución explícitos | KFB-08, KFB-09 | Directa normativa |
| EV-13 | Softly/CHECKPOINT.md | Estado diseñado distinto de activación; continuidad, dependencias y decisiones pendientes registradas; etapas de KAT-006 diferenciadas | KFB-02, KFB-08, KFB-12, KFB-13 | Directa, checkpoint |
| EV-14 | Softly/docs/architecture/coordination-patterns.md | Baseline single-agent/tools y workflow; criterios de éxito, coste, latencia, trazabilidad, permisos y mantenimiento | KFB-06, KFB-15 | Directa, guía comparativa |
| EV-15 | Softly/README.md | Inicio ligero y modos; entrega documental 1.0.0/Diseñado separada de runtime, integración y despliegue | KFB-01, KFB-06, KFB-13 | Directa normativa |

## Notas de evidencia

1. Los documentos prueban qué reglas y límites están declarados; no prueban que todos los agentes los interpreten o cumplan en cada sesión.
2. Un informe que declara pruebas no equivale a repetirlas en esta investigación. Para KAT-006 se registra exactamente la limitación descrita en su propio informe.
3. La ausencia de una validación automática en el schema no es por sí sola un defecto si la etapa es documental; sí se convierte en riesgo cuando el estado de tareas se usa para coordinar conjuntos grandes sin verificación externa.
4. No se atribuyen frecuencias, probabilidades estadísticas ni incidentes no demostrados.
5. El registro se mantendrá como evidencia de procedencia; discrepancias posteriores se añadirán, no se reescribirá la línea base.