---
title: "Glosario técnico de Softly — propuesta independiente de Katarina"
version: "0.1.0"
date: "2026-11-17"
status: "propuesta independiente para contraste; no normativa"
author: "Katarina 0.2.0-experimental"
scope: "Softly 1.1, antecedentes pertinentes y vocabulario necesario para investigar Softly 2"
---

# Glosario técnico de Softly — propuesta independiente de Katarina

**Estado:** propuesta independiente, no normativa y no aprobada.  
**Propósito:** ofrecer una segunda posición conceptual para contrastar con la propuesta de Softly. No consolida ambas propuestas ni modifica contratos, schemas o arquitectura.

## A. Criterios de construcción

### A.1 Qué merece una entrada

Incluyo un término cuando cumple al menos una de estas condiciones:

1. Su confusión puede cambiar una decisión, permiso, responsabilidad o resultado.
2. Es necesario para describir o medir un mecanismo que Softly quiere investigar.
3. Aparece con significados distintos en fuentes pertinentes.
4. Permite distinguir diseño, documentación, ejecución o evidencia.
5. Su ausencia puede inducir a construir componentes innecesarios o atribuir capacidades no demostradas.

No incluyo cada nombre de archivo, campo, modo o elemento de Git como entrada independiente. Los términos técnicos conocidos se definen solo cuando su significado local afecta al diseño. Un glosario no debe convertirse en un segundo manual de operación.

### A.2 Estados documentales y tipos epistemológicos

Propongo separar dos preguntas que no son equivalentes: **¿qué clase de afirmación es esta?** y **¿qué vigencia documental tiene?**

**Estado documental**
- **Contractual vigente:** definido por un contrato o instrucción de arranque vigente de Softly 1.1.
- **Declarativo vigente:** aparece en la superficie actual, pero no necesariamente tiene un contrato estructural.
- **Diseño:** formulación conceptual documentada, todavía no aprobada como regla operativa.
- **Propuesto:** alternativa o hipótesis sometida a deliberación.
- **Experimental:** probado en un ámbito acotado, sin generalización ni adopción automática.
- **Histórico/inactivo:** antecedente conservado que no gobierna la operación actual.
- **Pendiente:** la evidencia no permite fijar significado, alcance o autoridad.

**Tipo epistemológico**
- **Fuente:** artefacto del que se obtiene información.
- **Observación:** descripción de algo registrado o visto.
- **Inferencia:** conclusión derivada de evidencia o premisas.
- **Hipótesis:** explicación provisional susceptible de prueba.
- **Resultado:** salida registrada de una actividad o experimento.
- **Decisión:** elección adoptada por una autoridad competente.
- **Recomendación:** propuesta todavía no adoptada.

Una entrada puede tener más de un estado documental según la parte de su definición. No usaré «vigente» como sinónimo de «verdadero», «implementado» o «validado».

### A.3 Regla de evidencia

Cada definición distingue: (a) qué dice la fuente, (b) qué propongo como definición útil y (c) qué no se puede concluir. La precedencia normativa sirve para saber qué regla rige hoy; no convierte toda formulación canónica en una definición científicamente completa. Una fuente canónica también puede contener ambigüedades o límites.

---

## B. Glosario independiente

### 1. Identidad y arquitectura

#### Softly
Nombre del sistema/proyecto que organiza el trabajo y su evolución. En las fuentes actuales aparecen dos niveles descriptivos: SOFTLY.md define un núcleo operativo y generativo; docs/operating-model.md describe una matriz generativa y sistema autoevolutivo, y niega que Softly sea un agente individual o una instancia coordinadora separada.

**Estado:** declarativo vigente con diferencia de nivel descriptivo pendiente de aclaración editorial.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; docs/operating-model.md; CHECKPOINT.md.  
**Límite:** no resolveré esa diferencia reduciendo Softly a un agente, ni suponiendo que «núcleo» y «matriz» son sinónimos exactos. Puede que describan niveles distintos, pero la relación no está formalizada con precisión suficiente.

#### Softly 1.1
Baseline documental y operativo declarado, versión 1.1.0, estado bridge-to-2.0. Tiene un núcleo permitido Prompting + Contratos + GitHub; Runtime está excluido. La equivalencia funcional completa aún debe probarse mediante tareas reales.

**Estado:** contractual/declarativo vigente.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; CHECKPOINT.md.  
**Límite:** la etiqueta de versión no demuestra por sí sola la madurez de cada capacidad descrita.

#### Softly 2
Objetivo de evolución posterior a 1.1, todavía sin definición cerrada ni autorización de construcción. Debe tratarse como espacio de investigación y decisión, no como arquitectura ya existente.

**Estado:** objetivo propuesto; diseño pendiente.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; CHECKPOINT.md.  
**Límite:** no atribuirle componentes, instancias o capacidades antes de que se decidan y prueben.

#### Plano lógico
Distinción conceptual entre Definición, Coordinación y Ejecución. Sirve para separar preguntas arquitectónicas, no para exigir tres servicios, directorios o agentes.

**Estado:** vigente 1.1.  
**Fuente:** gatoscientist/Softly, SOFTLY.md.  
**Límite:** un plano no equivale a un componente desplegado.

#### Núcleo
Conjunto mínimo de elementos que el diseño declara necesarios para una función. En Softly 1.1, el núcleo permitido es Prompting + Contratos + GitHub.

**Estado:** vigente 1.1.  
**Fuente:** gatoscientist/Softly, SOFTLY.md.  
**Límite:** «núcleo» no debe usarse como sinónimo de sistema completo, infraestructura de ejecución o lista exhaustiva de capacidades.

#### Runtime
Entorno o mecanismo técnico que ejecuta procesos de agente, herramientas y ciclos de control. Está expresamente excluido de Softly 1.1.

**Estado:** excluido en 1.1.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; CHECKPOINT.md.  
**Límite:** su exclusión actual no prueba que sea innecesario para toda evolución futura; tampoco autoriza diseñarlo ahora.

#### Repositorio
Espacio Git que conserva archivos, referencias y un historial de cambios. Puede actuar como memoria documental y superficie de señales, pero no es por sí mismo una sesión, un agente ni un mecanismo de activación.

**Estado:** vigente como superficie documental.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; docs/operating-model.md.  
**Límite:** persistencia no equivale a percepción, interpretación, notificación o ejecución.

#### Sesión
Episodio temporal de trabajo de una instancia. Puede leer contexto, producir acciones y resultados, y terminar sin que la identidad documental del agente desaparezca.

**Estado:** modelo de diseño histórico/propositivo; no es una de las cuatro clases físicas de artefactos de 1.1.  
**Fuente:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md.  
**Límite:** no asumir que un commit crea, despierta o prolonga una sesión.

### 2. Agencia, capacidad y responsabilidad

#### Agente
Entidad de trabajo con un objetivo, un ámbito de responsabilidad y algún grado de control sobre cómo realiza su trabajo. Para clasificar algo como agente no basta con que tenga nombre, especialidad o instrucciones: importa si mantiene objetivo/ciclo de trabajo propio, toma decisiones operativas y responde por un resultado.

**Estado:** concepto documentado; modelo general aún en contraste.  
**Fuentes:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md; docs/architecture/agent-anatomy.md; agents/README.md.  
**Límite:** la documentación de un agente no prueba que exista una instancia activa o desplegada.

#### Instancia de agente
Realización concreta y contextual de una definición de agente, con configuración, modelo, herramientas, permisos y contexto efectivos. Dos instancias pueden compartir definición y diferir en asignación o sesión.

**Estado:** distinción de diseño.  
**Fuente:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md.  
**Límite:** el término no está formalizado como contrato operativo de Softly 1.1.

#### Herramienta
Interfaz invocable que permite ejecutar una operación delimitada. Puede encapsular una función sofisticada o especializada sin tener identidad, objetivo general, autoridad ni responsabilidad autónoma.

**Estado:** distinción analítica respaldada por la separación agente/herramientas del modelo de anatomía y por la aclaración de AgenteDIR registrada en DR-09.  
**Fuentes:** gatoscientist/Softly, docs/architecture/agent-anatomy.md; gatoscientist/SoftlyLab, DR-09, secciones 5–7.  
**Límite:** una herramienta puede tener efectos importantes; «no es agente» no significa «no requiere permisos, pruebas o controles».

#### Capacidad
Habilidad funcional que un sujeto o sistema puede ejercer. Puede estar declarada, disponible mediante una herramienta o demostrada en una evaluación. No es necesariamente un componente separado.

**Estado:** concepto documentado; niveles de evidencia explícitos en la documentación de taxonomías.  
**Fuentes:** gatoscientist/Softly, docs/architecture/taxonomy-and-mold-validation.md; docs/architecture/agent-model-v0.1.md.  
**Límite:** no confundir capacidad declarada con capacidad efectiva o demostrada.

#### Subagente
Agente delegado con un objetivo y un grado de autonomía propios, aunque opere bajo un agente principal. La delegación de una función a una herramienta o especialista interno no basta para establecer que existe un subagente.

**Estado:** distinción analítica propuesta; no es una categoría contractual vigente de 1.1.  
**Fuente:** gatoscientist/SoftlyLab, DR-09, sección 5.  
**Límite:** requiere criterios observables de autonomía, contexto, responsabilidad y ciclo de vida antes de usarse como categoría formal.

#### Rol
Función que un sujeto desempeña dentro de una tarea u organización, como dirección, coordinación, auditoría o ingeniería. No define por sí solo la identidad ni acredita competencias.

**Estado:** distinción conceptual; formalización pendiente.  
**Fuentes:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md; propuesta de glosario Softly.  
**Límite:** «rol» puede usarse en sentido institucional o como campo del modelo de agente; conviene especificar cuál en cada caso.

#### Competencia
Capacidad para ejecutar una actividad concreta. Debe distinguirse entre competencia declarada, demostrada y pendiente de prueba.

**Estado:** vigente en el modelo documental de taxonomías.  
**Fuente:** gatoscientist/Softly, docs/architecture/taxonomy-and-mold-validation.md.  
**Límite:** una taxonomía o especialidad no acredita automáticamente competencia.

#### Responsabilidad
Obligación de responder por la calidad, límites y estado de un trabajo aceptado. No equivale a permiso para realizar cualquier acción necesaria ni a autoridad para aprobar el propio resultado.

**Estado:** vigente como principio de coordinación 1.1.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; docs/architecture/task-centric-coordination.md.  
**Límite:** la responsabilidad de integración de Katarina no se transfiere a sus especialistas internos.

### 3. Autoridad y control

#### Autoridad
Facultad legítima para decidir o habilitar acciones dentro de un ámbito. En Softly, gAto conserva la autoridad humana última; Softly custodia coherencia y coordina dentro de su mandato.

**Estado:** contractual vigente.  
**Fuente:** gatoscientist/Softly, SOFTLY.md.  
**Límite:** visibilidad, conocimiento, seniority, especialidad o coordinación no crean autoridad.

#### Permiso efectivo
Acceso realmente concedido por el entorno o sistema técnico a una operación o recurso. Debe distinguirse de lo que un prompt, perfil o contrato declara que un agente debería poder hacer.

**Estado:** distinción vigente en contratos y documentación de seguridad.  
**Fuentes:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md; gatoscientist/ResKata, Katarina/core/PERMISSIONS.md.  
**Límite:** el documento de permisos expresa facultades del mandato; la ejecución depende de credenciales y controles técnicos disponibles.

#### Enforcement
Aplicación técnica de una regla o permiso, fuera de la mera declaración en lenguaje natural. Puede impedir o permitir una operación incluso cuando el modelo propone otra cosa.

**Estado:** distinción de diseño documentada.  
**Fuentes:** gatoscientist/Softly, docs/architecture/agent-anatomy.md; docs/architecture/agent-model-v0.1.md.  
**Límite:** Softly 1.1 declara contratos y procedimientos documentales; no debe atribuirse enforcement runtime no implementado.

#### Orden
Instrucción emitida por una autoridad competente que habilita una acción dentro de un alcance identificable. No toda conversación, idea o hipótesis es una orden.

**Estado:** distinción de autoridad vigente; tipología de interacciones pendiente.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; deliberación registrada en CHECKPOINT.md.  
**Límite:** una orden tampoco puede ampliar permisos técnicos o anular restricciones superiores.

#### Asignación
Vinculación contextual de un agente y una versión con una tarea o proyecto, incluyendo responsabilidad, herramientas, permisos, contexto y supervisión aplicables.

**Estado:** modelo histórico/propositivo.  
**Fuente:** gatoscientist/Softly, docs/architecture/agent-model-v0.1.md.  
**Límite:** asignar trabajo no crea una identidad ni garantiza que la sesión haya comenzado.

#### Aceptación
Decisión de la autoridad o revisor competente de que un entregable satisface los criterios establecidos. Es distinta de la entrega, de la declaración de término y de la verificación técnica realizada por quien produjo el trabajo.

**Estado:** contractual vigente.  
**Fuentes:** gatoscientist/Softly, contracts/tarea.md; contracts/entregable.md.  
**Límite:** el autor no debe presentar su propia declaración de término como aceptación externa.

### 4. Trabajo y coordinación

#### Tarea
Unidad de coordinación que vincula un resultado esperado con responsable, estado, dependencias, entradas, restricciones y criterios de aceptación. Es la unidad canónica declarada por Softly 1.1.

**Estado:** contractual vigente, con discrepancia de vocabulario de estados entre documentos.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; docs/architecture/task-centric-coordination.md; contracts/tarea.md; schemas/task.schema.json.  
**Límite:** los estados no son completamente uniformes: contracts/tarea.md incluye accepted, delivered y accepted_by_requester; el modelo task-centric/schema contempla proposed, ready, in_progress, blocked, done y cancelled. No los fusiono ni decido cuál prevalece en todos los usos sin una revisión contractual.

#### Responsable / owner
Sujeto identificado que responde por la tarea en su estado actual. La coordinación 1.1 requiere un responsable explícito y único en cada estado.

**Estado:** vigente 1.1.  
**Fuentes:** gatoscientist/Softly, contracts/tarea.md; docs/architecture/task-centric-coordination.md.  
**Límite:** el responsable no adquiere automáticamente autoridad de aceptación ni permisos adicionales.

#### Dependencia
Relación que indica que un trabajo requiere la satisfacción previa de otro. En el modelo task-centric se referencia mediante IDs de tareas, no mediante nombres de agentes o mensajes.

**Estado:** vigente 1.1.  
**Fuente:** gatoscientist/Softly, docs/architecture/task-centric-coordination.md.  
**Límite:** declarar una dependencia no demuestra que el sistema detecte ciclos o valide automáticamente su cumplimiento.

#### Orquestación
Coordinación de trabajo distribuido por un rol con autoridad explícita: ordenar, asignar, priorizar dentro de mandato, gestionar dependencias e integrar resultados.

**Estado:** vigente 1.1.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; docs/architecture/task-centric-coordination.md.  
**Límite:** orquestar no equivale a ejecutar cada tarea ni sustituye la responsabilidad de cada owner.

#### Coordinación sistémica
Responsabilidad transversal de preservar coherencia entre tareas, contratos, permisos, interfaces, dependencias y evolución. Softly 1.1 la declara transversal, no una cuarta dimensión.

**Estado:** vigente como responsabilidad; alcance fino abierto.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; CHECKPOINT.md; docs/architecture/task-centric-coordination.md.  
**Límite:** su relación exacta con orquestación y con un eventual rol DIR sigue sin resolverse.

#### Entregable
Resultado asociado a una tarea, acompañado de verificaciones, evidencia, referencias, limitaciones y estado de aceptación.

**Estado:** contractual vigente.  
**Fuente:** gatoscientist/Softly, contracts/entregable.md.  
**Límite:** existencia de archivo, commit o enlace no demuestra calidad ni aceptación.

#### Checkpoint
Resumen compacto del estado vigente, acuerdos que afectan la acción presente, bloqueos y próxima acción habilitada. No es una bitácora cronológica.

**Estado:** contractual vigente.  
**Fuente:** gatoscientist/Softly, contracts/checkpoint.md.  
**Límite:** no debe duplicar el contenido completo de las tareas ni convertirse en un archivo histórico acumulativo.

#### Handoff
Transferencia documental de contexto y responsabilidad operativa entre participantes. En Softly 1.1 no es una quinta clase física de artefacto ni crea una sesión o autoridad por sí mismo.

**Estado:** mecanismo heredado/documentado; no clase física canónica de 1.1.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; schemas/handoff.schema.json; plantilla histórica.  
**Límite:** su necesidad futura depende de si la tarea y el entregable expresan suficientemente el traspaso.

### 5. Conocimiento y evidencia

#### Fuente
Artefacto primario o secundario del que se obtiene información: documento, repositorio, publicación, mensaje autorizado, evento, medición o registro. La fuente puede ser parcial, errónea o sesgada.

**Estado:** método de investigación documentado.  
**Fuentes:** gatoscientist/Softly, docs/research-method.md; docs/architecture/knowledge-domain-model.md.  
**Límite:** fuente no equivale a verdad ni a evidencia suficiente para cualquier afirmación.

#### Registro
Representación persistida de un dato, evento, observación o artefacto con identidad y procedencia. Puede ser una captura derivada de una fuente, no necesariamente el original.

**Estado:** modelo conceptual.  
**Fuente:** gatoscientist/Softly, docs/architecture/knowledge-domain-model.md.  
**Límite:** conviene no usar «fuente/registro» como una sola categoría si se necesita distinguir original de copia o captura.

#### Afirmación
Proposición delimitada acerca de una entidad, concepto, actividad o relación. Puede recibir evidencia favorable, contradictoria o insuficiente.

**Estado:** modelo conceptual propuesto.  
**Fuente:** gatoscientist/Softly, docs/architecture/knowledge-domain-model.md.  
**Límite:** el tipo de afirmación (hecho, observación, inferencia, hipótesis, resultado, decisión, recomendación) no es lo mismo que su nivel de confianza o estado de revisión.

#### Evidencia
Dato o registro verificable que respalda, contradice o matiza una afirmación. Su valor depende de procedencia, integridad, método, contexto y pertinencia.

**Estado:** vigente como requisito de investigación y entregables.  
**Fuentes:** gatoscientist/Softly, contracts/entregable.md; docs/research-method.md.  
**Límite:** una referencia citada sin comprobar su contenido puede ser una pista, no evidencia suficiente.

#### Procedencia
Información que permite reconstruir de dónde viene un registro, quién o qué lo produjo o incorporó y mediante qué proceso.

**Estado:** principio transversal documentado.  
**Fuentes:** gatoscientist/Softly, docs/architecture/knowledge-domain-model.md; docs/research-method.md.  
**Límite:** autoría Git no demuestra por sí sola qué agente ejecutó una acción ni quién la decidió.

#### Contexto
Condiciones que delimitan la interpretación y validez de una afirmación o resultado: proyecto, universo, versión, periodo, configuración, permisos y condiciones de observación.

**Estado:** modelo conceptual propuesto.  
**Fuente:** gatoscientist/Softly, docs/architecture/knowledge-domain-model.md.  
**Límite:** no trasladar conclusiones entre contextos sin justificar equivalencia.

#### Síntesis
Representación derivada que organiza afirmaciones para responder una pregunta o apoyar una tarea. Debe preservar cobertura, incertidumbre, desacuerdos y referencias a las fuentes.

**Estado:** método de investigación documentado.  
**Fuentes:** gatoscientist/Softly, docs/architecture/knowledge-domain-model.md; docs/research-method.md.  
**Límite:** no sustituye la fuente primaria ni debe convertir inferencias en hechos por compresión.

#### Calibración
Evaluación cualitativa del respaldo de una afirmación. El método de Softly propone categorías como verificada, corroborada, plausible, disputada, refutada y no evaluada.

**Estado:** método documentado.  
**Fuente:** gatoscientist/Softly, docs/research-method.md.  
**Límite:** no asignar porcentajes de confianza sin un método definido; tampoco confundir calibración con tipo epistemológico.

#### Experimento
Actividad diseñada para contrastar una hipótesis bajo condiciones explícitas, con configuración, casos, variables, criterios, resultados y limitaciones registrados.

**Estado:** método documentado; cada experimento requiere autorización y ejecución efectiva.  
**Fuente:** gatoscientist/Softly, docs/research-method.md.  
**Límite:** un protocolo escrito no es un experimento ejecutado; un resultado aislado no demuestra generalidad.

### 6. Estigmergia y ciclo de vida de información

#### Medio compartido
Entorno que los participantes pueden observar y modificar, y cuyas modificaciones pueden influir en acciones posteriores. Puede incluir artefactos, registros y estados de trabajo.

**Estado:** concepto de investigación, no arquitectura aprobada.  
**Fuente:** gatoscientist/SoftlyLab, Estigmergia-Deliberacion-Softly-2.0.md.  
**Límite:** un repositorio compartido es un candidato a medio; no demuestra que los participantes lo consulten o coordinen a través de él.

#### Traza
Cambio observable en el medio producido por una acción. Puede ser intencional o un subproducto no dirigido a comunicar. Para ser útil en una explicación estigmérgica debe poder atribuirse y ser perceptible en el contexto estudiado.

**Estado:** concepto respaldado por la investigación revisada; aplicación a Softly como hipótesis.  
**Fuentes:** gatoscientist/SoftlyLab, Estigmergia-Deliberacion-Softly-2.0.md; Katarina-Deliberacion-Independiente-Estigmergia-2026-11-17.md.  
**Límite:** una traza no tiene por qué ser una instrucción ni una señal intencional.

#### Señal
Representación o marca que se ofrece para que un participante la interprete. Puede codificar estado, prioridad, procedencia o una propuesta de acción.

**Estado:** concepto analítico; contrato Softly pendiente.  
**Fuente:** inferencia de contraste entre investigación estigmérgica y contratos actuales.  
**Límite:** no toda traza es señal intencional. Llamar «señal» a todo cambio del repositorio borraría la distinción entre subproducto y comunicación diseñada.

#### Percepción y adopción causal
Proceso por el cual un participante encuentra una traza o señal, la interpreta y modifica su conducta a causa de ella. Es la condición observable que permite distinguir coordinación estigmérgica de mera persistencia documental.

**Estado:** criterio analítico propuesto para evaluación.  
**Fuente:** deliberación independiente de Katarina sobre estigmergia.  
**Límite:** una coincidencia temporal entre lectura y acción no prueba causalidad; hay que descartar instrucciones previas, asignación explícita y fuentes alternativas.

#### Estigmergia
Forma de coordinación indirecta mediada por cambios en un entorno compartido: una acción deja una traza que influye en acciones posteriores de otros participantes o del mismo participante.

**Estado:** concepto científico; aplicación a Softly 1.1 como hipótesis de mecanismo.  
**Fuentes:** investigación de estigmergia revisada en SoftlyLab; gatoscientist/Softly, SOFTLY.md y CHECKPOINT.md para la declaración de GitHub como superficie de señales.  
**Límite:** que GitHub conserve señales no demuestra que Softly haya implementado coordinación estigmérgica efectiva. Debe observarse la cadena acción → cambio del medio → percepción/interpretación → cambio conductual.

#### Estigmergia cognitiva
Coordinación mediada por artefactos interpretables por participantes capaces de razonar, planificar y actuar según metas. La señal puede estar en el propio estado del trabajo, no solo en un marcador añadido.

**Estado:** concepto de investigación; aplicación a Softly propuesta.  
**Fuente:** gatoscientist/SoftlyLab, Estigmergia-Deliberacion-Softly-2.0.md.  
**Límite:** no exige adoptar middleware específico ni multiplicar agentes; puede investigarse incluso con un agente y herramientas.

#### Vigencia operativa
Condición temporal o contextual por la que una señal sigue siendo pertinente para orientar trabajo presente.

**Estado:** propuesta de diseño.  
**Fuente:** deliberación gAto–Softly–Katarina registrada en gatoscientist/Softly, CHECKPOINT.md.  
**Límite:** no es lo mismo que retención histórica. Una señal puede dejar de estar vigente sin que su evidencia deba borrarse.

#### Caducidad
Fin de la vigencia de una señal por tiempo o condición predefinida. No implica que la señal haya sido falsa o reemplazada.

**Estado:** propuesta; regla de expiración pendiente.  
**Fuente:** deliberación registrada en gatoscientist/Softly, CHECKPOINT.md.  
**Límite:** no establecer TTL universal sin conocer el tipo de señal, su riesgo y su uso.

#### Reemplazo
Relación en la que una señal nueva asume la función operativa de una señal anterior. La anterior puede haber sido correcta en su momento.

**Estado:** distinción propuesta.  
**Fuente:** contraste conceptual de Katarina.  
**Límite:** reemplazo no equivale a invalidación.

#### Invalidación
Determinación de que una señal o afirmación no debe seguir usándose para el propósito declarado, por error, contaminación, falta de integridad u otra causa documentada.

**Estado:** distinción propuesta; criterios pendientes.  
**Fuente:** contraste conceptual de Katarina.  
**Límite:** no confundir invalidación con simple antigüedad.

#### Memoria documental
Conjunto persistente de documentos, decisiones, registros y evidencias que permite reconstruir trabajo y continuidad.

**Estado:** declarativo vigente.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; CHECKPOINT.md.  
**Límite:** no equivale a contexto activo de una sesión ni garantiza recuperación automática.

#### Archivo histórico inactivo
Material conservado por procedencia, genealogía o auditoría que no participa del arranque ni gobierna la operación actual. Se consulta bajo demanda.

**Estado:** vigente como clasificación de legado.  
**Fuentes:** gatoscientist/Softly, SOFTLY.md; archive/v1.0-legacy/README.md.  
**Límite:** «inactivo» no significa inútil, falso o autorizado para borrar.

### 7. Git y reversibilidad

#### Commit
Objeto de Git que registra un cambio sobre un árbol de archivos y enlaza con su historia. Es evidencia de persistencia de una modificación en el repositorio.

**Estado:** concepto técnico vigente.  
**Fuente:** uso y reglas de trazabilidad en gatoscientist/Softly, SOFTLY.md.  
**Límite:** un commit no prueba por sí solo quién tomó la decisión, qué proceso produjo el cambio, que el resultado sea correcto ni que otro agente lo haya leído.

#### Rama
Referencia móvil a una línea de commits, útil para aislar cambios y comparar alternativas antes de integrarlas.

**Estado:** concepto Git vigente; política experimental de Softly pendiente.  
**Fuentes:** Git; antecedentes de gobernanza conservados en Softly.  
**Límite:** crear una rama no vuelve reversible cualquier efecto externo. La reversibilidad depende también de datos, credenciales, servicios y efectos no versionados.

#### Reversibilidad
Propiedad de una intervención por la que puede abandonarse o deshacerse sin perder activos protegidos ni dejar efectos residuales no controlados.

**Estado:** criterio de diseño propuesto para experimentos.  
**Fuente:** deliberación actual sobre experimentación y ramas.  
**Límite:** revertir un commit no revierte automáticamente acciones externas, publicaciones, notificaciones, consumo de recursos o filtraciones.

---

## C. Conceptos ausentes o insuficientemente desarrollados en la propuesta de Softly

No afirmo que estos conceptos sean universalmente obligatorios. Los incluyo porque sin ellos sería difícil diseñar y evaluar Softly 2 sin ambigüedades.

1. **Instancia de agente:** separa definición portable, realización concreta y sesión temporal. «Agente» solo puede ocultar diferencias importantes de configuración.
2. **Herramienta frente a capacidad:** la capacidad es lo que puede hacerse; la herramienta es una interfaz concreta para hacerlo. Esta separación es esencial para evaluar AgenteDIR y el minimalismo.
3. **Adopción causal de una traza:** falta una condición operacional que separe persistencia, lectura y coordinación efectiva.
4. **Permiso efectivo y enforcement:** son necesarios para no atribuir a prompting controles que el entorno no aplica.
5. **Atribución:** quién o qué produjo una traza no siempre coincide con autoría Git, identidad declarada o autoridad que aprobó el cambio.
6. **Estado autoritativo frente a estado observado:** un agente puede observar un archivo o propuesta que no es la fuente vigente de verdad. La visibilidad no basta para convertirlo en estado oficial.
7. **Línea base experimental:** toda comparación necesita una alternativa de referencia. Sin ella no puede medirse si la complejidad adicional aporta valor.
8. **Costo total:** no solo tokens; incluye latencia, traspasos, retrabajo, supervisión, fallos, mantenimiento y atención humana.
9. **Causalidad y contaminación experimental:** una acción posterior puede provenir de instrucción explícita o contexto previo, no de una traza.
10. **Reversibilidad real:** una rama Git no basta cuando hay efectos fuera del repositorio.
11. **Criterio de detención/cierre:** evita que una deliberación se convierta en una secuencia indefinida de subtareas o reformas.
12. **Calidad de aceptación:** separa revisión del productor, verificación independiente y aceptación por autoridad competente.

---

## D. Definiciones cuestionadas o que requieren ajuste

### D.1 «Softly» como una definición única y cerrada
La propuesta de Softly privilegia la definición de núcleo operativo y generativo de SOFTLY.md y presenta la matriz generativa como formulación anterior. Sin embargo, docs/operating-model.md está en el árbol operativo actual y afirma explícitamente que Softly es una matriz generativa/sistema autoevolutivo y no un agente individual ni una instancia coordinadora separada.

**Mi posición:** no se debe resolver esto mediante precedencia automática sin aclarar si «matriz» y «núcleo» describen niveles diferentes o definiciones incompatibles. El glosario debe registrar la diferencia.  
**Estado:** discrepancia editorial/conceptual pendiente, no contradicción necesariamente irreconciliable.

### D.2 «Señal estigmérgica» como cualquier registro o cambio que comunica estado
Esta formulación puede mezclar una traza accidental con un marcador diseñado para comunicar. En estigmergia, una modificación del entorno puede influir en acciones posteriores sin haber sido creada como mensaje intencional.

**Mi posición:** distinguir traza, señal intencional e interpretación/adopción. La clasificación no requiere tres subsistemas; requiere precisión al describir el mecanismo.

### D.3 «Estigmergia» aplicada a GitHub
La declaración de GitHub como superficie de señales es vigente en Softly 1.1, pero no demuestra que exista estigmergia efectiva.

**Mi posición:** describirlo como superficie potencialmente estigmérgica o mecanismo declarado, y reservar «coordinación estigmérgica observada» para casos donde se compruebe la cadena causal.

### D.4 «Vigencia / tiempo de vida»
La propuesta junta vigencia y tiempo de vida como si fueran equivalentes. La vigencia puede depender de un evento, condición o cambio de estado, no solo de un plazo.

**Mi posición:** usar «vigencia operativa» como concepto general; TTL como mecanismo opcional de expiración temporal, no como definición de vigencia.

### D.5 «Demonio de Síntesis»
El nombre presupone un agente dedicado, aunque la función podría resolverse mediante una rutina, herramienta, regla o responsabilidad integrada.

**Mi posición:** definir primero la función de gestión de vigencia/archivo. No introducir una identidad de agente hasta demostrar que requiere autonomía propia.

### D.6 «Tarea fractal»
La expresión describe una preocupación real del gAto, pero «fractal» puede sugerir una propiedad matemática que no está definida ni medida.

**Mi posición:** conservarla como etiqueta coloquial de deliberación si resulta útil, pero definir operacionalmente el fenómeno como expansión recursiva no solicitada del alcance. No elevarla todavía a concepto arquitectónico.

### D.7 «Agente DIR»
La propuesta lo deja pendiente, correctamente, pero conviene no anticipar que sea un agente distinto de un rol de dirección. El nombre no determina su ontología.

**Mi posición:** mantener la pregunta abierta: ¿identidad autónoma, rol institucional, función de orquestación o combinación? La respuesta debe derivarse de responsabilidades, autonomía, autoridad y ciclo de vida.

### D.8 «Cápsula Directora»
El término está respaldado por SOFTLY.md y CHECKPOINT.md como forma de trabajo interno de Katarina. No obstante, su redacción puede inducir a pensar que existen especialistas autónomos separados.

**Mi posición:** describirla como mecanismo interno de distribución de análisis o subcontratos cognitivos, con responsabilidad e integración conservadas por Katarina. No contar cada lente como agente.

### D.9 «Estado vigente» como una sola categoría
La propuesta usa «vigente 1.1» para contratos, principios, modelos conceptuales y mecanismos documentados. Esto puede sugerir que todo tiene la misma fuerza.

**Mi posición:** separar vigencia documental de fuerza normativa y de evidencia de implementación. Un concepto puede estar documentado y no ser contractual; un contrato puede estar vigente sin enforcement técnico.

### D.10 Estados de tarea
Los documentos consultados no presentan una lista idéntica de estados. La plantilla contracts/tarea.md enumera estados distintos de los que aparecen en docs/architecture/task-centric-coordination.md y el schema mencionado allí.

**Mi posición:** conservar la discrepancia visible y remitirla a revisión contractual posterior. No normalizar el glosario escogiendo una lista por intuición.

---

## E. Conceptos que fusionaría, reduciría o dejaría fuera

1. **No crear entradas separadas para «Softly Fábrica», «Softly Coordinadora» y «Softly deliberativa» como identidades.** En la evidencia revisada son una propuesta de tres modos/instancias, no una arquitectura aprobada. Mantener «modo de trabajo» y registrar «Tres Softlys» como hipótesis pendiente.
2. **No crear una entrada autónoma para «Demonio de Síntesis» todavía.** La función de gestión de vigencia puede describirse sin presuponer un agente. Reabrir la clasificación solo si se demuestra autonomía necesaria.
3. **No mantener «señal caducada», «señal reemplazada» e «invalidada» como tres grandes subsistemas.** Mantenerlas como tres resultados distintos del ciclo de vida de una señal, porque tienen consecuencias diferentes: fin temporal, sustitución funcional y pérdida de validez.
4. **No duplicar «Fábrica / Entrega Directa» como modo y como proceso completo si la definición es la misma.** El modo indica intención operativa; el flujo describe pasos. Son niveles distintos, pero no necesitan entradas extensas duplicadas.
5. **No elevar «casa canónica» a concepto central de Softly 2.** Es un término útil de organización documental, pero su definición no parece necesaria para evaluar coordinación, agencia o estigmergia. Puede permanecer en documentación de repositorios.
6. **No mantener «inbox/outbox» como conceptos positivos del glosario principal.** Basta con una nota de diseño: son vistas lógicas derivadas, no artefactos físicos de 1.1.
7. **No incorporar todos los términos históricos de canales say/ como entradas principales.** Referenciarlos en la nota de legado, sin cargar el vocabulario activo.
8. **Fusionar «fuente/registro» solo en el índice de familias, no en la definición.** Son cercanos, pero fuente original y registro derivado no siempre son lo mismo; conservar una distinción breve evita perder procedencia.
9. **Mantener separadas autoridad, permiso efectivo y enforcement.** No son redundantes: una define quién puede decidir, otra qué acceso existe y la tercera qué control técnico aplica la regla.
10. **Mantener separadas capacidad, herramienta y agente.** Fusionarlas simplificaría el texto a costa de confundir el diseño minimalista con la eliminación de modularidad.

---

## F. Vocabulario crítico para investigar Softly 2

No propongo que todos estos términos se conviertan en contratos. Son el vocabulario mínimo que considero útil para formular hipótesis, comparar alternativas y evaluar resultados.

### F.1 Arquitectura mínima
- Agente, instancia, sesión.
- Herramienta, capacidad, subagente.
- Rol, responsabilidad, autoridad.
- Permiso efectivo y enforcement.
- Definición, asignación y contexto.

Con ellos se puede preguntar si una función necesita autonomía propia o basta con una herramienta.

### F.2 Coordinación observable
- Tarea, responsable, dependencia y aceptación.
- Medio compartido, traza, señal.
- Percepción, interpretación y adopción causal.
- Estado autoritativo y estado observado.
- Orquestación y coordinación sistémica.

Con ellos se puede comprobar si el entorno coordina realmente o solo almacena información.

### F.3 Memoria y vigencia
- Memoria documental y contexto activo.
- Procedencia y atribución.
- Vigencia operativa, caducidad, reemplazo e invalidación.
- Archivo histórico y retención.

Con ellos se puede reducir contexto rutinario sin borrar evidencia ni confundir lo antiguo con lo falso.

### F.4 Evaluación y aprendizaje
- Hipótesis, experimento, línea base y resultado.
- Calidad, costo total y carga de atención humana.
- Reversibilidad, contaminación y causalidad.
- Verificación independiente y aceptación.

Con ellos se puede medir si una arquitectura más simple conserva calidad y si una coordinación basada en trazas produce una mejora real.

**Criterio experimental central:** comparar la configuración mínima capaz de resolver una tarea con alternativas más complejas, bajo condiciones equivalentes. Medir calidad y completitud, tiempo, costo, contexto, traspasos, retrabajo, errores, intervenciones humanas, auditabilidad y mantenimiento. No asumir que una mejora en una métrica compensa cualquier degradación en otra.

---

## G. Incertidumbres y decisiones pendientes

### G.1 Incertidumbres que la evidencia consultada no resuelve
- Si «matriz generativa» y «núcleo operativo/generativo» describen niveles complementarios o una diferencia real de identidad.
- Qué criterios observables separarán agente, subagente y herramienta en casos límite.
- Si las trazas actuales de GitHub son consultadas de manera suficientemente regular y causal para producir coordinación estigmérgica.
- Qué señales necesitan marcador explícito y cuáles pueden ser sematectónicas, es decir, derivarse del propio estado del trabajo.
- Cómo medir la contribución de una señal frente a instrucciones, asignaciones o contexto previos.
- Qué mecanismo de caducidad resulta seguro para cada tipo de señal.
- Si el rol DIR requiere identidad autónoma o puede expresarse como rol/función.
- Si los tres modos propuestos para Softly requieren instancias separadas o solo configuración contextual.
- Qué vocabulario de estados de tarea debe prevalecer después de una reconciliación contractual.
- Qué resultados de AgenteDIR están medidos; DR-09 registra la descripción del gAto, no una auditoría experimental de su implementación.

### G.2 Decisiones de diseño pendientes
- Definir si el glosario final tendrá una sola capa breve o un núcleo más un apéndice histórico.
- Determinar qué estados documentales y tipos epistemológicos serán compartidos.
- Establecer el mínimo de metadatos para atribución, procedencia y vigencia de señales.
- Definir qué acciones pueden sugerirse por una traza y cuáles requieren asignación u orden explícita.
- Determinar qué cambios de estado deben ser autoritativos y quién puede producirlos.
- Elegir el experimento mínimo que permita evaluar estigmergia sin confundirla con coordinación explícita.
- Definir la línea base y el criterio de complejidad mínima suficiente para las comparaciones de arquitectura.

### G.3 Límites de esta investigación
- Se revisaron los documentos de arranque y checkpoint de Softly 1.1; el modelo operativo; los contratos de paquete, tarea, entregable y checkpoint; los documentos de coordinación task-centric, conocimiento, método de investigación, anatomía y modelo de agentes; taxonomías y catálogo; y la rectificación de limpieza estigmérgica.
- En SoftlyLab se revisaron la propuesta de glosario, la síntesis de investigación sobre estigmergia, la deliberación independiente de Katarina y DR-07, DR-08 y DR-09.
- En ResKata se revisaron identidad, contrato, perfil, permisos, principios de ingeniería, especialidad Softly y handoff de estigmergia de Katarina 0.2.0-experimental.
- Se inspeccionaron los árboles de archivos de los tres repositorios para identificar fuentes pertinentes. No se leyó línea por línea cada transcripción histórica, cada archivo del repositorio ni cada artefacto binario. No se leyó DR-06, conforme al encargo.
- No se realizó una nueva revisión bibliográfica externa: el objetivo fue contrastar los materiales disponibles, no abrir una investigación científica paralela.
- La documentación de Softly describe en parte modelos y procedimientos declarativos. No se verificó la ejecución real de cada capacidad, ni se ejecutaron experimentos.
- No se modificaron gatoscientist/Softly, el glosario de Softly, contratos, schemas, permisos ni arquitectura.

---

## Referencias documentales principales

### gatoscientist/Softly
- SOFTLY.md — SHA 25a6ee8eb277983440d11f285573fca674e8b4f5.
- CHECKPOINT.md — SHA f2ff751996d963d4ecf096df8e7fcaed3d3d636f.
- docs/operating-model.md — SHA 893f3fe89d29c9ba630686bf63af4f0c30b2b26e.
- docs/architecture/task-centric-coordination.md — SHA c485aed4c48d743bf1fb449fe3583cdb50b44353.
- docs/architecture/knowledge-domain-model.md — SHA 85d368789f920ddea29882d001942f2499f4633c.
- docs/research-method.md — SHA 3196cff8a46f904eecd51ad6ed6175a36ac6f059.
- docs/architecture/agent-model-v0.1.md — SHA 57d71101e50bd000b72bcfc0c78c7fb2a1ae3483.
- docs/architecture/agent-anatomy.md — SHA 2da4e7d9688d86a8ded9204d131a066824d0d96a.
- docs/architecture/taxonomy-and-mold-validation.md — SHA 85f2f93923964486d49cfd77093456df9db0db9b.
- contracts/paquete.md — SHA 54cc5eb8fda8133bdcc29bf5e4f9f58d11e99ed2.
- contracts/tarea.md — SHA 72df4dc15604ffae83d37a3684257d2dc9ec3d34.
- contracts/entregable.md — SHA 0d93c1ee38ffbc3ad81be0cc3561144870ab4dd3.
- contracts/checkpoint.md — SHA 2f7afedfb46fc1b157d660357fbde4202008f739.
- docs/governance/RECTIFICACION-HANDOFF-LIMPIEZA-ESTIGMERGICA-2026-11-16.md — SHA 76fcabed4e4a820adfc24369e71bbc0ab78fab80.

### gatoscientist/SoftlyLab
- Glosario-Tecnico-Propuesta-Softly-2026-11-17.md — SHA 774809ec0de703107263191bf133bef61332a5e8.
- Estigmergia-Deliberacion-Softly-2.0.md — SHA 4364bc1664f6690ac75d8bf5dff973d9e995509e.
- Katarina-Deliberacion-Independiente-Estigmergia-2026-11-17.md — SHA 39eef8242502df2f04f974a4256bb2d86845eb59.
- DR-07, DR-08 y DR-09: investigación y deliberación complementaria; no normativa ni implementada.

### gatoscientist/ResKata
- Katarina/core/AGENT.md — SHA c2b4cdb80c84dca0fb4d9c57574113756c59006e.
- Katarina/core/CONTRACT.md — SHA 3a6c30e34dc40273e90a8428fc20da5e643a1ad5.
- Katarina/core/PERMISSIONS.md — SHA 25e8a58e32945b598ca16905c8ee0b7f2593118e.
- Katarina/core/PROFILE.md — SHA 1290bc03bd70a2fa9b8363509756cd890c05cfea.
- Katarina/core/instructions/engineering-principles.md — SHA 1b910b55496c8d42202987b23c73af470f813ef4.
- Katarina/core/expertise/softly-ecosystem.md — SHA a3cb80b99d017d93ad1377948880efe0fe90bc40.
- Katarina/shared/2026-11-17-handoff-estigmergia-deliberacion.md — SHA 20fb69552f6f56cbc2c510cbcd255c8a407f305f.

---

## Conclusión

La propuesta independiente no intenta aumentar el vocabulario por sí mismo. Su prioridad es impedir cuatro confusiones costosas: capacidad frente a agente; persistencia frente a coordinación; influencia informativa frente a autoridad; y diseño declarado frente a comportamiento demostrado.

Para Softly 2, el vocabulario debe permitir formular experimentos pequeños y refutables. Si un término no ayuda a distinguir una decisión, una responsabilidad, un mecanismo o una medición, probablemente no necesita una entrada propia.

**Este documento es una posición independiente para contraste. No cierra la deliberación, no declara terminado el glosario y no autoriza la construcción de Softly 2.**
