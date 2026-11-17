# Informe para gAto — KAT-SOFTLY-FUTURE-BLOCKERS-2026-001

**Emite:** Katarina  
**ID:** katarina  
**Versión:** 2.0.1  
**Instancia:** katarina-home-main  
**Taxonomía:** Agent Softly  
**Fecha:** 2026-11-16  
**Mandato:** KAT-SOFTLY-FUTURE-BLOCKERS-2026-001  
**Estado documental de Katarina:** Diseñado  
**Estado del informe:** entregado documentalmente; contraste con Audeline pendiente.

## 1. Dictamen ejecutivo

Softly puede continuar evolucionando sin Runtime para sus funciones documentales, deliberativas y de coordinación basadas en Prompting + Contratos + GitHub. Esto no es una interpretación nueva: está declarado en SOFTLY.md, el molde de agentes, la checklist y los documentos de coordinación.

El riesgo central es que el ecosistema confunda **lo que está definido, lo que está persistido, lo que fue recibido, lo que está activado, lo que se está ejecutando y lo que fue aceptado**. Esos estados son distintos. Si se mezclan, aparecen bloqueos artificiales, tareas huérfanas, falsas transferencias, trabajo duplicado y esperas sin dueño.

La arquitectura task-centric reduce parte de esa ambigüedad al hacer de la tarea la unidad primaria. Sin embargo, el propio documento y el informe de KAT-006 reconocen que el schema no valida dependencias entre tareas, ciclos, referencias huérfanas ni aceptación efectiva. El diseño está definido documentalmente, pero la coordinación a escala requiere disciplina y verificaciones de conjunto.

La segunda brecha relevante es de gobernanza: la coordinación sistémica sigue sin dueño/alcance explícito. gAto preservó tres posibles interpretaciones y no aprobó una conclusión. Al aumentar el número de agentes y repositorios, esta pregunta puede convertirse en una responsabilidad omitida o en una sobrecarga del orquestador.

## 2. Qué podría trabar a Softly mañana

### Bloqueos inmediatos
1. **Runtime como peaje artificial.** El hilo actual ya exhibió una interpretación contraria a SOFTLY.md: se trató Runtime como requisito para trabajo que podía avanzar mediante análisis y documentación. Es un incidente de coordinación observable en esta conversación; no es una conclusión derivada solo de los repositorios.
2. **Handoff sin acuse.** Un archivo publicado puede quedarse sin receptor efectivo. La transferencia no está completa hasta que exista respuesta y continuidad de responsabilidad.
3. **Tareas sin owner/aceptador claro.** Un resultado puede quedar esperando una persona que nadie designó, o el orquestador puede asumir autoridad que no tiene.
4. **Dependencias no comprobadas.** Los estados ready/done pueden ser inconsistentes con el grafo real cuando aumente el número de tareas.

### Bloqueos en la siguiente etapa
5. **Coordinación sistémica sin definición.** Puede quedar fuera de la responsabilidad de todos o convertirse en una carga difusa.
6. **Rutas, versiones e instancias mezcladas.** La reconstrucción o ampliación de equipos puede generar escrituras en repositorios equivocados y asignaciones a agentes obsoletos.
7. **Capacidad declarada confundida con competencia/disponibilidad.** La taxonomía o Active Standby no prueban que el especialista esté habilitado para la tarea ni que exista una sesión activa.
8. **Aprobaciones no separadas por alcance.** Una decisión humana pendiente puede detener trabajo independiente que sí está autorizado.

### Bloqueos al crecer el ecosistema
9. **Ciclos de dependencia entre equipos.** Los handoffs y las tareas pueden formar esperas circulares.
10. **Sobrecarga de validación.** Los protocolos de calidad pueden convertirse en gates innecesarios si se aplican sin proporcionalidad.
11. **Deriva documental.** Paquetes antiguos y actuales pueden mezclarse; propuestas históricas pueden reaparecer como mandatos.
12. **Automatización prematura.** Construir infraestructura antes de medir el cuello de botella puede aumentar complejidad y dependencia sin resolver ambigüedades de responsabilidad.

## 3. Hallazgos y evidencia

Se preservó una evaluación independiente con 15 hallazgos KFB-01 a KFB-15. El registro de evidencia EV-01 a EV-15 vincula cada hallazgo con fuentes exactas de Softly y Katarina.

Hallazgos de mayor prioridad:
- KFB-01: dependencia artificial de Runtime.
- KFB-02: persistencia confundida con recepción/activación/ejecución.
- KFB-03: estados y dependencias sin verificación de conjunto.
- KFB-04: responsabilidad difusa entre owner, orquestador y aceptador.
- KFB-09: ambigüedad de rutas/repositorios/permisos.
- KFB-14: handoff sin respuesta ni aceptación.

La matriz cualitativa está en el archivo complementario. Las prioridades no son probabilidades estadísticas: expresan impacto potencial y exposición estructural.

## 4. Lo que ya está bien encaminado

- SOFTLY.md define un modo Fábrica predeterminado y prohíbe exigir Runtime para entregas documentales.
- El molde permite resolver detalles no críticos con supuestos explícitos, evitando detener el trabajo por información secundaria.
- La taxonomía separa dominio, especialidad, competencia, permisos y disponibilidad, y aplica no-herencia.
- El handoff incluye evidencia, siguiente acción y criterio de aceptación.
- El modelo task-centric define owner, dependencias, estados, resultados y bloqueos.
- El checkpoint diferencia decisiones adoptadas, propuestas, etapas pendientes y trabajo no ejecutado.
- Los documentos insisten en no confundir Diseñado con desplegado o ejecutándose.

Estas reglas son fortalezas documentales. No son prueba automática de cumplimiento en todas las sesiones.

## 5. Recomendaciones prioritarias

**Prioridad inmediata:** (1) prohibir el bloqueo por Runtime cuando el resultado solicitado sea documental o conceptual; (2) exigir acuse explícito del receptor en handoffs; (3) identificar owner, integrador, aceptador y autoridad de escalamiento; (4) no permitir que una tarea se declare done solo por un mensaje de término.

**Antes de escalar:** (5) verificar el grafo de dependencias en tableros multi-tarea; (6) realizar preflight de repositorio/ruta/versión/instancia/permisos; (7) resolver el alcance y propietario de coordinación sistémica; (8) registrar ciclo de vida de agentes y transiciones con evidencia.

**Para mantener eficiencia:** (9) aplicar validaciones proporcionales; (10) usar checkpoint como índice y recuperar historia bajo demanda; (11) justificar Runtime/A2A/MCP/workflow engine con métricas de cuello de botella, no con intuición.

El detalle y racional de cada recomendación está en el documento complementario. Ninguna recomendación fue implementada ni modifica contratos.

## 6. Contraste con Audeline

El contraste queda **pendiente**. En el repositorio indicado `gatoscientist/Audeline` no se recuperó la misión `AUD-SOFTLY-INTEGRITY-2026-001`, un informe completo atribuible a ella ni commits específicos de esa misión. Se consultó además `gatoscientist/Auditoria`, sin encontrar el ID exacto en commits. La actividad reciente visible de Audeline en Auditoria corresponde a KAT-006 y no demuestra el término de la auditoría de integridad de Softly.

No leí conclusiones de Audeline. Los hallazgos preliminares de Katarina fueron creados y releídos desde GitHub antes de la comprobación de su estado. Por tanto, la independencia documental de esta primera evaluación queda preservada.

No se afirma que Audeline no esté trabajando en una sesión no persistida o en otra ubicación no consultada. Solo se afirma que no hay evidencia recuperada suficiente para declarar la misión terminada.

## 7. Decisiones que requieren a gAto

1. Definir si la coordinación sistémica queda dentro de la orquestación, como responsabilidad transversal, o como capacidad diferenciada.
2. Autorizar o no un piloto acotado de handoffs con acuse y verificación de dependencias.
3. Decidir si se formalizan owner, integrador y aceptador como campos o reglas comunes.
4. Decidir el ciclo de vida canónico de agentes e instancias.
5. Autorizar cambios posteriores a SOFTLY.md, moldes, contratos, schemas o directorios, si se consideran necesarios.
6. Definir qué evidencia justificaría inversión en Runtime u otra automatización.

## 8. Límites de la investigación

- La evaluación es documental y arquitectónica.
- No se ejecutaron experimentos ni pruebas de coordinación multiagente.
- No se midió frecuencia de incidentes, probabilidad, latencia ni costo.
- No se inspeccionó configuración privada ni se asumió ejecución real de agentes.
- No se modificó Softly ni se implementaron recomendaciones.
- El contraste independiente con Audeline sigue abierto.

## 9. Entregables y trazabilidad

- Investigación preliminar independiente: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-preliminar.md`.
- Registro de evidencia: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-evidencia.md`.
- Matriz de riesgos: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-matriz-riesgos.md`.
- Contraste pendiente con Audeline: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-contraste-audeline.md`.
- Recomendaciones: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-recomendaciones.md`.
- Este informe final: `shared/2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-informe-final.md`.

**Estado final de la misión:** investigación documental independiente entregada; contraste externo pendiente por falta de evidencia persistente de la misión de Audeline; sin cambios normativos ni implementación.

**Katarina queda disponible para responder preguntas de gAto.**