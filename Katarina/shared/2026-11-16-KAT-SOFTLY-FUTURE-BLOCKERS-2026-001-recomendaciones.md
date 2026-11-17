# Recomendaciones priorizadas — KAT-SOFTLY-FUTURE-BLOCKERS-2026-001

**Emite:** Katarina 2.0.1 / katarina-home-main  
**Fecha:** 2026-11-16  
**Estado:** propuestas para decisión de gAto; ninguna implementada ni aprobada por este informe.

## P0 — Corregir inmediatamente la interpretación operativa

### R-01. Regla explícita de no bloqueo por Runtime
Para cada encargo, identificar primero el resultado y la operación concreta. Runtime solo puede ser dependencia si la acción pedida exige ejecución, automatización, integración o enforcement que no puede realizarse documentalmente. Nunca bloquear análisis, diseño, deliberación, especificación, coordinación documental o preparación de entregables por ausencia de Runtime.

**Razón:** contradicción directa con SOFTLY.md y checklist documental. El incidente de coordinación visible en el hilo actual demuestra que la regla escrita puede no bastar para prevenir una interpretación equivocada.

### R-02. Protocolo mínimo de handoff con acuse y owner
Un handoff debe tener emisor, receptor, tarea, resultado, evidencia, siguiente acción y criterio de aceptación; además, el receptor debe dejar estado accepted/rejected/blocked. Si no hay acuse, la transferencia sigue pendiente y el emisor/orquestador conserva la responsabilidad de seguimiento.

**Razón:** publicación en GitHub no equivale a recepción ni activación.

### R-03. Owner y autoridad de aceptación explícitos
Toda tarea con más de un participante debe distinguir owner del resultado, integrador, aceptador y autoridad de escalamiento. No usar "equipo" como propietario ambiguo cuando una persona/agente concreto debe responder por la entrega.

**Razón:** evita tareas huérfanas y aprobación circular.

## P1 — Antes de ampliar el número de equipos

### R-04. Verificación de conjunto para dependencias
Cuando se use un tablero de varias tareas, comprobar IDs referenciados, ciclos, dependencias obligatorias y coherencia de estados. No exigir esta comprobación para crear un paquete documental aislado.

### R-05. Preflight de identidad/ruta/versión
Antes de escribir o asignar, fijar repositorio, rama/commit, ruta, identidad, versión, instancia y permiso efectivo. Los repositorios externos no heredan la casa ni los permisos de un agente.

### R-06. Resolver la responsabilidad de coordinación sistémica
gAto debe decidir si la coordinación sistémica es parte de la orquestación, una especialización transversal o una capacidad diferenciada. La decisión debe definir propietario, alcance y señales de activación, sin crear una cuarta dimensión por inercia.

### R-07. Registro de ciclo de vida de agentes
Distinguir al menos diseñado, disponible para asignación, asignado, activado, suspendido y retirado. Cada transición debe tener responsable y evidencia. Active-standby no debe usarse como sinónimo de sesión viva.

### R-08. Control de vigencia documental
En handoffs y decisiones, identificar versión/instancia y enlazar la fuente canónica vigente. Marcar antecedentes históricos, propuestas y decisiones reemplazadas sin borrarlos.

## P2 — Eficiencia y resiliencia

### R-09. Proporcionalidad de validaciones
Separar checklist de producción, verificación técnica, aceptación humana y cierre de hilo. Aplicar la profundidad adecuada al riesgo y a la etapa; no convertir cada tarea en un protocolo exhaustivo ni eliminar verificaciones necesarias para declaraciones de cierre.

### R-10. Continuidad mediante checkpoint como índice
El checkpoint debe responder qué está vigente, qué está pendiente, quién lo posee y dónde está la evidencia. Consultar los hilos históricos solo cuando sean relevantes; no copiar la historia completa en cada sesión.

### R-11. Decidir infraestructura por evidencia
Antes de construir Runtime, A2A, MCP, bus de eventos o workflow engine, medir fallos de recepción, latencia, trabajo duplicado, costo de coordinación, errores de permisos y recuperación. Si el proceso documental/manual no es el cuello de botella, no añadir infraestructura.

## Decisiones reservadas a gAto

1. Aprobar o rechazar cada recomendación y su prioridad.
2. Definir el alcance de coordinación sistémica.
3. Autorizar un piloto de verificación de dependencias y handoffs.
4. Autorizar cambios normativos, de schemas, moldes, contratos o directorios.
5. Decidir cuándo los datos operativos justifican infraestructura.

**Límite:** Katarina propone; no implementa ni modifica mandatos en virtud de este informe.