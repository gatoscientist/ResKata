# KAT-SOFTLY-FUTURE-BLOCKERS-2026-001 — Investigación preliminar independiente

**Emite:** Katarina  
**ID / versión / estado:** katarina / 2.0.1 / Agent Softly, Diseñado  
**Instancia:** katarina-home-main  
**Fecha:** 2026-11-16  
**Repositorio de investigación:** gatoscientist/Katarina, `shared/`  
**Estado:** PRELIMINAR PRESERVADO ANTES DE LEER CONCLUSIONES DE AUDeline  
**Mandato:** gAto; investigación arquitectónica independiente.  
**Alcance:** anticipar trabas futuras; no auditoría general de integridad, no implementación.

## 1. Resumen

La evidencia documental muestra que Softly ya dispone de reglas que previenen varias trabas: independencia de Runtime para entregas documentales, separación de modos, no-herencia de competencias/permisos, distinción entre handoff publicado y sesión activada, y coordinación task-centric. El riesgo futuro principal no es la ausencia absoluta de reglas, sino la brecha entre reglas documentales, interpretación consistente y mecanismos de operación verificables.

No se afirma que todos los riesgos descritos ya hayan ocurrido. Cada hallazgo se clasifica como hecho documental, incidente/evidencia histórica o riesgo prospectivo.

## 2. Hallazgos preliminares

### KFB-01 — Dependencia artificial de Runtime
**Clase:** contradicción operativa posible; riesgo alto.  
**Evidencia:** SOFTLY.md declara Prompting + Contratos + GitHub como sustrato suficiente y prohíbe retener entregas documentales esperando Runtime. El molde, la checklist y la validación de taxonomías repiten que la entrega documental no requiere runtime, CLI ni motor externo.  
**Riesgo futuro:** un agente puede convertir una limitación de ejecución automática en bloqueo de análisis, diseño, documentación, asignación o preparación de entregables.  
**Condición de materialización:** instrucciones locales o interpretación del agente que exijan runtime sin vincularlo a una operación que realmente lo necesite.  
**Control documental existente:** separar capacidad requerida por tarea de infraestructura opcional; identificar explícitamente qué acción concreta no puede ejecutarse.  
**Estado:** regla preventiva explícita; no demuestra que el ecosistema esté libre de futuras interpretaciones erróneas.

### KFB-02 — Confusión entre persistencia, recepción, activación y ejecución
**Clase:** riesgo de coordinación; alto.  
**Evidencia:** SOFTLY.md y operational-modes-and-autocoordination.md dicen que publicar un handoff no activa una sesión. El modelo task-centric distingue tarea, mensaje, evento, artifact y workspace.  
**Riesgo futuro:** tratar un archivo depositado como recibido, aceptado, asignado, iniciado o completado; generar esperas silenciosas o duplicación de trabajo.  
**Condición:** ausencia de confirmación de recepción/aceptación, propietario o siguiente acción visible.  
**Control existente:** estados accepted/rejected/blocked en handoff y estados explícitos de tarea; requieren disciplina y verificación del conjunto, no se ejecutan automáticamente.

### KFB-03 — Estados y dependencias declarativos sin verificación de conjunto
**Clase:** brecha entre contrato y ejecución; alto.  
**Evidencia:** task-centric-coordination.md reconoce que el schema no comprueba existencia de IDs, ciclos ni cierre de dependencias; el informe KAT-006 etapa 1 deja pendientes pruebas DAG, referencias huérfanas y validador completo.  
**Riesgo futuro:** tareas marcadas ready/done con dependencias incumplidas, ciclos, IDs inexistentes o aceptación no demostrada.  
**Condición:** crecimiento del número de tareas o uso concurrente sin una revisión de grafo y evidencia.  
**Control existente:** reglas semánticas en el documento; la comprobación de conjunto está expresamente pendiente.

### KFB-04 — Responsabilidad difusa entre owner, orquestador y autoridad humana
**Clase:** riesgo de gobernanza; alto.  
**Evidencia:** el modelo task-centric asigna owner a cada tarea, reserva a orquestación la integración y escalamiento, y conserva a gAto las decisiones reservadas.  
**Riesgo futuro:** varios participantes creen que otro acepta el resultado, resuelve el bloqueo o decide cambios de alcance; o el orquestador asume autoridad no concedida.  
**Condición:** tareas con múltiples entregables, aceptación externa o dependencia de decisiones humanas sin responsable explícito.  
**Control:** owner único por resultado, autoridad de aceptación y escalamiento identificados por tarea.

### KFB-05 — Coordinación sistémica insuficientemente delimitada
**Clase:** pregunta arquitectónica abierta; medio-alto.  
**Evidencia:** la decisión de dirección task-centric conserva expresamente abierta la relación entre orquestación y coordinación sistémica, con tres interpretaciones posibles.  
**Riesgo futuro:** nadie asume observación transversal de cuellos de botella, conflictos entre equipos, dependencias globales o consistencia entre repositorios; alternativamente, el orquestador se sobrecarga con una responsabilidad no acotada.  
**Condición:** crecimiento multi-equipo o decisiones que cruzan repositorios y dominios.  
**Estado:** no resuelto por decisión de gAto; no debe cerrarse por inferencia.

### KFB-06 — Sobrecarga de validación y cierre ceremonial
**Clase:** riesgo de productividad; medio-alto.  
**Evidencia:** SOFTLY.md y checklist definen auto-revisión integrada, no una aprobación burocrática. A la vez, «Cierra el Hilo» exige persistencia, dos revisiones y validaciones requeridas antes del cierre.  
**Riesgo futuro:** aplicar protocolos de cierre exhaustivos a cada microtarea, duplicar revisiones, exigir validaciones fuera del alcance o confundir checklist de calidad con gate de autorización.  
**Condición:** instrucciones locales que omitan proporcionalidad, o falta de distinción entre cierre de hilo, entrega y aceptación.  
**Control:** usar revisión proporcional al riesgo y al objeto; no relajar la exigencia de evidencia para declaraciones de cierre.

### KFB-07 — Competencias y disponibilidad sobredeclaradas o mal interpretadas
**Clase:** riesgo de enrutamiento; medio-alto.  
**Evidencia:** taxonomía separa categoría, dominio, especialidad, competencia, disponibilidad y evidencia; no-herencia por defecto. El registro incluye competencias vacías y evidencia declarativa de procedencia.  
**Riesgo futuro:** asignar por etiqueta profesional, familiaridad histórica o estado active-standby sin verificar competencia pertinente y disponibilidad efectiva.  
**Condición:** catálogo grande, perfiles desactualizados o asignaciones urgentes.  
**Control:** derivación con competencia requerida, evidencia, motivo y límites; confirmar disponibilidad antes de tratarla como sesión activa.

### KFB-08 — Deriva de versiones y fuentes normativas
**Clase:** riesgo de evolución; medio-alto.  
**Evidencia:** coexistencia de Katarina 2.0.1 con referencias históricas a agentdev-katarina 1.1.0, y documentación de decisiones que preserva propuestas y estados anteriores. Los documentos exigen mantener genealogía y no confundir versiones.  
**Riesgo futuro:** una sesión aplica contrato antiguo, copia instrucciones de un agente retirado o interpreta una propuesta histórica como decisión vigente.  
**Condición:** múltiples repositorios, ramas, paquetes instalados y documentos que se enlazan entre sí.  
**Control:** identidad/version/instancia, fuente canónica y fecha/estado de vigencia en cada handoff; preservar historia sin tratarla como instrucción actual.

### KFB-09 — Ambigüedad de rutas y propiedad de repositorios
**Clase:** riesgo operativo; alto.  
**Evidencia:** Katarina 2.0.1 dedica reglas específicas a distinguir su casa canónica del Laboratorio externo; el registro de cierre KAT-006 describe un reinicio integral y exige inventario antes de retirar instancias.  
**Riesgo futuro:** leer o escribir en repositorio equivocado, asumir que un equipo externo comparte la casa/permisos del agente, o perder trazabilidad durante reconstrucciones.  
**Condición:** nombres similares, rutas relativas sin repositorio, instalaciones externas y migraciones.  
**Control:** repositorio + ruta + operación explícitos antes de cada escritura; inventario canónico de agentes/versiones/instancias/dependencias antes de retiro.

### KFB-10 — Dependencias circulares y colas de espera humanas
**Clase:** riesgo de flujo; medio-alto.  
**Evidencia:** task-centric declara que los ciclos de dependencias no son detectados por el schema; CHECKPOINT mantiene decisiones que requieren confirmación posterior de gAto.  
**Riesgo futuro:** A espera a B, B espera a A; o varios agentes detienen trabajo documental no dependiente mientras esperan una aprobación que solo afecta una decisión separable.  
**Condición:** dependencias sin dirección, bloqueos sin owner de resolución o tareas agrupadas con aprobaciones de alcance distinto.  
**Control:** grafo acíclico revisado, bloqueos específicos, trabajo independiente desacoplado y aprobación humana limitada a la decisión reservada.

### KFB-11 — Capacidad universal de coordinación confundida con autoridad universal
**Clase:** riesgo de gobernanza; medio.  
**Evidencia:** decisión de dirección reconoce coordinación propia, entre pares y orquestación; task-centric prohíbe que la coordinación conceda permisos o jerarquía.  
**Riesgo futuro:** interpretar que todos pueden coordinar como autorización para asignar trabajo ajeno, cambiar prioridades, aceptar entregables de terceros o reasignar recursos.  
**Control:** competencia transversal separada de rol, mandato, permisos y autoridad de aceptación.

### KFB-12 — Crecimiento de equipo sin administración de ciclo de vida
**Clase:** riesgo de escala; medio-alto.  
**Evidencia:** checkpoint registra equipos en estado documental y exige inventario, respaldo e identidad/version/instancia antes de retiro/reconstrucción; active-standby no equivale a ejecución.  
**Riesgo futuro:** duplicación de agentes, paquetes obsoletos, responsables huérfanos, permisos residuales o asignaciones a instancias inexistentes.  
**Control:** registro de ciclo de vida que distinga diseñado, disponible, asignado, activado, suspendido y retirado, con owner y evidencia por transición.

### KFB-13 — Continuidad excesiva o insuficiente
**Clase:** riesgo de contexto; medio.  
**Evidencia:** inicio ligero exige SOFTLY.md y CHECKPOINT.md y consulta histórica bajo demanda; los protocolos de cierre e incidencia piden preservar trazabilidad observable.  
**Riesgo futuro:** contexto insuficiente si el checkpoint no apunta a la evidencia necesaria; o sobrecarga si cada sesión carga hilos y logs históricos completos.  
**Control:** checkpoint como índice de estado, referencias estables a artefactos, y consulta histórica focalizada por pregunta.

### KFB-14 — Handoffs que no se completan por falta de respuesta o criterio de aceptación
**Clase:** riesgo de transferencia; alto.  
**Evidencia:** plantilla de handoff define estados accepted/rejected/blocked y campos NEXT/ACCEPT; modelo operativo advierte que publicación no despierta sesión.  
**Riesgo futuro:** handoff permanece ready indefinidamente, receptor no confirma, emisor cree haber transferido responsabilidad y la tarea queda sin owner operativo.  
**Control:** plazo/condición de expiración cuando aplique, responsable de seguimiento, acuse de recibo y aceptación/rechazo/bloqueo explícitos.

### KFB-15 — Automatización prematura o arquitectura sobredimensionada
**Clase:** riesgo estratégico; medio.  
**Evidencia:** documentos de coordinación comparan baseline de agente único/workflow con equipos y runtime; la investigación interna recomienda no construir bus/runtime antes de demostrar cuello de botella.  
**Riesgo futuro:** invertir en Runtime, A2A, MCP, event sourcing o bus de mensajes antes de demostrar que el proceso documental es insuficiente; añadir nuevos puntos de fallo y dependencia operativa.  
**Control:** decisión de infraestructura basada en métricas de fallos, costo, latencia, recuperación y permisos; mantener alternativa manual/documental funcional.

## 3. Priorización preliminar

**Prioridad inmediata:** KFB-01, KFB-02, KFB-03, KFB-04, KFB-09 y KFB-14.  
**Prioridad de diseño antes de escalar equipos:** KFB-05, KFB-07, KFB-08, KFB-10 y KFB-12.  
**Vigilancia de eficiencia y complejidad:** KFB-06, KFB-11, KFB-13 y KFB-15.

La prioridad expresa impacto potencial y exposición estructural, no probabilidad estadística medida.

## 4. Límites y asuntos pendientes

- Esta es una evaluación documental independiente; no prueba la frecuencia de los riesgos en operación.
- No se inspeccionó la configuración privada de agentes ni se presume su ejecución.
- No se ha leído ningún informe ni conclusión de Audeline antes de preservar este documento.
- El contraste con Audeline queda pendiente de verificar su misión, entregables completos, commits y relectura desde el repositorio indicado por gAto.
- No se modifica ningún mandato, contrato, schema, taxonomía ni repositorio de Softly.

## 5. Fuentes internas principales

- `gatoscientist/Softly/SOFTLY.md`
- `gatoscientist/Softly/CHECKPOINT.md`
- `gatoscientist/Softly/docs/architecture/operational-modes-and-autocoordination.md`
- `gatoscientist/Softly/docs/architecture/task-centric-coordination.md`
- `gatoscientist/Softly/docs/operating-model.md`
- `gatoscientist/Softly/agents/templates/agent-generation-mold.md`
- `gatoscientist/Softly/agents/templates/handoff.md`
- `gatoscientist/Softly/docs/agent-delivery-checklist.md`
- `gatoscientist/Softly/docs/architecture/taxonomy-and-mold-validation.md`
- `gatoscientist/Softly/schemas/agent-taxonomy-registry.json`
- `gatoscientist/Softly/schemas/task.schema.json`
- `gatoscientist/Softly/Katarinasay/reports/KAT-006-ETAPA-1-IMPLEMENTACION-2026-11-16.md`
- `gatoscientist/Softly/logs/2026-11-16-cierre-administrativo-kat-006-reinicio-integral.md`
- `gatoscientist/Softly/research/coordination/2026-11-16-decision-direccion-task-centric-tres-dimensiones.md`

**Preservación:** estos hallazgos son la línea base independiente. No deben reescribirse para ajustarlos a la auditoría posterior.