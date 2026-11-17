# Investigación independiente de Katarina y comparación final con Softly
**Fecha:** 2026-11-16  
**Agente:** Katarina · `katarina` · versión normativa vigente 2.0.1  
**Dirección humana:** gAto  
**Modalidad:** investigación, auditoría documental y síntesis comparativa  
**Estado:** entregado y archivado; propuestas no implementadas ni aprobadas  
**Alcance:** seis repositorios autorizados: `gatoscientist/Katarina`, `Cytryna`, `TITAN`, `Auditoria`, `Softly` y `Laboratorio-de-agentes`.

---

## 1. Dictamen ejecutivo

La investigación independiente de Katarina y la investigación independiente de Softly convergen en una recomendación: **avanzar hacia una coordinación centrada en tareas y dependencias (Alternativa B), mediante un piloto medido, sin reescribir ahora los contratos ni desplegar un runtime multiagente**.

La convergencia no elimina diferencias conceptuales ni constituye aprobación humana. Los dos informes fueron elaborados de manera independiente. La propuesta queda sometida a la decisión de gAto.

El problema principal no es la cantidad de carpetas. Es la falta de semántica compartida y verificable para las entidades que las carpetas intentan representar: mensajes, tareas, eventos, entregables, espacios de trabajo, decisiones y responsabilidades. En distintos repositorios, las mismas rutas representan funciones diferentes; y varias funciones se duplican en artefactos sin ciclo de vida común.

La recomendación integrada es:
1. Tomar la **tarea** como unidad principal de responsabilidad y seguimiento.
2. Vincular mensajes, eventos y entregables a esa tarea, sin duplicar el contenido.
3. Mantener espacios compartidos solo cuando exista una necesidad real de colaboración sobre recursos comunes.
4. Derivar vistas de recepción y envío desde asignaciones y autoría, en vez de mantener copias físicas obligatorias.
5. Enseñar a todos los agentes a coordinar su propio trabajo y colaborar entre pares; reservar la orquestación/directiva a roles con autoridad.
6. Mantener la coordinación documental en GitHub mientras no se demuestre que la activación manual, la recepción o la recuperación son un cuello de botella que justifique runtime.
7. Ejecutar un piloto comparativo antes de cambiar moldes, schemas, contratos o estructuras productivas.

## 2. Preguntas investigadas

- ¿Qué significa coordinar y qué diferencia existe entre coordinar y coordinarse?
- ¿Qué competencias colaborativas deberían ser universales y cuáles dependen del rol?
- ¿Qué funciones reales cumplen `say/`, `shared/`, `inbox/`, `outbox/`, `deliveries/`, bitácoras y handoffs?
- ¿Qué inconsistencias y duplicaciones aparecen al comparar los seis repositorios?
- ¿Qué arquitectura permitiría colaboración verificable sin imponer complejidad innecesaria?
- ¿Qué formación mínima necesitan los agentes y cómo evaluar su eficacia?
- ¿Qué mecanismos de concurrencia, recepción, aceptación y continuidad faltan?
- ¿Qué conviene conservar, simplificar o postergar?

## 3. Método, fuentes y límites

Katarina inspeccionó los árboles y documentos relevantes de los seis repositorios autorizados, contrastando mandatos, contratos, procedimientos, estructuras, schemas, ejemplos y código disponible. La revisión fue documental y selectiva, no una lectura íntegra de todos los archivos. Se consultaron además fuentes públicas académicas y técnicas sobre coordinación, equipos de agentes, handoffs, workflows, A2A, MCP y persistencia.

La investigación de Softly declara un inventario recursivo de 1.096 archivos y lectura selectiva de documentos centrales. Softly señala expresamente que no leyó íntegramente los 1.096 archivos. No ejecutó sesiones runtime ni pruebas comparativas.

**Límites comunes:**
- No se ejecutaron pruebas de runtime ni experimentos controlados.
- No se midieron tokens, latencia, costos, duplicación real, tasas de recepción o aceptación en el ecosistema.
- Los documentos prueban qué está escrito y versionado, no que todos los flujos descritos se hayan ejecutado correctamente.
- No se fijaron pinned SHAs para cada observación de la investigación de Katarina; los repositorios pueden cambiar.
- Los resultados de benchmarks y preprints externos son contextuales, no leyes universales.
- No se modificaron contratos, schemas, taxonomías ni runtime durante la investigación.
- Este informe no certifica implementación, despliegue ni validación experimental.

## 4. Marco conceptual: coordinar y coordinarse

Coordinar consiste en gestionar dependencias entre actividades: precedencia, interfaces, recursos compartidos, intercambio de información, autoridad, integración y aceptación. No toda interacción necesita coordinación explícita; si las tareas son independientes y no comparten recursos ni resultados intermedios, agregar mensajes puede aumentar el costo sin aportar valor.

Se distinguen dos competencias esenciales:

**Coordinarse (competencia universal):** comprender misión, autoridad, alcance y restricciones; planificar el trabajo propio; reconocer dependencias; informar estado y bloqueos; solicitar o confirmar colaboración; respetar propiedad y permisos; entregar resultados con evidencia, limitaciones y siguiente acción.

**Coordinar (competencia de rol):** descomponer objetivos, asignar responsables, ordenar dependencias, administrar recursos y estados, integrar entregas, resolver conflictos, aceptar resultados y escalar decisiones. Esta competencia directiva requiere autoridad explícita; no se hereda por el solo hecho de ser agente.

### 4.1 Modelo integrado de competencias

La investigación de Katarina propuso cuatro dimensiones:
1. Autocoordinación.
2. Coordinación colaborativa entre pares.
3. Coordinación directiva.
4. Coordinación sistémica.

Softly propone tres niveles:
1. Coordinación propia.
2. Coordinación entre pares.
3. Orquestación.

La síntesis conserva cuatro dimensiones funcionales, pero reconoce que las dos primeras son la base universal y las dos últimas dependen del rol:
- **Autocoordinación:** universal.
- **Colaboración entre pares:** universal cuando existe trabajo compartido.
- **Coordinación directiva/orquestación:** según rol y autoridad.
- **Coordinación sistémica:** responsabilidad especializada para gobernar interfaces, reglas, recursos y coherencia entre equipos o dominios.

Queda abierta la decisión de si coordinación sistémica merece una categoría autónoma en el molde universal o debe describirse como especialización de orquestación.

### 4.2 Diez reglas universales de conducta

1. Comprender objetivo, autoridad, alcance, restricciones y criterio de aceptación.
2. Identificar al responsable de la tarea y a los dueños de sus dependencias.
3. Revisar el trabajo previo antes de duplicarlo.
4. Reconocer dependencias, interfaces y recursos compartidos.
5. Comunicar cambios relevantes de estado; no generar reportes vacíos.
6. Informar bloqueos con causa, impacto y condición de desbloqueo.
7. No duplicar trabajo ni reclamar tareas ya asumidas sin resolver la concurrencia.
8. Entregar resultado, evidencia, límites y siguiente acción verificable.
9. No interpretar silencio, publicación o lectura como aceptación.
10. Cerrar solo cuando se cumplan criterios; distinguir cierre administrativo de éxito.

## 5. Hallazgos comparados en los seis repositorios

### 5.1 Katarina
La casa canónica y los materiales del Laboratorio no siempre comparten la misma estructura. La casa canónica contiene `Softlysay/`, `shared/` y espacios propios; una copia de instancia del Laboratorio conserva una estructura más extensa con inbox, borradores y outbox. Se observó divergencia de versión documental entre copias. La topología requiere conocer demasiadas rutas y distinguir la casa canónica del proyecto externo.

### 5.2 Cytryna
Cytryna combina agentes independientes, `devteam/`, logs JSONL, políticas de escritura y un coordinador de proveedores/modelo/contexto/tools. El `AgentCoordinator` organiza recursos dentro de una instancia; no es por sí mismo un coordinador multiagente. Se detectó una contradicción documental sobre el estado de la GUI: `devteam/GUI.md` indica que no hay GUI integrada en el código actual de `main`, mientras otros documentos describen pasos para iniciarla. El propio documento GUI contiene formulaciones contradictorias. El estado real requiere comprobación técnica específica antes de afirmarlo.

### 5.3 TITAN
Existen dos estructuras de equipos. La Dirección de Recuperación Cytryna usa `shared/inbox/`, `deliveries/`, `decisions/`, `bitacoras/` y canales documentales. La Constitución aclara que los canales no implican mensajes enviados, sesiones activas ni invocación automática. La Dirección TITAN / Los Mancos define roles y límites claros. Parte del README describe rutas que no coinciden con el árbol actual, por lo que hay referencias documentales obsoletas.

### 5.4 Auditoría
Dispone de coordinación, protocolo de trabajo, política de hilos y tablero de tareas. Destaca por single-pass, límite de retest, severidades, evidencia, independencia de auditoría y aceptación. Una propuesta técnica documenta duplicaciones de estructuras, pero es una propuesta, no implementación. Su disciplina evita ciclos de revisión interminables.

### 5.5 Softly
Su modelo documental separa definición, brief, asignación y sesión. El schema de handoff exige identificadores, estado, emisor/destinatario, asignación, tarea, resultado, evidencia, siguiente paso, aceptación y fecha; lease es opcional. El schema establece que un handoff no ejecuta ni autoriza herramientas. El modelo de agente es una propuesta documental, no runtime. Sus fortalezas son la separación de identidad, autoridad, permisos, madurez y sesión, y la independencia de auditoría. Riesgo: acumular componentes documentales para operaciones sencillas.

### 5.6 Laboratorio de agentes
Contiene paquetes, instancias y material histórico. Una copia de Katarina 2.0.0 convive con una casa canónica que declara 2.0.1. Se necesita una política de vigencia y sincronización para no confundir instancias históricas con definiciones normativas actuales.

## 6. Hallazgos transversales

1. No existe una semántica universal de directorios: `shared/` puede significar recepción, memoria propia, workspace de equipo o contenedor de entregas/decisiones/bitácoras.
2. Los canales son documentales, no transporte activo. Publicar no prueba recepción, lectura, aceptación ni ejecución.
3. Una misma etiqueta puede representar direcciones distintas. Softly identificó una contradicción entre los README de `Auditoria/Softlysay/` y `Softly/audsay/`.
4. El handoff actual no equivale a un gestor completo de tareas: su schema no define por sí solo estados de ejecución como working, submitted o completed.
5. La instrumentación no es homogénea. Hay logs y eventos, pero propuestas de schema no equivalen a validadores operativos.
6. La confusión de repositorio/ruta durante la creación de Katarina para TITAN produjo una migración de 42 archivos y limpieza posterior. La ubicación final fue verificada; la causa raíz no está demostrada.
7. Más agentes no significa necesariamente mejor resultado. El valor depende de la tarea, capacidad individual, dependencias y costo de coordinación.
8. Las declaraciones de permisos no equivalen a enforcement técnico.
9. La documentación compartida no garantiza comprensión, recepción ni continuidad automática.
10. La duplicación puede ser estructural (copias de archivos), semántica (múltiples entidades para una tarea) o de autoridad (varios actores creen poder aceptar o cerrar).

## 7. Comunicación, coordinación y persistencia

Deben mantenerse separados tres planos:

- **Comunicación:** transmitir un mensaje con emisor, destinatario, tipo, referencia y respuesta.
- **Coordinación:** organizar responsables, tareas, dependencias, estados, integración y escalamiento.
- **Persistencia:** conservar eventos, decisiones, artefactos y evidencia.

Una carpeta o archivo puede servir a uno o más planos, pero no debe confundirse con ellos. La existencia de un archivo en GitHub no despierta un agente. Un handoff publicado queda disponible para una sesión futura; no activa automáticamente al destinatario.

Semántica conceptual:
- `say/`: comunicación direccional.
- `inbox/`: recepción de asignaciones o mensajes.
- `outbox/`: registro de salidas.
- `shared/`: recurso común con reglas de propiedad y edición.
- `deliveries/` / entregables: artefactos producidos.
- bitácora/logs: eventos y cronología.
- `decisions/`: decisiones de autoridad/diseño.
No todas las funciones requieren directorios separados.

## 8. Arquitecturas consideradas

### A. Conservadora
Mantener `say/shared/inbox/outbox`, normalizando identificadores, responsables, estados, handoffs y propiedad. Menor cambio, pero conserva parte de la complejidad y las duplicaciones actuales.

### B. Simplificada y centrada en tareas — recomendada
La tarea es el registro canónico: objetivo, responsable, destinatario, alcance, dependencias, estado, criterios de aceptación y referencias a evidencia. Los eventos registran cambios relevantes; los mensajes se vinculan a tareas cuando corresponde; los entregables se conservan como artifacts referenciados; los workspaces existen solo cuando hay recursos realmente comunes. Las vistas de inbox/outbox pueden derivarse de asignación y autoría.

Katarina propuso una estructura física mínima de `tasks/`, `events/` y `deliveries/`. Softly propone cinco entidades conceptuales: `message`, `task`, `event`, `artifact` y `workspace`. No son incompatibles: las cinco entidades describen responsabilidades; las tres carpetas son una posible organización documental. No se deben convertir automáticamente en cinco directorios obligatorios.

### C. Distribuida/runtime
A2A para tareas y mensajes entre agentes, MCP para herramientas/recursos, registry, eventos, artifacts, observabilidad y workflow persistente. Aporta recepción, notificaciones, reintentos y reanudación reales, pero introduce autenticación, permisos, seguridad, consistencia, infraestructura y mantenimiento. No es el siguiente paso sin evidencia de que la coordinación documental es un cuello de botella.

## 9. Estados y contrato de handoff

Katarina propuso un ciclo conceptual de tarea con estados: READY, CLAIMED, WORKING, DELIVERED, REVIEW, ACCEPTED, REWORK, BLOCKED, INPUT_REQUIRED, CANCELLED y CLOSED. Softly propone separar el estado del proceso/handoff del resultado de la tarea/entrega.

La síntesis recomienda mantener dos dimensiones:
1. **Estado del proceso:** asignado, reclamado, en ejecución, entregado, bloqueado, expirado, cancelado, sustituido o cerrado administrativamente.
2. **Resultado de la entrega:** aceptado/completado, observado, rechazado o incompleto.

El schema actual de Softly existe y contiene `handoff_id`, `event_id`, `status`, `from`, `to`, `assignment_id`, `task`, `result`, `evidence`, `next`, `acceptance`, `created_at` y lease opcional. Sus estados declarados son ready, accepted, rejected, blocked y closed. El schema no demuestra validación runtime, exclusión mutua ni enforcement de transiciones.

Un handoff ampliado podría incluir ID estable, idempotency key, actor, versión, timestamp con zona horaria, estado anterior/nuevo, dependencias, evidencia, aceptación y siguiente acción. La reasignación, duplicación, expiración, leases y ciclo de retrabajo deben diseñarse antes de implementar.

## 10. Formación y evaluación de agentes

No hay evidencia suficiente para exigir formación académica formal universal. Tampoco basta con asumir que las instrucciones garantizan conducta fiable.

Se recomienda:
- **Base universal:** instrucciones breves sobre autoridad, alcance, estado, dependencias, comunicación y entrega.
- **Formación de rol:** para agentes que dirigen equipos, integran resultados, auditan o gobiernan sistemas.
- **Práctica:** ejercicios de dependencia, bloqueo, rechazo, interfaz, concurrencia, entrega y aceptación.
- **Evaluación conductual:** medir lo que el agente hace, no solo lo que puede recitar.

La hipótesis de que una formación extensa mejora a todos los agentes debe probarse frente a instrucciones mínimas y protocolos explícitos.

## 11. Riesgos y controles

| Riesgo | Control propuesto |
|---|---|
| Coordinador sobrecargado | Delegación por equipos y autoridad local delimitada |
| Tareas duplicadas | ID estable, idempotencia y revisión del trabajo previo |
| Escrituras concurrentes | Propietario, partición de rutas o lease; relectura antes de actualizar |
| Mensajes no recibidos | Acuse explícito cuando el riesgo lo justifique |
| Eventos fuera de orden | Secuencia/versionado por tarea |
| Agente no responde | Vencimiento y escalamiento explícito |
| Entrega sin aceptación | Separar entrega, evaluación y cierre |
| Conflicto de autoridad | Matriz de autoridad y escalamiento |
| Contexto excesivo | Referencias y recuperación bajo demanda |
| Memoria contaminada | Namespaces, procedencia y límites de acceso |
| Consenso artificial | Auditoría independiente y desacuerdos explícitos |
| Burocracia | Proporcionalidad; no convertir cada mensaje en una tarea |
| Error de destino | Preflight obligatorio: owner/repo, rama, ruta y operación |
| Falsa autonomía | Separar definición, sesión activa, ejecución y aceptación |

## 12. Experimentos propuestos (no ejecutados)

### 12.1 Competencia universal
Comparar agente actual, instrucciones mínimas, formación estructurada y protocolo explícito. Usar tareas con dependencias, interfaces, bloqueos, encargos fuera de competencia, destino ambiguo y aceptación/retrabajo.

### 12.2 Arquitectura
Comparar estructura conservadora normalizada, modelo centrado en tareas y simulación de runtime. Mantener equipo, tareas, modelo, herramientas y presupuesto constantes.

### 12.3 Métricas
- tasa de tareas aceptadas;
- tiempo de ciclo;
- tokens y tiempo de coordinación, medidos por separado;
- duplicación;
- pérdida de handoff;
- exactitud del estado declarado;
- calidad ciega de entrega;
- intervención humana;
- errores de enrutamiento;
- conflictos de interfaz;
- recuperación ante bloqueos;
- incumplimientos de privacidad/permisos.

No hay resultados de estos experimentos. No se debe declarar ganadora una alternativa por impresiones o una única ejecución.

## 13. Comparación de los informes independientes

| Tema | Katarina | Softly | Síntesis |
|---|---|---|---|
| Arquitectura | Alternativa B | Alternativa B | Convergencia; piloto antes de migrar |
| Unidad central | Tarea con owner/estado | Tarea con responsable/dependencias/aceptación | Tarea canónica |
| Mensajes/eventos/entregables | Registro único, eventos y deliveries | Cinco entidades conceptuales | Entidades separadas, sin directorios obligatorios |
| Coordinación universal | Cuatro dimensiones | Tres niveles | Autocoordinación y pares universales; dirección según rol |
| `say/` | Retirar universalidad progresivamente | No exigir directorios por emisor | Mensaje tipado; canal como metadato/vista |
| `shared/` | Conservar con finalidad/propiedad | Solo para recursos genuinamente comunes | Mantener workspace cuando exista necesidad real |
| `inbox/` | Simplificar como vista de tareas | Vista de tareas asignadas | Vista derivada o compatibilidad temporal |
| `outbox/` | Quitar obligatoriedad | No duplicar por defecto | Registro único de envío/autoría |
| Runtime | Postergar | Postergar | Solo si piloto demuestra cuello de botella |
| Validación | Experimento comparativo | Piloto medido | No migrar sin resultados |

### 13.1 Diferencias abiertas

**A. Modelo conceptual:** Katarina enfatiza el sistema de conocimiento y coordinación cognitiva; Softly enfatiza la arquitectura de información operacional. Son perspectivas complementarias posibles: una describe la función global y otra el mecanismo documental que vuelve accionables contratos, eventos y handoffs. No está resuelta su jerarquía identitaria.

**B. Núcleo mínimo:** Katarina ordena responsabilidades y propone una organización física de tres espacios. Softly distingue cinco entidades semánticas. Se recomienda conservar ambas vistas y probar qué estructura física mínima satisface las responsabilidades.

**C. Competencia sistémica:** Katarina la distingue de la orquestación; Softly la agrupa dentro de niveles de coordinación/orquestación. Requiere decisión conceptual.

**D. Niveles de evidencia:** Softly incluye antecedentes de coordinación y una incidencia concreta de resolución errónea de repositorio durante la creación de TITAN. La causa raíz sigue sin demostrarse. La coincidencia de informes no prueba por sí misma eficacia de la alternativa B.

## 14. Decisiones reservadas a gAto

No se adoptan por cuenta de gAto:
1. Aprobar o rechazar la arquitectura centrada en tareas.
2. Autorizar un piloto y determinar su proyecto/alcance.
3. Aprobar entidades y schema común de tareas, mensajes, eventos y artifacts.
4. Cambiar moldes, contratos, instrucciones de inicio o directorios.
5. Incorporar coordinación universal como requisito normativo.
6. Resolver si coordinación sistémica es una dimensión separada.
7. Resolver la jerarquía entre conocimiento/coordinación cognitiva e información operacional.
8. Autorizar A2A/MCP, workflow runtime o automatización.
9. Autorizar migraciones o retiro de estructuras históricas.

## 15. Recomendación final de Katarina

Recomiendo **Alternativa B mediante un piloto**, no una reescritura inmediata. Antes de modificar los repositorios productivos, definir un modelo conceptual mínimo que especifique:
- tarea con responsable, objetivo, dependencias, estado y aceptación;
- mensajes vinculados cuando transmiten información necesaria;
- eventos mínimos y trazables;
- artifacts con ruta, autor, versión, commit y evidencia;
- workspace con propietario y reglas solo si existe recurso compartido real;
- vistas derivadas de asignaciones y autoría.

Conservar identidad, roles, autoridad, permisos, especialización, independencia de auditoría, evidencia, historia y handoffs. Simplificar gradualmente duplicaciones, outbox obligatorio, canales redundantes y estados representados varias veces. No desplegar runtime antes de medir.

La investigación de Softly y la de Katarina coinciden en dirección, pero no reemplazan la decisión humana. El cierre de este hilo significa que los análisis independientes y su comparación quedaron documentados; **no significa que la arquitectura haya sido aprobada, implementada o validada**.

## 16. Referencias principales

### Repositorios internos
- [Softly — informe final individual de coordinación universal y rediseño](https://github.com/gatoscientist/Softly/blob/main/research/coordination/2026-11-16-investigacion-coordinacion-universal-y-redisenio-arquitectura.md)
- [Katarina — contrato](https://github.com/gatoscientist/Katarina/blob/main/core/CONTRACT.md)
- [Katarina — procedimiento operativo](https://github.com/gatoscientist/Katarina/blob/main/core/OPERATING-PROCEDURE.md)
- [Cytryna — coordinador](https://github.com/gatoscientist/Cytryna/blob/main/Cytryna/coordinator.py)
- [Cytryna — políticas y agentes](https://github.com/gatoscientist/Cytryna/blob/main/AGENTS.md)
- [TITAN — README](https://github.com/gatoscientist/TITAN/blob/main/README.txt)
- [Auditoría — coordinación](https://github.com/gatoscientist/Auditoria/blob/main/TEAM/COORDINATION.md)
- [Auditoría — protocolo de trabajo](https://github.com/gatoscientist/Auditoria/blob/main/TEAM/WORK_PROTOCOL.md)
- [Softly — modelo de agente](https://github.com/gatoscientist/Softly/blob/main/docs/architecture/agent-model-v0.1.md)
- [Softly — patrones de coordinación](https://github.com/gatoscientist/Softly/blob/main/docs/architecture/coordination-patterns.md)
- [Softly — schema de handoff](https://github.com/gatoscientist/Softly/blob/main/schemas/handoff.schema.json)
- [Laboratorio de agentes](https://github.com/gatoscientist/Laboratorio-de-agentes)

### Literatura y documentación técnica consultada
- Malone y Crowston (1994), *The Interdisciplinary Study of Coordination*, https://doi.org/10.1145/174666.174668
- Hayes-Roth (1985), *A Blackboard Architecture for Control*, https://doi.org/10.1016/0004-3702(85)90063-3
- Salas, Sims y Burke (2005), *Is there a “Big Five” in Teamwork?*, https://doi.org/10.1177/1046496405277134
- Bachrach et al. (2019), *Transactive memory systems in context*, https://doi.org/10.1037/apl0000329
- MultiAgentBench (ACL 2025), https://aclanthology.org/2025.acl-long.421/
- AgentVerse (ICLR 2024), https://proceedings.iclr.cc/paper_files/paper/2024/hash/578e65cdee35d00c708d4c64bce32971-Abstract-Conference.html
- A2A specification, https://a2a-protocol.org/v1.0.0/specification/
- Model Context Protocol, https://modelcontextprotocol.io/specification/
- OpenAI Agents SDK, https://openai.github.io/openai-agents-python/
- Microsoft AutoGen group chat, https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/design-patterns/group-chat.html
- AWS transactional outbox, https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/transactional-outbox.html
- Azure architecture principle: minimize coordination, https://learn.microsoft.com/en-us/azure/architecture/guide/design-principles/minimize-coordination

---

**Estado de cierre:** investigación de Katarina archivada; informe final de Softly leído; comparación integrada; decisiones normativas y piloto pendientes de gAto. No se modificaron otros repositorios ni se implementó arquitectura alguna.
