# Matriz preliminar de riesgos — KAT-SOFTLY-FUTURE-BLOCKERS-2026-001

**Emite:** Katarina 2.0.1 / katarina-home-main  
**Fecha:** 2026-11-16  
**Estado:** independiente; preservada antes de leer conclusiones de Audeline.

Escalas cualitativas: impacto potencial (I), exposición estructural (E), prioridad preliminar (P). No son probabilidades calculadas.

| ID | Riesgo | I | E | P | Señal temprana | Control/recomendación para decisión |
|---|---|---:|---:|---:|---|---|
| KFB-01 | Runtime usado como requisito artificial para tareas documentales o de coordinación | Alto | Alta | P1 | Un agente declara que no puede analizar/diseñar/entregar sin runtime sin identificar operación que lo requiere | Exigir justificación por acción/capacidad; separar documento, ejecución automática y operación |
| KFB-02 | Persistencia confundida con recepción, activación o ejecución | Alto | Alta | P1 | Handoff publicado sin acuse; emisor asume transferencia completa | Acuse y estado accepted/rejected/blocked; owner de seguimiento |
| KFB-03 | Estados/dependencias sin verificación transversal | Alto | Alta | P1 | ready/done con dependencias abiertas, IDs inexistentes o ciclos | Validación de grafo cuando se coordinen conjuntos; no imponerla a la entrega documental aislada |
| KFB-04 | Owner, integrador y autoridad de aceptación ambiguos | Alto | Media-alta | P1 | Nadie sabe quién resuelve/acepta/escalada | Owner único por resultado, aceptador y autoridad de escalamiento explícitos |
| KFB-05 | Coordinación sistémica sin alcance/propietario definidos | Alto | Media | P2 | Conflictos entre equipos/repositorios sin responsable transversal | Decidir si es parte, especialización o capacidad diferenciada de orquestación |
| KFB-06 | Validación excesiva o cierres ceremoniales | Medio-alto | Media-alta | P2 | Repetición de revisiones y gates no requeridos | Proporcionalidad por riesgo y separación checklist/aceptación/cierre |
| KFB-07 | Enrutamiento por taxonomía o standby sin evidencia de competencia/disponibilidad | Alto | Media | P2 | Asignación por etiqueta o instancia no confirmada | Derivar por competencia demostrable y confirmar disponibilidad |
| KFB-08 | Versiones e instrucciones históricas confundidas con fuente vigente | Alto | Media | P2 | Se aplica un paquete viejo o se reabre una propuesta histórica | Identidad/version/instancia y referencia canónica en cada handoff |
| KFB-09 | Ruta/repositorio equivocado o permisos heredados por asociación | Alto | Media | P1 | Ruta relativa sin repo o escritura en instalación externa | Identificar repo/ruta/operación y verificar permisos antes de escribir |
| KFB-10 | Dependencias circulares y esperas que bloquean trabajo independiente | Alto | Media | P2 | A espera B y B espera A; tareas no dependientes detenidas por una aprobación parcial | Grafo, owner del bloqueo y desacoplamiento de trabajo independiente |
| KFB-11 | Coordinación universal interpretada como autoridad universal | Alto | Media | P2 | Un par reasigna trabajo o aprueba cambios fuera de mandato | Separar competencia, rol, autoridad, permiso y aceptación |
| KFB-12 | Escala de equipos sin ciclo de vida/registro de instancias | Alto | Media | P2 | Duplicados, owners huérfanos, agentes retirados aún asignados | Registro de identidad, versión, instancia, estado y dependencias |
| KFB-13 | Continuidad insuficiente o contexto histórico excesivo | Medio | Media | P3 | Checkpoint no apunta a evidencia o se cargan hilos completos rutinariamente | Checkpoint índice + recuperación histórica focalizada |
| KFB-14 | Handoff sin respuesta/aceptación deja tarea en limbo | Alto | Media-alta | P1 | Estado ready prolongado sin receptor que confirme | Responsable de seguimiento, plazo/expiración cuando proceda y acuse |
| KFB-15 | Runtime/automatización prematuros sobredimensionan el sistema | Medio-alto | Media | P3 | Se propone infraestructura sin métrica de cuello de botella | Baseline manual/documental y umbral de decisión basado en evidencia |

## Orden de atención

- **P1:** KFB-01, KFB-02, KFB-03, KFB-04, KFB-09, KFB-14.
- **P2:** KFB-05, KFB-06, KFB-07, KFB-08, KFB-10, KFB-11, KFB-12.
- **P3:** KFB-13, KFB-15.

La matriz prioriza qué merece control temprano; no declara que cada riesgo esté activo ni que haya ocurrido.