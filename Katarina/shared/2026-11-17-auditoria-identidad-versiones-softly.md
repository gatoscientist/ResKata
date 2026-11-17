# Auditoría de identidad, versiones y responsabilidades de Softly

**Fecha:** 2026-11-17  
**Emisor:** Katarina (gatoscientist/ResKata, versión 0.2.0-experimental)  
**Destinatario:** gAto  
**Objeto:** revisión de materiales de coordinación e instrucciones sobre identidad, versiones, responsabilidades y capacidades de Softly.  
**Estado:** auditoría documental y propuesta de normalización; no normativa.  
**Límite:** no se modificó la casa canónica gatoscientist/Softly, ni sus contratos, permisos, identidad o instrucciones.

## 1. Dictamen ejecutivo

La identidad estable **Softly** está suficientemente definida en los documentos actuales: es una matriz generativa y sistema autoevolutivo cuyo núcleo operativo/generativo sostiene el ecosistema. El modelo operativo dice expresamente que Softly no es un agente individual ni una instancia coordinadora separada.

La versión actualmente declarada en la casa canónica es **Softly 1.1.0**, con estado **activa** y **bridge-to-2.0**. Esa etiqueta identifica el baseline operativo/documental vigente del sistema Softly. Los documentos revisados no establecen una versión separada y explícita para una supuesta «instancia agente Softly». No corresponde inventarla ni presentar 1.1.0 como versión de un agente convencional.

**Softly 2.0** es el objetivo de una etapa futura de reset/evolución. Los registros deliberativos indican que no estaba instanciada ni iniciada en el corte consultado. No es la versión operativa actual ni una capacidad ya implementada.

**Katarina 2.0.0** es una versión histórica de Katarina, no de Softly. La continuidad de Katarina del 15-11-2026 describe su rediseño como Agent Softly 2.0.0. La expresión «Agent Softly» allí designa la taxonomía profesional de Katarina; no convierte a Softly en Katarina ni transfiere el número 2.0.0 a Softly.

El defecto principal no es una identidad equivocada en el documento normativo central, sino una **sobrecarga semántica de la palabra “versión”** en los materiales de coordinación: se usan versiones de Softly, de Katarina y de otros agentes en el mismo flujo sin identificar siempre a qué entidad pertenecen. Además, «instancia de Softly 1.1» puede interpretarse erróneamente como versión de un agente cuando el propio modelo define Softly como matriz/sistema.

## 2. Estado de identidad y versiones observado

| Dimensión | Estado respaldado por fuentes | No debe inferirse |
|---|---|---|
| Identidad | **Softly** | Que sea un agente convencional individual. |
| Naturaleza | Matriz generativa y sistema autoevolutivo; núcleo operativo/generativo del ecosistema. | Que el repositorio o una sesión de chat sean por sí solos la totalidad de Softly. |
| Baseline canónico actual | **Softly 1.1.0**, estado active / bridge-to-2.0. | Que exista un runtime desplegado o que cada capacidad descrita esté técnicamente ejecutable. |
| Versión separada de una instancia-agente Softly | **No declarada por separado en las fuentes revisadas.** | No asignar 1.1.0 o 2.0.0 a un agente independiente sin decisión explícita. |
| Proyecto/arquitectura actual | Baseline operativo/documental **Softly 1.1.0**. | Que el proyecto haya terminado o que su arquitectura equivalga a Softly 2.0. |
| Objetivo futuro | **Softly 2.0**, etapa de reset/evolución planificada y deliberada. | Que esté instanciada, implementada, validada o activa. |
| Legado | Softly v1.0 / v1.0-legacy, clasificado como histórico inactivo para el arranque de Softly 1.1. | Que el legado haya sido borrado o que sus documentos gobiernen la operación actual. |
| Snapshot fundacional | SOFTLY.v0.2.old.md, archivo histórico. | Que v0.2 sea el baseline vigente. |
| Katarina | En ResKata: identidad katarina, taxonomía Agent Softly, versión 0.2.0-experimental. | Que Agent Softly sea una versión o un sinónimo de la identidad Softly. |
| Katarina 2.0.0 | Diseño histórico de la agente Katarina descrito en el handoff del 15-11-2026. | Que Softly estuviera en versión 2.0.0. |

### Interpretación conservadora de 1.1.0

README.md, SOFTLY.md y CHECKPOINT.md declaran 1.1.0. El contenido los presenta como la versión puente operativa y deliberativa hacia Softly 2.0. En consecuencia, este informe usa **Softly 1.1.0** para identificar el baseline canónico vigente del sistema/proyecto y no crea un campo de «versión de agente Softly» que las fuentes no definen.

Si gAto desea versionar por separado una instancia o agente Softly en el futuro, esa separación requiere una decisión de diseño. No se debe resolver por inferencia.

## 3. Hallazgos de auditoría

### H-01 — “Versión” sin entidad explícita

**Severidad:** alta para coordinación; baja para la identidad canónica.

En los materiales se habla de Softly 1.1.0, Softly 2.0, Katarina 2.0.0, Katarina 1.1 y otras versiones de agentes. Cuando un prompt dice solamente «usa la versión 2.0» o «la instancia es 1.1», no queda determinado a qué entidad pertenece el número.

**Referencias:**
- README.md, SOFTLY.md, CHECKPOINT.md: baseline Softly 1.1.0.
- docs/handoff/2026-11-15-katarina-2.0.0-continuity.md: diseño de Katarina 2.0.0.
- logs/threads/hilo XIV: deliberación que menciona Softly 1.0 y Softly 2.0, sin formalizar aún la nueva etapa.
- logs/threads/hilo XVI: Softly 2.0 como objetivo del reset; versiones y moldes de agentes pendientes de definición.
- logs/threads/hilo XVII: Softly 2.0 todavía no iniciada; la casa canónica de Softly permanece intacta.

**Corrección propuesta:** toda versión debe llevar el sujeto completo: «Softly (baseline del sistema) 1.1.0», «Katarina (agente) 2.0.0», «Audeline (agente) x.y.z». Nunca usar una cifra aislada.

### H-02 — Softly se describe como matriz, pero algunos textos hablan de “instancias de Softly”

**Severidad:** media.

docs/operating-model.md dice que Softly no es un agente individual ni una instancia coordinadora separada. SOFTLY.md, en cambio, comienza con «Toda instancia de Softly 1.1 despierta leyendo...» y utiliza expresiones como núcleo operativo/generativo. La expresión puede referirse a una sesión que recupera el paquete documental, pero no lo explica de forma explícita.

**Corrección propuesta:** reservar «instancia» para una ejecución/sesión concreta de un agente o proceso, si existe evidencia de ella. Para Softly, usar «sistema Softly», «baseline Softly 1.1.0» o «sesión de trabajo que opera bajo el mandato Softly 1.1.0». No atribuir una instancia persistente o runtime por la sola existencia del repositorio.

### H-03 — “Agent Softly” puede confundirse con la identidad Softly

**Severidad:** media.

En el handoff de Katarina 2.0.0, «Agent Softly» es la taxonomía profesional elegida para Katarina. El paquete actual de Katarina en ResKata mantiene taxonomy: Agent Softly, agent_id: katarina y version: 0.2.0-experimental. Softly, por su parte, es la matriz/sistema.

**Corrección propuesta:** cuando se use el término, escribir «Katarina — taxonomía Agent Softly» o «agente Katarina». No llamar a Softly «la agente Agent Softly» ni tratar esa taxonomía como versión de Softly.

### H-04 — Softly 2.0 aparece en deliberaciones, no como baseline vigente

**Severidad:** alta si se reutiliza como instrucción operativa.

El hilo XIV declara que aún no se acordó cómo formalizar la separación entre Softly 1.0 y Softly 2.0. El hilo XVI identifica el reset y la instanciación futura, pero deja taxonomías, molde y versiones pendientes. El hilo XVII confirma que Softly 2.0 no había comenzado y que la casa canónica no debía modificarse todavía. El CHECKPOINT.md mantiene como acción habilitada deliberar para afinar Softly 2.0 y prohíbe iniciar su construcción sin mandato.

**Corrección propuesta:** calificar toda mención como «objetivo/propuesta Softly 2.0, no instanciada ni implementada al corte». No importar reglas, equipos o capacidades de esos hilos como si fueran contrato vigente.

### H-05 — Capacidades de diseño pueden leerse como capacidades técnicas ya disponibles

**Severidad:** alta en prompts de ejecución.

SOFTLY.md y docs/operating-model.md describen la función de transformar intención autorizada en tareas, coordinar trabajo y crear agentes/equipos/herramientas. Sin embargo, los propios documentos delimitan que el repositorio es memoria documental pasiva, que los archivos no despiertan sesiones y que Runtime está excluido. agents/README.md indica que el catálogo conserva definiciones y no representa agentes desplegados. La checklist dice que no certifica competencias reales ni concede permisos.

**Corrección propuesta:** separar siempre:
- **Mandato/función:** lo que Softly debe organizar o producir según su definición.
- **Capacidad documental:** procedimiento descrito y artefactos que puede generar con herramientas disponibles.
- **Capacidad técnica disponible:** herramienta/conexión realmente accesible en la sesión.
- **Ejecución comprobada:** acción efectivamente realizada.
- **Validación/operación:** evidencia específica de pruebas, despliegue y monitoreo.

No afirmar que Softly «puede ejecutar» una operación externa sin verificar la herramienta y autorización concretas.

### H-06 — Autoridad y coordinación: frontera correcta, pero conviene repetirla en los prompts

**Severidad:** media.

SOFTLY.md establece que gAto conserva la autoridad humana última; Softly custodia coherencia, contratos e interfaces y coordina; cada agente responde por su tarea dentro de sus permisos; Katarina conserva integración y entrega de sus tareas. También establece que ningún archivo o commit concede autoridad ni inicia una sesión.

El modelo task-centric añade que la coordinación no concede permisos ni competencias y que la orquestación no reemplaza la responsabilidad del owner.

**Corrección propuesta:** los prompts deben especificar quién decide, quién coordina, quién ejecuta y quién acepta. «Coordinar», «crear», «asignar», «autorizar» y «aceptar» no son verbos intercambiables.

### H-07 — Reglas históricas pueden reactivarse por copia de prompts

**Severidad:** alta.

archive/v1.0-legacy/README.md clasifica expresamente RESET-CORE, canales *say/, handoffs antiguos, esquemas y topologías como legado inactivo para Softly 1.1. El contenido se preserva, pero no gobierna el arranque. El handoff de Katarina 2.0.0 conserva una arquitectura de canales y equipos que es histórica y distinta de la coordinación task-centric vigente.

**Corrección propuesta:** antes de reutilizar un prompt histórico, declarar su estado: «histórico / no normativo». Extraer solo los antecedentes pertinentes y reconstruir la instrucción con el contrato actual. No copiar rutas Katarinasay/ o Softlysay/ como canales operativos vigentes.

### H-08 — Versión por defecto de agentes nuevos no es la versión de Softly

**Severidad:** media.

docs/operating-model.md indica que Softly entrega agentes nuevos como versión 1.0.0, estado Diseñado, salvo instrucción distinta. docs/agent-delivery-checklist.md también establece 1.0.0 para un agente nuevo. Es una regla de versionado de los agentes creados, no una declaración sobre la versión de Softly.

**Corrección propuesta:** escribir «versión inicial por defecto de un agente nuevo: 1.0.0», nunca «Softly usa 1.0.0» ni «Softly es 1.0.0» a partir de esa regla.

## 4. Revisión de prompts y materiales de coordinación concretos

| Material | Riesgo detectado | Tratamiento recomendado |
|---|---|---|
| Texto aportado Buscar instrucciones GitHub.txt | El texto de Katarina dice que la instancia de Katarina declara 2.0.0 y compara esa referencia con un 1.1.0 anterior sin nombrar de forma inequívoca qué entidad tenía cada versión. Puede inducir a interpretar una sucesión de versiones dentro de una sola identidad. | Corregir la explicación al reutilizarla: Katarina 2.0.0 era la versión de Katarina; Softly 1.1.0 era el baseline de Softly. No es una actualización de Softly. |
| docs/handoff/2026-11-15-katarina-2.0.0-continuity.md | Título y contenido nombran correctamente a Katarina 2.0.0, pero se reutiliza en el mismo ecosistema que Softly 1.1.0/2.0. | Mantener como antecedente histórico de Katarina; añadir aclaración al citarlo, sin editar el original. |
| SOFTLY.md | La frase «instancia de Softly 1.1» no distingue sesión, sistema y baseline. | Proponer ajuste editorial en una futura revisión autorizada. |
| README.md y CHECKPOINT.md | Declaran Softly 1.1.0 y puente a 2.0; son coherentes entre sí. | Mantener como fuente de estado actual; no reemplazar por 2.0. |
| docs/operating-model.md | Dice que Softly no es agente individual, pero describe capacidades de fábrica y creación de agentes sin una etiqueta uniforme de capacidad declarada/efectiva. | Conservar su distinción ontológica; añadir lenguaje de capacidad documental vs ejecución real solo con autorización. |
| logs/threads/hilo XIV, XVI, XVII | Contienen propuestas y planes de Softly 2.0 que podrían copiarse como si fueran normas vigentes. | Preservar como deliberación histórica; citar como propuesta/plan, no contrato. |
| agents/README.md y docs/agent-delivery-checklist.md | El versionado 1.0.0 por defecto podría confundirse con la versión de Softly. | Aclarar en futuros prompts que aplica a agentes nuevos creados por Softly. |
| archive/v1.0-legacy/README.md y archive/SOFTLY.v0.2.old.md | Los nombres de versiones históricas podrían reaparecer en prompts sin estado. | Mantener archivados y etiquetarlos como histórico/inactivo o snapshot. |

## 5. Propuesta mínima de normalización

No propongo crear una nueva taxonomía, un registro paralelo ni modificar contratos. Recomiendo usar un bloque breve y estable al inicio de prompts dirigidos a Softly:

~~~text
DESTINATARIO: Softly
IDENTIDAD: Softly (matriz generativa / sistema autoevolutivo).
BASELINE CANÓNICO ACTUAL: Softly 1.1.0.
ESTADO DEL BASELINE: activo; puente deliberativo hacia Softly 2.0.
VERSIÓN DE AGENTE/INSTANCIA SOFTLY: no declarada por separado; no inventar.
OBJETIVO FUTURO: Softly 2.0 (plan/objetivo; no asumir instanciación ni implementación).
AUTORIDAD HUMANA: gAto.
FUENTES NORMATIVAS DE ARRANQUE: SOFTLY.md y CHECKPOINT.md en gatoscientist/Softly, rama main.
REGLA DE PRECEDENCIA: los documentos históricos y deliberativos son antecedentes; no sustituyen las fuentes normativas actuales.
~~~

Si el encargo menciona otro agente, agregar una línea independiente:

~~~text
AGENTE REFERIDO: Katarina | versión 0.2.0-experimental | repositorio gatoscientist/ResKata.
~~~

Si se cita el handoff antiguo, escribir «Katarina 2.0.0 (diseño histórico del agente Katarina, 15-11-2026)». No usar «Softly 2.0.0» como sustituto.

### Regla de redacción para acciones

Cada prompt debería separar explícitamente:

- **Objetivo:** resultado solicitado.
- **Autoridad:** quién puede decidir y qué requiere aprobación.
- **Responsable:** quién ejecuta y responde.
- **Capacidad disponible:** herramientas y permisos verificados para esa tarea.
- **Estado esperado:** propuesta, diseñado, implementado, probado, validado u operativo.
- **Fuentes:** documentos normativos actuales y antecedentes históricos pertinentes.

Esto reduce la ambigüedad sin crear una nueva capa de gobernanza.

## 6. Referencias afectadas y evidencia consultada

Snapshot de la casa canónica gatoscientist/Softly, rama main, HEAD consultado: e7aecc5db775ab4854d3bc61af5492a64d72c916.

| Archivo | Blob SHA observado | Uso en la auditoría |
|---|---|---|
| README.md | bc8122a57786d9df16f1a09126b907b73cec42ee | Declara versión 1.1.0, estado bridge-to-2.0 y Softly 1.1 activa. |
| SOFTLY.md | 25a6ee8eb277983440d11f285573fca674e8b4f5 | Fuente normativa de identidad, autoridad, núcleo, arquitectura y estado de puente. |
| CHECKPOINT.md | f2ff751996d963d4ecf096df8e7fcaed3d3d636f | Estado actual y acción habilitada; Softly 2.0 aún no iniciada. |
| docs/operating-model.md | 893f3fe89d29c9ba630686bf63af4f0c30b2b26e | Define Softly como matriz/sistema, no agente individual. |
| docs/architecture/task-centric-coordination.md | c485aed4c48d743bf1fb449fe3583cdb50b44353 | Responsabilidades, límites de coordinación y autoridad. |
| docs/agent-delivery-checklist.md | 3ebe8b0087ab35102e3dae500796ba364a6f949f | Versión inicial 1.0.0 de agentes nuevos y límites de la checklist. |
| agents/README.md | febf18e9e2bcd0ab2e3ef05fa629038bf0c9d6ac | Catálogo documental, estados de madurez y no equivalencia con despliegue. |
| archive/v1.0-legacy/README.md | a89dfc3bc70391863a7a076c81abc9ab49fe9bb0 | Clasificación de legado inactivo. |
| archive/SOFTLY.v0.2.old.md | 75283c7798a7f448901c7ae613c58a9aef1acb72 | Snapshot histórico fundacional. |
| docs/handoff/2026-11-15-katarina-2.0.0-continuity.md | 3cfd801d8abce174620b2522451a22ef2556f404 | Versión histórica de Katarina, no de Softly. |
| logs/threads/hilo XIV | 10bc9327eaa7c679abb97984008fc93570ae2799 | Deliberación no normativa sobre Softly mínimo, 1.0 y 2.0. |
| logs/threads/hilo XVI | 95640449082d2f1e90bb8e5a2a238099054ee4c1 | Reset/Softly 2.0 planificado, definiciones aún pendientes. |
| logs/threads/hilo XVII | 59c06500d4a2c2fb414268d92cdc49806cd8ee88 | Softly 2.0 no iniciada; casa canónica intacta. |

También se revisaron los documentos de identidad, contrato, permisos, procedimiento y versionado de la instancia actual de Katarina en gatoscientist/ResKata. Esos documentos identifican a Katarina como agente katarina, taxonomía Agent Softly, versión 0.2.0-experimental, y declaran a Softly 1.1.0 como contraparte. Esta distinción es coherente con la lectura anterior.

## 7. Cambios realizados

- **Casa canónica Softly:** ninguno.
- **Contratos, permisos, identidad y arquitectura de Softly:** ninguno.
- **Prompts normativos existentes:** ninguno editado.
- **Repositorios de terceros:** ninguno modificado.
- **Este informe:** propuesta documental creada en la casa de Katarina, sin fuerza normativa.

La publicación del informe no significa que Softly lo haya leído, aceptado o incorporado.

## 8. Incertidumbres pendientes

1. **Versionado independiente de Softly:** no hay una declaración separada de versión de agente/instancia. Las fuentes disponibles no permiten saber si gAto quiere mantener esa distinción como no aplicable o formalizarla en el futuro.
2. **Definición formal de Softly 2.0:** los hilos contienen intención, deliberación y planificación, pero no una especificación normativa final ni evidencia de implementación.
3. **Significado exacto de “instancia de Softly”:** puede referirse a sesión de trabajo, despliegue conceptual o copia de instrucciones. Los documentos no lo tipifican de manera uniforme.
4. **Capacidades efectivas de cada sesión:** dependen de conexiones, herramientas, credenciales y permisos disponibles en el momento. Los documentos revisados no prueban por sí solos el estado de esas conexiones.
5. **Adopción de la normalización:** requiere decisión de gAto si se desea convertir esta propuesta en una convención normativa o incorporarla a plantillas futuras.

## 9. Conclusión

La identidad de Softly no necesita ser renombrada ni reconstruida. El baseline canónico observado es **Softly 1.1.0 activa, puente hacia Softly 2.0**. Softly 2.0 permanece como objetivo futuro no instanciado en el corte consultado. Katarina 2.0.0 pertenece a la historia de Katarina y «Agent Softly» es su taxonomía, no la identidad ni la versión de Softly.

La corrección de mayor impacto es pequeña: **cada prompt debe nombrar explícitamente la entidad a la que pertenece cada versión y separar estado documental de capacidad efectiva**. No se requieren cambios en la casa canónica para aplicar esa disciplina en nuevas instrucciones. Cualquier edición de SOFTLY.md, CHECKPOINT.md, plantillas o contratos queda pendiente de autorización expresa de gAto.

---
**Fin del informe.**