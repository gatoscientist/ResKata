---
title: "Contraste independiente de las propuestas del Glosario Técnico de Softly"
version: "0.1.0"
date: "2026-11-17"
status: "informe de contraste; no normativo; no aprobado"
author: "Katarina 0.2.0-experimental"
scope: "Comparación documental de las dos propuestas originales; sin consolidación ni cambios normativos"
---

# Contraste independiente de las propuestas del Glosario Técnico de Softly

**Estado:** informe de contraste independiente. No es un glosario consolidado, no aprueba ninguna definición y no modifica contratos, schemas ni arquitectura.

## 1. Alcance, fuentes y límites

### Fuentes primarias comparadas

1. **Propuesta de Katarina:** `gatoscientist/ResKata/Katarina/shared/2026-11-17-glosario-tecnico-propuesta-katarina.md`, versión 0.1.0, 662 líneas, SHA consultado `5ef7aa24452f24a6fed0329d8ed560343dbe37df`.
2. **Propuesta de Softly:** `gatoscientist/SoftlyLab/Glosario-Tecnico-Propuesta-Softly-2026-11-17.md`, versión 0.1.0, 592 líneas, SHA consultado `774809ec0de703107263191bf133bef61332a5e8`.
3. **Encargo:** `gatoscientist/ResKata/Katarina/shared/2026-11-17-encargo-contraste-glosario-softly.md`, SHA consultado `8f6c36c83e96c25b70c0f574ba167b5e7f54541f`.

Se leyeron los dos documentos completos desde sus repositorios. La matriz y el análisis siguientes comparan lo que efectivamente afirman esas propuestas, no lo que sería deseable que afirmaran.

### Método

Cada punto se clasifica como:

- **AS — Acuerdo sustantivo:** mismo criterio o consecuencia conceptual.
- **AR — Acuerdo de redacción:** formulaciones distintas, pero sin diferencia material apreciable.
- **DS — Diferencia sustantiva:** definiciones o criterios que conducen a decisiones distintas.
- **OS — Omisión de Softly:** concepto de Katarina ausente o insuficientemente tratado por Softly.
- **OK — Omisión de Katarina:** concepto de Softly ausente o insuficientemente tratado por Katarina.
- **PC — Problema compartido:** ambas propuestas dejan una ambigüedad, insuficiencia o cuestión sin resolver.

Una omisión no se interpreta como desacuerdo. Tampoco se considera acuerdo que ambas propuestas mencionen una palabra si le asignan alcance distinto.

### Límites

- No se leyó DR-06 ni se utilizó como fuente.
- No se abrió una nueva investigación bibliográfica ni se revisaron nuevamente los documentos subyacentes de Softly. El objeto de este encargo es el contraste de las dos propuestas existentes.
- Por tanto, las afirmaciones sobre contratos, schemas, arquitectura o deliberaciones se consignan como referencias y caracterizaciones que las propias propuestas hacen. Este informe no constituye una auditoría independiente de esas fuentes.
- No se ejecutaron experimentos, no se comprobó comportamiento runtime y no se validaron capacidades declaradas.
- No se modificaron Softly, SoftlyLab, contratos, schemas, permisos ni arquitectura.
- No se resuelve aquí la autoridad de aprobación del glosario final.

## 2. Resumen ejecutivo

Las propuestas comparten un núcleo conceptual importante: Softly 1.1 debe describirse sin confundir documentación con ejecución; Runtime está excluido de 1.1; una tarea necesita responsable, dependencias y aceptación; el handoff no constituye por sí solo una nueva clase física de artefacto ni despierta sesiones; la autoridad humana no se deriva de la visibilidad o especialidad; y la persistencia documental no demuestra coordinación efectiva.

Las diferencias de mayor impacto son cinco:

1. **Identidad de Softly.** Softly define una formulación vigente centrada en el núcleo operativo y generativo y trata la matriz generativa como formulación anterior. Katarina considera que la presencia de ambas descripciones en documentos actuales impide declarar equivalencia o reemplazo sin aclaración.
2. **Modelo de coordinación.** Softly desarrolla tres dimensiones de coordinación (propia, entre pares y orquestación). Katarina trata orquestación y coordinación sistémica, pero no incorpora esa taxonomía tridimensional.
3. **Agencia y vocabulario institucional.** Softly ofrece una taxonomía más completa de identidad, definición de agente, brief, rol institucional, taxonomía, dominio, especialidad y disponibilidad. Katarina prioriza la frontera agente/instancia/sesión/herramienta/capacidad/subagente y deja varias categorías institucionales fuera.
4. **Estigmergia y evidencia causal.** Katarina separa medio, traza, señal, percepción e influencia causal. Softly usa una definición más compacta de estigmergia y señal estigmérgica, y recoge vigencia/caducidad/reemplazo/invalidez, pero no desarrolla con el mismo rigor el criterio de adopción causal.
5. **Tamaño y función del glosario.** Softly intenta cubrir también vocabulario de operación, interacción, taxonomías, investigación y deliberaciones actuales. Katarina propone un filtro más estricto para evitar que el glosario se convierta en un segundo manual. Ambas propuestas son extensas y no establecen un umbral operativo verificable para decidir qué queda en el cuerpo principal.

Mi conclusión no es que una propuesta deba prevalecer íntegramente. Softly aporta cobertura institucional y operacional que mi propuesta no tiene; mi propuesta conserva distinciones necesarias para no confundir capacidades, autoridad, señales y evidencia causal. La consolidación debería seleccionar conceptos por su capacidad de prevenir errores concretos, no por procedencia, extensión ni cantidad de entradas.

## 3. Matriz de contraste

### 3.1 Identidad, versión y arquitectura

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Softly: definición | §2: «núcleo operativo y generativo» que transforma intención humana autorizada en coordinación, trabajo y entregables, y custodia coherencia. | B.1: nombre del sistema/proyecto; registra dos niveles descriptivos, núcleo y matriz, sin asumir sinonimia. | **DS** | No está resuelto si matriz y núcleo son niveles complementarios o definiciones incompatibles. Prevalece la descripción normativa para gobernar la operación, pero eso no prueba que la diferencia conceptual sea inexistente. |
| Softly como agente | §2: repositorio no es sesión viva ni agente activado por archivos; la definición central no lo trata como agente individual. | B.1: rechaza reducir Softly a un agente o instancia coordinadora separada. | **AS** | Coinciden en no antropomorfizar ni identificar Softly con un agente individual. |
| Softly 1.1 | §2: versión puente operativa y deliberativa hacia 2.0, con acuerdos arquitectónicos cerrados que se contrastan con tareas reales. | B.1: baseline documental y operativo declarado, bridge-to-2.0; advierte que equivalencia funcional completa debe probarse. | **AR** | La diferencia es de énfasis. Katarina explicita el límite probatorio; Softly explicita el papel de versión puente. |
| Softly 2 / 2.0 | §2: evolución futura cuyo diseño y construcción no están terminados ni autorizados por ser 1.1 un puente. | B.1: objetivo posterior a 1.1, sin definición cerrada ni autorización de construcción. | **AS** | Coincidencia sustantiva y explícita. No se debe hablar de Softly 2 como sistema instanciado. |
| Núcleo y Runtime | §2: núcleo Prompting + Contratos + GitHub; Runtime expresamente excluido y fuera de norma en 1.1. | B.1: núcleo Prompting + Contratos + GitHub; Runtime excluido de 1.1. | **AS** | Coinciden. La exclusión actual no decide por sí sola necesidades futuras. |
| Casa canónica | §2: entrada propia, definición formal pendiente; repositorio de identidad/documentación/memoria, distinto de sesión, proceso, workspace o asignación. | Sin entrada equivalente; B.1 describe repositorio, sesión e identidad por separado. | **OK** | Omisión de Katarina. Puede ser término útil de organización documental, pero no se demuestra que requiera entrada principal. |
| Plano lógico | §3: Definición, Coordinación y Ejecución, sin exigir servicios físicos. | B.1: misma separación conceptual y misma cautela contra convertir planos en componentes. | **AS** | Acuerdo sustantivo. |
| Dimensiones de coordinación | §3: coordinación propia, entre pares y orquestación como tres dimensiones. | B.4: define orquestación y coordinación sistémica; no define coordinación propia/entre pares como dimensiones. | **OK** | Softly desarrolla una taxonomía que Katarina no incorpora. Falta decidir si aporta distinción práctica o duplica el plano lógico. |
| Coordinación sistémica | §3: responsabilidad transversal, no cuarta dimensión, alcance fino abierto. | B.4: mismo criterio, con relación pendiente con orquestación y DIR. | **AS** | Acuerdo sustantivo. |
| Orquestación | §3: dimensión/función de distribución, priorización, secuenciación, integración y escalamiento. | B.4: rol con autoridad explícita que ordena, asigna, prioriza dentro del mandato, gestiona dependencias e integra. | **AR** | Diferencia principalmente de encuadre: dimensión funcional frente a coordinación ejercida por un rol. Conviene no convertir la diferencia de sustantivo en dos mecanismos distintos sin necesidad. |

### 3.2 Agentes, identidad, capacidades y responsabilidad

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Agente | §5: entidad con identidad funcional, propósito, responsabilidades y límites; modelo histórico/propositivo. | B.2: entidad con objetivo, responsabilidad y control operativo; exige autonomía/ciclo/decisión, no solo nombre o instrucciones. | **DS** | Katarina propone un umbral de agencia más exigente y observable. Softly describe atributos de identidad funcional, pero no explicita el mismo criterio de autonomía. |
| Definición de agente | §5: entrada extensa sobre identidad funcional, misión, límites, competencias, método, herramientas, memoria, autonomía, seguridad y evaluación. | No tiene entrada propia; B.2 define agente e instancia, F.1 enumera definición como vocabulario crítico. | **OK** | Softly cubre el artefacto descriptivo/versionado de agente. Katarina no lo desarrolla como término independiente. |
| Instancia de agente | No aparece como entrada propia; la asignación y sesión aparecen separadas. | B.2: realización concreta de una definición, con configuración, modelo, herramientas, permisos y contexto efectivos. | **OS** | Omisión de Softly. La distinción es útil para no tratar definición, ejecución y contexto como una sola entidad. |
| Sesión | §5: sesión de trabajo como unidad temporal de actividad. | B.1: sesión como episodio temporal de trabajo de una instancia; distinta de identidad y commit. | **AR** | Coinciden en temporalidad y en que la sesión no redefine identidad. Katarina explicita su relación con instancia y repositorio. |
| Herramienta y capacidad | Softly separa herramientas requeridas dentro de la definición, pero no presenta entradas autónomas «herramienta» y «capacidad» en §5. | B.2 y C.2: herramienta como interfaz invocable; capacidad como habilidad funcional; no son intercambiables. | **OS** | Omisión importante de Softly. La distinción permite decidir si una función necesita agente autónomo o basta una herramienta. |
| Subagente | §5 no usa entrada propia; Cápsula Directora afirma que especialistas internos no son identidades externas. | B.2: agente delegado con objetivo y autonomía propios; una función/herramienta no basta. | **OS** | Katarina introduce criterio explícito de subagencia que Softly deja implícito. |
| Rol institucional | §5: rol institucional separado de taxonomía profesional. | B.2: rol genérico dentro de tarea u organización; no desarrolla explícitamente rol institucional como categoría diferenciada. | **OK** | Softly ofrece una distinción más específica. |
| Taxonomía, dominio y especialidad | §5: tres entradas diferenciadas; clasificación no acredita competencia. | No hay entradas equivalentes propias; B.2 trata competencia y advierte contra inferirla de taxonomía/especialidad. | **OK** | Omisión de Katarina. Puede ser material de apéndice o documentación de agentes, no necesariamente núcleo del glosario sistémico. |
| Competencia | §5: declarada/demostrada/pendiente; no herencia automática. | B.2: declarada, demostrada o pendiente; taxonomía/especialidad no acreditan automáticamente. | **AS** | Acuerdo sustantivo. |
| No-herencia por defecto | §5: entrada propia para competencias, permisos, herramientas y certificaciones no heredadas automáticamente. | B.2: afirma que taxonomía/especialidad no acreditan competencia; F.1 distingue permisos y capacidades, pero no formula regla general de no-herencia. | **OK** | Softly cubre una regla transversal más amplia. Conviene revisar si una sola regla puede abarcar atributos distintos sin borrar sus fuentes de autoridad. |
| Active Standby | §5: disponibilidad documental para asignación, no ejecución ni herramientas conectadas. | No hay entrada. | **OK** | Término de estado específico de registro/taxonomía. Su inclusión en el glosario principal depende de que sea usado transversalmente. |
| Responsabilidad | §5 y §3: sujeto responsable, límites y responsabilidad de tarea. | B.2 y B.4: obligación de responder por calidad, límites y estado; no confiere permisos ni autoridad de aceptación. | **AS** | Coincidencia sustantiva. Katarina explicita la separación de autoridad y aceptación. |
| Agente DIR | §3: nombre para agente o rol de dirección; definición insuficiente y asunto prioritario. | D.7 y G: no presumir agente separado; opciones identidad autónoma, rol institucional, función de orquestación o combinación. | **AS** | Ambas dejan la ontología abierta. Katarina hace explícito que el nombre no determina qué clase de entidad es. |

### 3.3 Autoridad, permisos y control

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Autoridad humana | §2 gAto: dirección humana y autoridad última sobre propósito, prioridades, permisos y gobierno. | B.3: autoridad legítima para decidir/habilitar; gAto conserva autoridad humana última. | **AS** | Acuerdo sustantivo. |
| Permiso efectivo | No aparece como entrada autónoma. Se menciona en asignación y definición de agente. | B.3: acceso realmente concedido por el entorno, distinto de lo declarado en prompt/contrato. | **OS** | Omisión de Softly. |
| Enforcement | No aparece como entrada autónoma; §1 distingue diseño de implementación, pero no formaliza enforcement. | B.3: aplicación técnica de reglas/permisos, distinta de declaración lingüística; advierte que no debe atribuirse enforcement runtime a 1.1. | **OS** | Omisión de Softly. Es una distinción crítica de seguridad, no una invitación a diseñar Runtime. |
| Orden / instrucción | §8: mensaje de gAto que autoriza acción concreta, distinto de hipótesis o comentario. | B.3: instrucción emitida por autoridad competente y dentro de alcance; no amplía permisos técnicos. | **AR** | Coinciden en la función de autorización. Katarina generaliza el principio a una autoridad competente y explicita límites técnicos. |
| Asignación | §5: vinculación de definición y versión con proyecto, brief, contexto, herramientas, permisos y supervisión. | B.3: vinculación contextual de agente/versión con tarea/proyecto, responsabilidad, herramientas, permisos, contexto y supervisión. | **AR** | Formulación casi equivalente. Katarina incluye explícitamente tarea y responsabilidad. |
| Aceptación | §4: criterio verificable y declaración de término no equivale a evidencia de aceptación. | B.3: decisión de autoridad/revisor competente, distinta de entrega, término y verificación del productor. | **AR** | Coinciden en separar término, verificación y aceptación. Katarina precisa quién acepta. |
| Visibilidad y autoridad | §11: visibilidad no equivale a autoridad de intervención. | B.3: conocimiento, seniority, especialidad o coordinación no crean autoridad. | **AS** | Mismo principio; la formulación de Katarina enumera más falsos sustitutos de autoridad. |

### 3.4 Tareas, artefactos y coordinación

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Tarea | §4: unidad canónica con resultado, responsable, estado, dependencias, entradas, restricciones y aceptación. | B.4: misma unidad canónica y atributos; advierte discrepancia de estados entre contrato y schema/modelo. | **AS** | Acuerdo sustantivo. |
| Responsable / owner | §4: responsable único en cada estado; no confiere autoridad adicional. | B.4: responsable explícito y único; no adquiere aceptación ni permisos. | **AS** | Acuerdo sustantivo. |
| Dependencia | §4: trabajo precedente, referenciado por IDs de tareas. | B.4: mismo criterio; declarar dependencia no demuestra validación automática de ciclos. | **AR** | Coinciden en semántica; Katarina explicita límite de automatización. |
| Estados de tarea | §4: schema proposed, ready, in_progress, blocked, done, cancelled; define condiciones de done y blocked. | B.4: identifica diferencia entre contratos/tarea y modelo/schema; no elige lista. | **PC** | Ambas reconocen el modelo/schema, pero Katarina señala estados adicionales en contracts/tarea.md. No hay base en las propuestas para decidir precedencia en todos los usos. |
| Criterio de aceptación | §4: condición verificable para evaluar resultado. | B.3: decisión de autoridad/revisor competente contra criterios establecidos. | **AR** | Softly define la condición; Katarina añade el acto de aceptación. Son partes complementarias, no necesariamente definiciones rivales. |
| Paquete | §4: artefacto operativo que reúne identidad, mandato, contrato, autoridad, permisos, capacidades, procedimiento e interfaz. | No tiene entrada propia. | **OK** | Omisión de Katarina. Es un artefacto operativo específico, candidato a glosario solo si su semántica se usa fuera del contrato correspondiente. |
| Entregable | §4: resultado con evidencia, verificaciones, referencias, límites y aceptación. | B.4: resultado asociado a tarea con verificaciones, evidencia, referencias, límites y estado de aceptación. | **AS** | Acuerdo sustantivo. |
| Checkpoint | §4: síntesis breve del estado vigente, acuerdos activos, bloqueos y próxima acción. | B.4: misma función; no bitácora cronológica. | **AS** | Acuerdo sustantivo. |
| Handoff | §4: transferencia documental; no despierta sesión ni transfiere autoridad; no quinta clase física. | B.4: mismo criterio y misma cautela sobre quinta clase física. | **AS** | Acuerdo sustantivo. |
| Inbox / outbox | §4: vistas lógicas derivadas, no buzones físicos. | E.6: relegar a nota de diseño, no entrada principal. | **AS** | Acuerdo sustantivo y de ubicación editorial. |
| Canales say/ | §4: históricos/inactivos. | E.7: no incorporar cada canal histórico como entrada; remitir a nota de legado. | **AS** | Acuerdo sustantivo. |
| Tarea fractal | §4: expansión recursiva de conversación/corrección/petición en tareas y reformas que desplazan encargo. | D.6: mantener como etiqueta coloquial si sirve; definir operacionalmente como expansión recursiva no solicitada, no como concepto matemático/arquitectónico aún. | **AR** | Coinciden en que no es contrato vigente. Katarina añade cautela semántica y operacional. |
| Modos de trabajo | §8: Fábrica, Coordinación, Investigación/Deliberación e Interacción conversacional como entradas. | No desarrolla el catálogo; A.1 advierte contra convertir cada modo/proceso en entrada. | **OK** | Softly ofrece vocabulario operacional ausente en Katarina. Falta decidir si estos modos son términos del glosario o instrucciones de uso. |
| Interacción conversacional, deliberación, orden y decisión | §8: separa estos conceptos y señala falta de contrato explícito de intención. | B.3 define orden y A.2 distingue decisión/recomendación; no crea una tipología de interacción. | **OK** | Omisión parcial de Katarina. La distinción puede prevenir que una conversación exploratoria se interprete como tarea u orden. |

### 3.5 Conocimiento, investigación y evidencia

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Fuente / registro | §6 fusiona ambos en una entrada «Fuente / registro», descrita como artefacto original o captura. | B.5 mantiene Fuente y Registro separados: origen de información frente a representación persistida/captura. | **DS** | Diferencia real. La fusión puede ocultar la diferencia entre original y derivado; la separación puede ser útil si esa diferencia cambia procedencia o verificación. |
| Afirmación | §6: proposición delimitada sobre entidades/conceptos/actividades/relaciones; distingue tipo epistemológico de confianza/revisión. | B.5: proposición delimitada que puede recibir evidencia favorable, contradictoria o insuficiente; menciona tipos epistemológicos en el límite. | **AR** | Mismo concepto central. Softly enumera clases; Katarina enfatiza el tratamiento de respaldo. |
| Evidencia | §6: registro verificable con referencia y procedencia; declaración de término no la sustituye. | B.5: dato/registro verificable que respalda, contradice o matiza; valor depende de procedencia, integridad, método, contexto y pertinencia. | **AR** | Katarina ofrece criterios de calidad más explícitos. |
| Procedencia | §6: origen de registro, productor/incorporador y proceso. | B.5: misma reconstrucción; autoría Git no prueba por sí sola agente ejecutor ni decisor. | **AR** | Coinciden; Katarina explicita atribución como problema separado. |
| Contexto / ámbito | §6: marco de validez de la información, contexto/periodo/versión/condiciones. | B.5: condiciones que delimitan interpretación/validez, incluyendo permisos y observación. | **AR** | Diferencia de ejemplos, no de criterio. |
| Síntesis | §6: representación condensada que preserva cobertura, límites, incertidumbre y fuentes. | B.5: misma idea; no sustituye fuente ni convierte inferencias en hechos por compresión. | **AS** | Acuerdo sustantivo. |
| Entidad y concepto | §6: entradas separadas, desde modelo de conocimiento. | No hay entradas propias. | **OK** | Omisión de Katarina. Son términos de un modelo de conocimiento; falta probar que sean necesarios para el vocabulario mínimo transversal. |
| Actividad | §6: proceso delimitado que consume información y produce registros/afirmaciones/síntesis. | No tiene entrada propia. | **OK** | Omisión de Katarina. |
| Observación e inferencia | §6: entradas propias y diferenciadas de hipótesis. | A.2 las incluye como tipos epistemológicos, sin definiciones extensas. | **AR** | Katarina cubre la distinción como clasificación; Softly desarrolla definiciones. |
| Hipótesis y experimento | §6: definiciones separadas y cautela de no confundir diseño con ejecución. | B.5 y F.4: mismo criterio, además de criterios/variables/resultados y límites. | **AS** | Acuerdo sustantivo. |
| Calibración | §6: categorías de respaldo y prohibición de porcentajes sin método. | B.5: misma cautela; distingue calibración de tipo epistemológico. | **AS** | Acuerdo sustantivo. |
| Antiauditoría / investigación adversarial | §6: línea de investigación propuesta, no equipo formal. | No aparece como entrada. | **OK** | Omisión de Katarina. Puede ser una práctica o línea metodológica, no necesariamente término central. |
| Tipos epistemológicos | §1: afirmación, observación, inferencia, hipótesis, resultado, decisión y recomendación aparecen distribuidos por las entradas. | A.2: taxonomía explícita y separada del estado documental. | **OS** | Katarina ofrece una estructura transversal que Softly no formaliza como eje propio. |
| Estado documental vs fuerza normativa | §1: vigente, histórico/inactivo, propuesto, pendiente. | A.2 y D.9: contractual vigente, declarativo vigente, diseño, propuesto, experimental, histórico/inactivo, pendiente; separado del tipo epistemológico. | **DS** | Softly usa cuatro estados; Katarina descompone «vigente» y añade experimental. Las categorías no son directamente equivalentes. |

### 3.6 Estigmergia, tiempo y memoria

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Medio compartido | No tiene entrada propia; GitHub se describe como superficie persistente/de coordinación. | B.6: entorno observable y modificable cuyas trazas pueden influir en acciones posteriores. | **OS** | Omisión de Softly. El concepto permite distinguir el entorno del mecanismo y del soporte concreto. |
| Traza | No tiene entrada propia; §7 habla de señal como registro/cambio observable. | B.6: cambio observable producido por una acción, intencional o subproducto, atribuible y perceptible. | **OS** | Omisión de Softly. La distinción evita llamar señal intencional a todo cambio. |
| Señal | §7: registro/cambio observable que comunica estado, procedencia, responsable o acción habilitada y puede influir. | B.6: marca/representación ofrecida para interpretación; no toda traza es señal intencional. | **DS** | Diferencia central: Softly agrupa registro/cambio y señal; Katarina separa traza de señal intencional. |
| Percepción e interpretación | §7 las deja implícitas en «responden a señales persistentes»; no define etapas. | B.6: proceso explícito de encontrar, interpretar y cambiar conducta. | **OS** | Omisión importante de Softly. |
| Adopción causal | §7 dice «puede influir», pero no exige demostrar que la conducta cambió a causa de la traza. | B.6 y D.3: requisito para afirmar coordinación estigmérgica observada; exige descartar instrucción, asignación y contexto previo. | **OS** | Es la diferencia metodológica más relevante. Sin causalidad, se demuestra persistencia o lectura, no coordinación estigmérgica. |
| Estigmergia | §7: coordinación indirecta mediada por señales persistentes en entorno compartido; GitHub se propone como superficie. | B.6: coordinación indirecta por trazas; aplicación a Softly es hipótesis, no capacidad demostrada. | **DS** | Softly la presenta como línea activa y GitHub como superficie de señales; Katarina exige separar mecanismo declarado de coordinación observada. |
| Estigmergia cognitiva | No tiene entrada. | B.6: coordinación mediada por artefactos interpretables por participantes cognitivos; aplicación propuesta, sin exigir middleware o más agentes. | **OK** | Omisión de Softly. Falta decidir si el término aporta distinción útil respecto de estigmergia general. |
| Vigencia / tiempo de vida | §7: periodo de pertinencia; duración y regla de expiración pendientes. | B.6: vigencia operativa como condición temporal o contextual; no equivale a retención histórica. | **DS** | Softly aproxima vigencia a periodo/tiempo de vida; Katarina la separa de TTL y admite condición/evento. |
| TTL / caducidad | §7: señal caducada por tiempo o condición predefinida; TTL no se nombra como mecanismo separado. | B.6: caducidad por tiempo o condición; rechaza TTL universal. D.4 diferencia vigencia general de expiración temporal. | **AR** | Coinciden en no equiparar caducidad con falsedad ni reemplazo. Katarina hace explícito que TTL sería solo un mecanismo posible. |
| Reemplazo e invalidación | §7: entradas separadas y no equivalentes. | B.6: mismas distinciones y consecuencias diferentes. | **AS** | Acuerdo sustantivo. |
| Demonio de Síntesis | §7: posible agente propuesto para gestionar vigencia, retirar señales y conservar trazabilidad. | D.5/E.2: definir primero la función; no presuponer agente autónomo. | **DS** | Softly conserva la hipótesis como posible agente; Katarina rechaza que el nombre determine la forma de implementación. |
| Memoria documental | §7: documentos, decisiones, registros y evidencias persistentes. | B.6: conjunto persistente para reconstruir continuidad. | **AS** | Acuerdo sustantivo. |
| Contexto activo | Se trata indirectamente en sesión y síntesis, pero no hay entrada equivalente explícita. | B.1/B.6/F.3: se distingue de memoria documental. | **OS** | Omisión de Softly. La diferencia es útil para evitar asumir que persistencia implica carga o recuperación activa. |
| Archivo histórico inactivo | §7: legado consultado bajo demanda, no participa del arranque. | B.6: misma definición; inactividad no autoriza borrar. | **AS** | Acuerdo sustantivo. |
| Modelo de desaparición en tres capas | §7: entrada propia como modelo propuesto de superficie activa, referencia y archivo. | B.6 separa vigencia, caducidad, reemplazo, invalidación, memoria y archivo, pero no presenta el modelo de tres capas. | **OK** | Omisión de Katarina. Es un modelo de retención/representación, no necesariamente un término del glosario principal. |

### 3.7 Experimentación, Git y control de alcance

| Tema | Propuesta de Softly | Propuesta de Katarina | Clase | Resultado del contraste |
|---|---|---|---|---|
| Commit | No tiene entrada propia. | B.7: objeto Git que registra cambio; persistencia no prueba decisión, autoría efectiva, corrección o lectura. | **OS** | Omisión de Softly. Puede ser demasiado técnico para el cuerpo principal, pero su límite probatorio es relevante en trazabilidad. |
| Rama / main | §9: rama, main y política experimental pendiente. | B.7: rama y reversibilidad; no desarrolla main ni política de rama única histórica. | **OK** | Softly conserva contexto de gobernanza de ramas ausente en Katarina. |
| Reversibilidad | §9: experimento reversible como prueba acotada con objetivo, aislamiento, resultado y recuperación. | B.7: propiedad de una intervención que incluye efectos externos y residuales, no solo revertir Git. | **AR** | Coinciden en el criterio general; Katarina explicita los límites de reversión de efectos externos. |
| Línea base | No tiene entrada ni tratamiento explícito. | C.7/F.4: necesaria para comparar alternativas en condiciones equivalentes. | **OS** | Omisión de Softly. |
| Causalidad y contaminación experimental | §1/§6 mencionan método y experimento, pero no desarrollan contaminación ni atribución causal. | C.9/F.4/G.1: distingue causalidad de coincidencia, instrucciones previas y contexto. | **OS** | Omisión de Softly. |
| Costo total y carga humana | §3: atención/administración de atención como capacidad candidata; no desarrolla costo total. | C.8/F.4: costo total incluye tokens, latencia, traspasos, retrabajo, supervisión, fallos, mantenimiento y atención humana. | **OS** | Omisión de Softly. «Atención» no sustituye la evaluación de costo total. |
| Verificación independiente y calidad de aceptación | §4 define criterios y evidencia; no separa de forma explícita productor, verificador independiente y autoridad de aceptación. | C.12/F.4: separa revisión del productor, verificación independiente y aceptación competente. | **OS** | Omisión de Softly. |
| Criterio de detención/cierre | No tiene entrada propia. | C.11/G.2: criterio para impedir deliberación/subtareas indefinidas. | **OS** | Omisión de Softly. |
| Activos protegidos | No tiene entrada propia. | No entrada en glosario B; sí G y límites de permisos. | **PC** | Ambos no formalizan un vocabulario general de protección de activos. Katarina menciona activos protegidos como criterio de reversibilidad, no como concepto plenamente definido. |
| Tres Softlys | §8: hipótesis de tres configuraciones/instancias que comparten casa. | E.1/G.1: no crear tres identidades; decidir si son instancias, perfiles, paquetes o modos. | **DS** | Softly registra la hipótesis; Katarina recomienda no convertirla en identidades antes de definir la ontología y necesidad. |
| Atención humana | §3: capacidad candidata de priorización/escalamiento. | F.4 incluye carga de atención humana como métrica, pero no define «administración de atención». | **OK** | Softly desarrolla una función; Katarina trata la carga como costo. No son equivalentes: administrar atención y medir carga son problemas distintos. |

## 4. Análisis de las discrepancias prioritarias

### 4.1 Identidad de Softly: núcleo y matriz

**Propuesta de Softly, §2:** adopta una definición única centrada en el núcleo operativo y generativo que transforma intención autorizada en coordinación, trabajo y entregables. La nota indica que formulaciones anteriores como laboratorio o matriz deben leerse según fecha y estado.

**Propuesta de Katarina, B.1 y D.1:** observa que `SOFTLY.md` y `docs/operating-model.md` contienen descripciones que no se pueden tratar automáticamente como sinónimos. Propone mantener la diferencia hasta saber si «núcleo» nombra el sustrato mínimo y «matriz» el sistema que lo organiza, o si hay contradicción editorial.

**Evaluación:** la propuesta de Softly puede ser la referencia normativa de operación sin resolver por completo la ontología del sistema. Precedencia documental y equivalencia semántica son preguntas diferentes. El glosario no debería hacer pasar una decisión de precedencia por una demostración conceptual.

**Resoluble documentalmente:** puede identificarse qué formulación se declara vigente en cada documento y qué precedencia afirma la propuesta.  
**Requiere decisión:** si se mantiene una definición única con nota histórica o se explicitan dos niveles relacionados.

### 4.2 Softly 1.1, Softly 2 y estado de construcción

Ambas propuestas coinciden en que 1.1 es el baseline/puente vigente, Runtime está excluido y 2 es objetivo futuro no autorizado por la sola existencia de 1.1.

La diferencia es de precisión: Katarina advierte que «versión vigente» no prueba que todas las capacidades estén implementadas o equivalentes funcionalmente. Softly define el papel operativo y deliberativo de 1.1, pero su sistema de estados no separa con el mismo detalle fuerza normativa, tipo de afirmación y evidencia de ejecución.

**Evaluación:** debe conservarse la separación entre estado de documento, autorización y evidencia de ejecución. Una definición puede estar vigente como documento y seguir sin estar implementada. Una capacidad puede estar declarada sin haber sido validada.

### 4.3 Agente, instancia, sesión, herramienta y capacidad

Softly ofrece una ontología de agente centrada en identidad funcional, propósito, responsabilidades y límites, y desarrolla los artefactos que rodean su incorporación: definición, brief, asignación y sesión.

Katarina exige distinguir la entidad abstracta de su realización contextual y de la sesión temporal. Añade una frontera funcional: capacidad es lo que puede hacerse; herramienta es la interfaz invocable; agente es una entidad con objetivo/ciclo y autonomía propios; subagente requiere autonomía y responsabilidad propias.

**Evaluación:** la propuesta de Softly tiene mejor cobertura del ciclo documental de incorporación. La de Katarina aporta criterios más útiles para decidir si una función debe convertirse en agente. No son alternativas excluyentes: describen ejes diferentes.

**Riesgo:** si el glosario final solo define «agente» y «sesión», puede dejar sin respuesta si una especialidad, lente cognitiva, función invocable o instancia configurada cuenta como agente. Si incluye todas las categorías institucionales sin jerarquía, puede convertirse en un catálogo de taxonomía.

**Recomendación de contraste:** mantener en el núcleo las distinciones que afectan autonomía, permisos y responsabilidad: agente, instancia, sesión, herramienta, capacidad y rol/responsabilidad. Llevar brief, definición versionada, dominio, especialidad, taxonomía y disponibilidad a una sección secundaria o documentación de agentes, salvo que se demuestre uso transversal.

### 4.4 Agente DIR, Cápsula Directora y Tres Softlys

Ambas propuestas mantienen Agente DIR como pendiente. Katarina hace explícitas cuatro posibilidades: identidad autónoma, rol institucional, función de orquestación o combinación. Esta es la formulación más prudente: el nombre no resuelve la categoría.

En Cápsula Directora, Softly la presenta como forma de organizar especialistas como lentes/subcontratos internos, manteniendo integración y responsabilidad en Katarina. Katarina advierte que el término puede sugerir especialistas autónomos separados y propone describir primero el mecanismo, sin multiplicar identidades.

En Tres Softlys, Softly conserva la hipótesis de tres configuraciones o instancias. Katarina se niega a elevarlas a identidades antes de resolver si son instancias, perfiles, paquetes o modos.

**Evaluación:** existe acuerdo de fondo en no inferir autonomía a partir del nombre o especialización, pero falta un criterio operacional compartido. La pregunta correcta no es cuántos nombres existen, sino si cada participante tiene objetivo propio, ciclo de trabajo, autoridad, permisos, contexto, responsabilidad y ciclo de vida independientes.

**Decisión pendiente:** gAto debe decidir si necesita una separación institucional; el análisis documental puede describir las alternativas, pero no elegir el gobierno del sistema.

### 4.5 Autoridad, responsabilidad, permiso y enforcement

Katarina desarrolla autoridad, permiso efectivo y enforcement como conceptos distintos. Softly reconoce autoridad, permisos en otras entradas y no-herencia, pero no define con precisión el permiso efectivo ni la aplicación técnica de reglas.

La distinción importa porque:
- autoridad determina quién puede decidir;
- responsabilidad determina quién responde por el trabajo;
- permiso efectivo describe qué operación permite realmente el entorno;
- enforcement describe qué control técnico hace cumplir una regla.

Una instrucción autorizada no crea una credencial ni elimina una restricción técnica. Un permiso técnico no concede autoridad institucional. Ser responsable no convierte al productor en autoridad de aceptación.

**Evaluación:** la omisión de Softly es material y debería corregirse en el vocabulario mínimo. No exige diseñar Runtime ni afirmar que Softly 1.1 tenga enforcement automático. Es precisamente una distinción para no atribuirle controles que no existen.

### 4.6 Estados de tarea y aceptación

Ambas propuestas reconocen la tarea como unidad canónica, responsable único, dependencias y aceptación. Softly presenta el conjunto de estados del schema y define `done`; Katarina señala una discrepancia entre ese conjunto y los estados que atribuye a `contracts/tarea.md`.

**Evaluación:** no corresponde elegir una lista por conveniencia editorial. La discrepancia se debe conservar en el informe y resolverse en revisión contractual separada. El glosario puede definir «estado de tarea» de forma general y remitir a la fuente normativa vigente, pero no debe inventar una reconciliación.

La aceptación también requiere separar tres actos: productor declara terminado, verificador comprueba y autoridad competente acepta. Ambas propuestas cubren parte de esta distinción; Katarina la formula de manera más completa.

### 4.7 Orquestación y coordinación sistémica

Softly presenta coordinación propia, coordinación entre pares y orquestación como tres dimensiones funcionales. Katarina define orquestación como función/rol con autoridad y coordinación sistémica como responsabilidad transversal.

No hay contradicción necesaria: una clasificación describe modalidades de coordinación; la otra describe una responsabilidad transversal. Sin embargo, las propuestas no explican explícitamente cómo se relacionan las tres dimensiones con la responsabilidad transversal.

**Evaluación:** no crear entradas duplicadas para «orquestación» como modo, dimensión y rol si se trata de una sola función vista desde niveles distintos. El glosario final debería declarar el nivel de análisis de cada término y dejar la relación entre dimensiones y responsabilidad transversal en una nota breve.

### 4.8 Estigmergia: traza, señal y adopción causal

Esta es la discrepancia técnica más importante.

Softly, §7, define señal estigmérgica como registro/cambio observable que comunica estado, procedencia, responsable o acción habilitada y puede influir en trabajo posterior. Define estigmergia como coordinación indirecta por señales persistentes en un medio compartido.

Katarina, B.6 y D.2-D.3, separa:
1. medio compartido;
2. traza, que puede ser intencional o subproducto;
3. señal, como marca ofrecida para interpretación;
4. percepción e interpretación;
5. adopción causal, cuando el participante cambia su conducta a causa de lo percibido.

La diferencia no es meramente terminológica. Si todo cambio observable se llama señal, se pierde la diferencia entre subproducto y comunicación diseñada. Si una traza solo existe y alguien actúa después, no se demuestra que la traza causó la acción.

**Evaluación:** la distinción de Katarina es más fuerte para investigación y medición. Softly puede conservar una definición breve de estigmergia como mecanismo, pero no debería declarar coordinación estigmérgica observada sin evidencia de la cadena causal. GitHub puede ser un medio o superficie potencial; no es por sí solo prueba de estigmergia.

**No resuelto:** qué observación sería suficiente para atribuir adopción causal en un caso real, cómo registrar alternativas causales y cómo medir el efecto sin contaminar el experimento.

### 4.9 Vigencia, TTL, caducidad, reemplazo e invalidación

Softly agrupa «vigencia / tiempo de vida» y define caducidad por tiempo o condición. Katarina sostiene que vigencia es una condición operativa más amplia y que TTL sería solo un mecanismo temporal opcional.

Ambas separan caducidad, reemplazo e invalidación. La diferencia es importante:
- caducidad: terminó la pertinencia por tiempo o condición;
- reemplazo: otra señal asumió la función;
- invalidación: la señal no debe seguir usándose para el propósito declarado;
- archivo: conserva evidencia, aunque ya no gobierne la operación.

**Evaluación:** la estructura de Katarina evita imponer TTL universal. El glosario puede explicar la relación entre términos, pero no debería fijar política de expiración, retención o borrado. Eso requiere reglas por tipo de señal, riesgo y autoridad.

### 4.10 Conocimiento, procedencia y estados epistemológicos

Softly incorpora entidad, concepto, actividad, fuente/registro, afirmación, síntesis, observación, inferencia, hipótesis, calibración y experimento. Tiene una cobertura más completa del modelo de conocimiento.

Katarina reduce entradas y separa fuente de registro. Además, distingue tipo epistemológico de estado documental. Esa separación evita que «vigente» se use como si significara «verdadero», «implementado» o «validado».

**Evaluación:** la propuesta de Softly aporta vocabulario de dominio; Katarina aporta una clasificación transversal. No es necesario mantener todas las categorías como entradas extensas. Una estructura mínima podría tener:
- una nota de estados documentales;
- una nota de tipos de afirmación;
- entradas breves para fuente/registro, evidencia, procedencia y síntesis;
- referencia a documentación metodológica para calibración y taxonomía de conocimiento.

### 4.11 Evaluación experimental, línea base y costo total

Katarina introduce línea base, contaminación, causalidad, reversibilidad real, costo total, carga humana, verificación independiente y criterio de detención. Softly trata experimento, atención y reversibilidad, pero no cubre la mayoría de estos conceptos con el mismo detalle.

**Evaluación:** no todos necesitan una entrada del glosario principal. Sin embargo, son términos necesarios para comparar alternativas de arquitectura sin confundir más componentes con mejor resultado. «Atención» y «costo total» no son equivalentes: la primera es un problema de asignación/priorización de atención humana; el segundo es una medida agregada de recursos y consecuencias.

La línea base y la causalidad son especialmente importantes si se pretende evaluar coordinación estigmérgica o minimalismo. Sin una condición de comparación y control de fuentes alternativas, el resultado no permite atribuir mejoras a una arquitectura.

## 5. Aspectos insuficientemente considerados por ambas propuestas

Además de las omisiones cruzadas, hay problemas compartidos:

1. **Jerarquía entre vocabulario y artefactos.** Ambas mezclan conceptos generales, estados, artefactos, modos y nombres de deliberación. Ninguna fija una regla final suficientemente operacional para decidir cuándo un concepto merece entrada principal, nota o referencia externa.
2. **Relación entre fuerza normativa y evidencia.** Katarina separa más categorías, pero la aplicación a cada entrada puede ser costosa y ambigua. Softly simplifica los estados, pero «vigente» agrupa cosas con fuerza distinta. Hace falta distinguir, como mínimo, estado documental, fuerza normativa y evidencia de implementación, sin convertirlo en una taxonomía burocrática.
3. **Autoridad de las fuentes.** Las propuestas citan documentos, pero no establecen una convención compacta para resolver cuándo una fuente canónica es normativa, cuándo es descriptiva y cuándo es histórica. La precedencia no elimina contradicciones semánticas.
4. **Atribución del cambio.** Procedencia y autoría no bastan siempre para establecer quién decidió, quién ejecutó, qué agente actuó o qué proceso produjo el cambio. Katarina lo señala, pero ninguna propone un mínimo de atribución que sea viable y no invasivo.
5. **Relación entre señal y estado autoritativo.** Las propuestas distinguen señal, estado, autoridad y visibilidad de manera desigual. Ninguna desarrolla una regla compacta para saber cuándo un registro observado puede modificar el estado reconocido por el sistema.
6. **Límites de la adopción causal.** Katarina exige causalidad, pero no define el umbral de evidencia ni el método para atribuir influencia cuando varios participantes comparten contexto. El glosario no debe fingir resolverlo.
7. **Ciclo de vida y retención.** Ambas distinguen caducidad, reemplazo, invalidación y archivo, pero no definen cómo resolver conflictos entre retención, privacidad, auditoría, seguridad y carga de contexto. Este asunto no debe decidirse desde el glosario.
8. **Costo de mantenimiento del propio glosario.** Ninguna define cómo evitar que cada nuevo término, deliberación o excepción aumente el vocabulario permanente. Se necesita un criterio de revisión/eliminación de entradas, no solo de incorporación.
9. **Criterio de cierre.** Katarina nombra el criterio de detención, pero ninguna propuesta define cuándo una deliberación terminológica está suficientemente resuelta para detener cambios.
10. **Prueba de utilidad.** No hay un conjunto de casos mínimos que permita comprobar si las definiciones reducen errores reales de interpretación. La calidad no se puede medir por cantidad de entradas ni por extensión.

Estos puntos no justifican ampliar automáticamente el glosario. Algunos deberían quedar como preguntas de investigación o reglas editoriales fuera de él.

## 6. Decisiones que puede resolver el análisis documental

El contraste permite sostener las siguientes conclusiones sin invocar autoridad nueva:

1. **No hay desacuerdo** en que Softly 2 no está definido ni autorizado para construcción por el solo hecho de que 1.1 sea un puente.
2. **No hay desacuerdo** en que Runtime está excluido de Softly 1.1.
3. **No hay desacuerdo** en que tarea, responsable, dependencia, entregable, checkpoint y aceptación forman el vocabulario operativo central.
4. **No hay desacuerdo** en que handoff no es una quinta clase física de artefacto ni una activación de sesión.
5. **No hay desacuerdo** en que inbox/outbox son vistas lógicas y los canales say/ son legado/inactivos.
6. **No hay desacuerdo** en que la autoridad no se deriva de visibilidad, especialidad o responsabilidad.
7. **No hay desacuerdo** en que memoria documental y contexto/sesión activa no son equivalentes.
8. **No hay desacuerdo** en que caducidad, reemplazo e invalidación tienen consecuencias distintas.
9. **No hay base en ninguna propuesta** para afirmar que la coordinación estigmérgica de Softly haya sido demostrada experimentalmente.
10. **No hay base en ninguna propuesta** para declarar que Agente DIR, Tres Softlys o Demonio de Síntesis constituyan identidades/arquitectura aprobadas.

Estas conclusiones describen el contenido de las propuestas. No sustituyen una auditoría de las fuentes citadas.

## 7. Decisiones que requieren deliberación o autoridad de gAto

Requieren decisión humana explícita, o una deliberación posterior mandatada:

- Qué definición de Softly se adopta y cómo se relacionan núcleo y matriz.
- Si Agente DIR es identidad autónoma, rol institucional, función de orquestación o combinación.
- Si se necesitan Tres Softlys y, en caso afirmativo, qué separación real representan.
- Qué autoridad puede declarar estados autoritativos, aceptar entregables y modificar permisos.
- Qué fuerza normativa tendrá el glosario y quién puede aprobar, versionar o retirar entradas.
- Si se incorpora un mecanismo de gestión de vigencia y archivo, sin presuponer que sea un agente.
- Qué política de expiración, retención y archivo se autoriza.
- Qué criterio de evidencia será suficiente para declarar adopción causal/estigmergia observada.
- Qué experimento, si alguno, se autoriza para comparar coordinación explícita, trazas y alternativas de arquitectura.
- Qué nivel de detalle taxonómico y de modos de trabajo necesita el glosario principal.

La resolución documental de una discrepancia no autoriza modificar contratos, schemas ni arquitectura. Cualquier cambio de esos activos exige su proceso y autorización propios.

## 8. Propuesta de estructura mínima del glosario final

No se redactan definiciones consolidadas en este informe. Como estructura de deliberación, recomiendo un núcleo breve con notas secundarias, no un catálogo de cada término presente en las propuestas.

### Núcleo principal candidato

1. **Identidad y estado del sistema:** Softly, Softly 1.1, Softly 2, núcleo, Runtime, estado documental.
2. **Agencia y control:** agente, instancia, sesión, herramienta, capacidad, rol, responsabilidad, autoridad, permiso efectivo, enforcement.
3. **Trabajo:** tarea, responsable, dependencia, aceptación, entregable, checkpoint, orquestación, coordinación sistémica, handoff.
4. **Conocimiento:** fuente, registro, afirmación, evidencia, procedencia, contexto, síntesis.
5. **Coordinación mediada por entorno:** medio compartido, traza, señal, percepción/interpretación, adopción causal, estigmergia.
6. **Tiempo y memoria:** memoria documental, contexto activo, vigencia operativa, caducidad, reemplazo, invalidación, archivo histórico.
7. **Evaluación:** hipótesis, experimento, línea base, resultado, causalidad/contaminación, reversibilidad, costo total, verificación independiente.

### Notas secundarias o referencias

- Taxonomía, dominio, especialidad, competencia y no-herencia: remitir al modelo de agentes/taxonomías, con una nota sobre no inferir competencia de clasificación.
- Definición de agente, brief, asignación a proyecto y Active Standby: remitir al ciclo documental de incorporación.
- Paquete, modos Fábrica/Coordinación/Investigación, interacción conversacional y canales: remitir a contratos y procedimientos.
- Inbox/outbox y say/: nota de legado/diseño.
- Commit, rama y main: nota Git y gobernanza experimental.
- Entidad, concepto y actividad: apéndice o referencia al modelo de conocimiento.
- Calibración y antiauditoría: método de investigación.
- Tarea fractal, Tres Softlys, Agente DIR, Demonio de Síntesis y Cápsula Directora: registro de términos de deliberación, no entradas normativas por defecto.

La lista principal es una recomendación de estructura, no una decisión de aprobación. Debe aplicarse el filtro: una entrada principal se justifica si su confusión cambia permisos, responsabilidad, decisiones, resultados o evaluación.

## 9. Términos que conviene excluir, relegar o mantener abiertos

| Tratamiento | Términos | Motivo |
|---|---|---|
| Excluir del núcleo por ahora | Tres Softlys como identidades; Demonio de Síntesis como agente; Agente DIR como identidad ya definida | Son hipótesis o nombres sin ontología resuelta. Mantenerlos como preguntas de deliberación. |
| Relegar a nota o apéndice | Casa canónica; Paquete; Brief de incorporación; Active Standby; taxonomía; dominio; especialidad; entidad; concepto; actividad | Tienen significado útil, pero pueden pertenecer a modelos especializados y no al vocabulario transversal mínimo. |
| Relegar a nota de operación/legado | Inbox/outbox; canales say/; main; modos Fábrica, Coordinación e Investigación; rama experimental | Son convenciones o modos dependientes de la operación y su estado histórico. |
| Mantener como conceptos separados | Fuente y registro; agente e instancia; herramienta y capacidad; autoridad, responsabilidad, permiso y enforcement; traza y señal; caducidad, reemplazo e invalidación; memoria documental y contexto activo | Fusionarlos simplificaría el glosario a costa de perder distinciones que cambian decisiones o interpretación. |
| Mantener como preguntas abiertas | Núcleo/matriz; ontología de DIR; autonomía de subagente; tres dimensiones de coordinación y coordinación sistémica; estados de tarea; vigencia/TTL; criterio de adopción causal; retención/archivo; costo y atención; verificación independiente | Las propuestas no aportan evidencia suficiente para cerrar estas decisiones. |
| Evitar como entradas extensas | Tarea fractal; Cápsula Directora; Antiauditoría; modelo de desaparición en tres capas | Son fenómenos, mecanismos, prácticas o propuestas que pueden definirse en notas breves sin convertirlos en subsistemas conceptuales. |

## 10. Riesgos de falsa equivalencia, exceso de vocabulario y pérdida de distinciones

### Falsa equivalencia

- **Núcleo = matriz:** no demostrado.
- **Agente = instancia = sesión:** son niveles distintos.
- **Agente = herramienta = capacidad:** confunde autonomía con interfaz y función.
- **Rol = identidad = taxonomía:** confunde responsabilidad institucional con clasificación.
- **Responsabilidad = autoridad = permiso:** confunde obligación, decisión y acceso.
- **Vigencia = TTL:** reduce una condición contextual a un temporizador.
- **Traza = señal:** convierte cualquier subproducto en comunicación intencional.
- **Persistencia = percepción = adopción:** confunde almacenamiento con influencia.
- **Lectura seguida de acción = causalidad:** no descarta instrucciones o contexto previos.
- **Commit = decisión/autoría/agencia:** el historial técnico no prueba por sí solo quién decidió o ejecutó.
- **Diseño vigente = implementación = validación:** confunde estado documental con comportamiento comprobado.

### Exceso de vocabulario

- Convertir cada artefacto, campo, modo, estado histórico o nombre de deliberación en una entrada principal.
- Mantener definiciones largas que duplican contratos o procedimientos.
- Crear entradas para componentes hipotéticos antes de probar que requieren autonomía o existencia propia.
- Incorporar taxonomías completas al glosario general cuando basta una referencia al modelo de agentes.
- Convertir un problema operativo en una nueva identidad, servicio o subsistema por el solo hecho de nombrarlo.

### Pérdida de distinciones

La reducción no debe eliminar las diferencias entre:
- autorización humana, permiso técnico y enforcement;
- objetivo autónomo y función invocable;
- estado declarado y estado observado;
- traza accidental y señal intencional;
- percepción e influencia causal;
- fuente original y registro derivado;
- caducidad, reemplazo e invalidación;
- memoria persistente y contexto activo;
- verificación del productor y aceptación independiente.

La regla de minimalismo no es «menos palabras a cualquier costo». Es conservar el mínimo de distinciones que previene errores relevantes.

## 11. Tabla final de decisiones pendientes

| Asunto | Opciones reales | Evidencia disponible en las propuestas | Consecuencia de cada opción | Quién debe decidir |
|---|---|---|---|---|
| Identidad de Softly | A) Definición única centrada en núcleo. B) Núcleo y matriz como niveles distintos. C) Mantener discrepancia documentada hasta aclaración. | Softly §2 prioriza núcleo; Katarina B.1/D.1 registra matriz y núcleo como descripciones no reconciliadas. | A) Máxima simplicidad editorial, riesgo de ocultar diferencia. B) Mayor precisión, exige definir relación. C) Conserva incertidumbre, prolonga ambigüedad. | gAto, con propuesta editorial de Softly. |
| Estados documentales | A) Cuatro estados de Softly. B) Estados de Katarina separados por fuerza documental. C) Dos ejes: estado documental y tipo epistemológico, con fuerza normativa explícita. | Softly §1; Katarina A.2/D.9. | A) Simple, pero «vigente» puede agrupar fuerza distinta. B) Preciso, pero más pesado. C) Más discriminante, requiere metadatos y disciplina. | gAto aprueba; Softly propone convención. |
| Agente e instancia | A) Mantener «agente» amplio. B) Separar definición, instancia y sesión. C) Usar distinción solo cuando cambie permisos/autonomía. | Softly §5 separa definición/asignación/sesión; Katarina B.2 añade instancia y criterio de autonomía. | A) Menos términos, más ambigüedad. B) Mayor precisión, más vocabulario. C) Minimalismo condicionado por impacto. | Softly y Katarina pueden proponer; gAto aprueba vocabulario canónico. |
| Herramienta y capacidad | A) Mantener implícitas. B) Entradas separadas. C) Nota breve bajo agencia. | Katarina B.2/C.2; Softly no tiene entradas autónomas. | A) Brevedad con riesgo de confusión. B) Claridad para diseño de agentes. C) Compromiso de tamaño. | gAto, asesorado por Softly/Katarina. |
| Agente DIR | A) Identidad autónoma. B) Rol institucional. C) Función de orquestación. D) Combinación explícitamente delimitada. | Ambas propuestas §3/D.7 lo dejan pendiente. | A) Más autonomía y costo de gobierno. B) No crea nueva identidad. C) Puede bastar si no hay ciclo propio. D) Mayor expresividad y riesgo de complejidad. | gAto. |
| Cápsula Directora | A) Concepto de agente/equipo. B) Mecanismo interno de análisis. C) Relegar a nota de procedimiento. | Softly §5 la declara forma interna; Katarina D.8 advierte riesgo de reificar especialistas. | A) Riesgo de multiplicar identidades. B) Mantiene responsabilidad integrada. C) Reduce glosario y remite al procedimiento. | gAto define el uso; Softly/Katarina proponen la redacción. |
| Tres Softlys | A) Tres instancias. B) Una identidad con perfiles/modos. C) Una identidad y sesiones/contextos separados. D) No adoptar separación. | Softly §8 registra hipótesis; Katarina E.1/G.1 no recomienda identidades sin necesidad demostrada. | A) Separación clara, más coordinación y permisos. B/C) Menos identidades, requiere límites de contexto. D) Menor complejidad, posible pérdida de especialización. | gAto. |
| Dimensiones de coordinación | A) Conservar tres dimensiones de Softly. B) Mantener solo plano lógico y orquestación. C) Conservar dimensiones y definir coordinación sistémica transversal. | Softly §3; Katarina B.4/D.10. | A) Más vocabulario funcional. B) Menos categorías, riesgo de perder distinción pares/propia. C) Mayor precisión, necesita relación clara. | Softly propone; gAto aprueba. |
| Estados de tarea | A) Schema/task-centric. B) Estados de contracts/tarea. C) Reconciliar fuentes y versionar una lista. D) Definir solo «estado» en glosario y remitir al contrato vigente. | Softly §4 cita schema; Katarina B.4 identifica discrepancia documental. | A/B) Mantiene conflicto. C) Requiere revisión contractual separada. D) Evita duplicar contrato, pero no resuelve conflicto operativo. | Autoridad contractual de Softly y gAto. |
| Fuente y registro | A) Una entrada combinada. B) Dos entradas separadas. C) Una familia con distinción breve. | Softly §6 combina; Katarina B.5 separa. | A) Más breve, riesgo de perder original/derivado. B) Preciso, más entradas. C) Compromiso de concisión. | Softly propone; gAto aprueba glosario. |
| Traza y señal | A) Tratar como sinónimos. B) Separar traza de señal intencional. C) Distinguir solo cuando sea relevante para el experimento. | Softly §7 los agrupa en señal; Katarina B.6/D.2 los separa. | A) Breve, pierde causalidad/comunicación. B) Preciso, exige explicar términos. C) Reduce carga, pero puede dejar ambigüedad en casos críticos. | gAto decide vocabulario; investigadores definen protocolo. |
| Evidencia de estigmergia | A) Basta con superficie persistente y señal visible. B) Exigir percepción e interpretación. C) Exigir además adopción causal con alternativas descartadas. | Softly §7 dice «puede influir»; Katarina B.6/D.3 exige cadena causal. | A) Afirmación fácil, débil. B) Demuestra lectura, no necesariamente influencia. C) Mayor rigor, mayor costo experimental. | gAto autoriza criterio; investigación debe justificar método. |
| Vigencia y TTL | A) Vigencia/tiempo de vida juntos. B) Vigencia general y TTL opcional. C) Vigencia por tipo de señal, sin política general aún. | Softly §7; Katarina B.6/D.4. | A) Simple, reduce vigencia a tiempo. B) Distingue condición y mecanismo. C) Evita regla universal, requiere especificación por caso. | gAto para política; Softly para propuesta documental. |
| Demonio de Síntesis | A) Agente autónomo. B) Herramienta/rutina. C) Regla o responsabilidad distribuida. D) No implementar hasta medir necesidad. | Softly §7 lo contempla como agente posible; Katarina D.5/E.2 rechaza presuponer ontología. | A) Más autonomía y carga. B/C) Menor complejidad, menor autonomía. D) Evita anticipar solución. | gAto. |
| Atención y costo total | A) Una entrada conjunta. B) Atención como función y costo como métrica separada. C) Solo medir carga humana dentro de costo total. | Softly §3 define administración de atención; Katarina C.8/F.4 mide costo y carga humana. | A) Confunde función con métrica. B) Mantiene niveles distintos. C) Más minimalista, puede perder problema de priorización. | gAto y responsables de evaluación. |
| Línea base y verificación | A) Mantener fuera del glosario. B) Incluir en núcleo experimental. C) Remitir a método de investigación con entradas mínimas. | Katarina C/F; Softly §6 cubre experimento sin línea base explícita. | A) Glosario breve, investigación menos explícita. B) Evaluación más reproducible, más vocabulario. C) Equilibrio entre núcleo y método. | Softly propone método; gAto autoriza experimentos. |
| Ubicación de términos de taxonomía y conocimiento | A) Núcleo único. B) Núcleo + apéndice. C) Glosario general + referencias a modelos especializados. | Softly §§5–6 es amplio; Katarina A.1/E propone reducir entradas especializadas. | A) Consulta única, mayor tamaño. B) Balance, requiere mantener apéndice. C) Menor duplicación, exige navegación entre documentos. | gAto decide estructura y autoridad editorial. |
| Autoridad de aprobación y mantenimiento | A) Softly mantiene y consolida. B) Aprobación explícita de gAto y mantenimiento delegado. C) Revisión periódica con retiro de términos sin uso. | Ambas propuestas §13 plantean deliberación/aprobación antes de cambios normativos; no definen gobernanza completa. | A) Eficiencia, riesgo de confundir custodia con autoridad. B) Control claro, más carga humana. C) Evita inflación, exige cadencia y criterio de retiro. | gAto. |

## 12. Conclusión: qué está claro y qué sigue abierto

### Suficientemente claro entre ambas propuestas

- Softly 1.1 es el baseline/puente actual; Softly 2 es futuro, no una arquitectura ya construida ni autorizada.
- Runtime está excluido de 1.1.
- Tarea, responsable, dependencia, entregable, checkpoint y aceptación son vocabulario operativo central.
- Handoff no es una quinta clase física ni un mecanismo de activación por sí mismo.
- Autoridad, responsabilidad y permisos no deben confundirse.
- Memoria documental no equivale a contexto activo.
- La persistencia de GitHub no demuestra coordinación estigmérgica efectiva.
- Caducidad, reemplazo e invalidación son estados distintos.
- Agente DIR, Tres Softlys y Demonio de Síntesis siguen siendo preguntas, no decisiones arquitectónicas.

### Abierto

- La relación conceptual entre núcleo y matriz en la identidad de Softly.
- La frontera operacional agente/instancia/herramienta/subagente.
- La relación entre dimensiones de coordinación y coordinación sistémica.
- La ontología y autoridad de DIR y la eventual separación en Tres Softlys.
- La discrepancia de estados de tarea.
- El mínimo vocabulario institucional/taxonómico que debe estar en el glosario principal.
- La distinción formal entre traza y señal y el criterio de adopción causal.
- La relación entre vigencia, TTL, retención y archivo.
- El costo total y la atención humana como criterios de evaluación.
- La gobernanza, versionado, mantenimiento y criterio de retiro del glosario.

**Conclusión independiente:** no recomiendo adoptar íntegramente ninguna de las dos propuestas. Softly cubre mejor el vocabulario institucional, los artefactos operativos y los modos de trabajo; Katarina cubre mejor las distinciones de agencia, control técnico, causalidad y evaluación. La solución más útil probablemente será un núcleo pequeño con notas y referencias especializadas, pero su contenido y autoridad deben decidirse explícitamente. La precisión no se obtiene acumulando entradas ni borrando diferencias: se obtiene conservando solo las distinciones que cambian decisiones, responsabilidades, permisos, resultados o mediciones.

Este informe termina en el contraste. No declara terminado el glosario, no aprueba definiciones y no autoriza cambios en Softly 2, contratos, schemas o arquitectura.
