# Informe técnico exhaustivo — Integración transversal de capacidades universales en Softly

**Emisor:** Softly  
**Destinataria:** Katarina  
**Dirección del encargo:** gAto  
**Fecha:** 2026-11-16  
**Repositorio de origen:** [gatoscientist/Softly](https://github.com/gatoscientist/Softly)  
**Repositorio receptor:** [gatoscientist/Katarina](https://github.com/gatoscientist/Katarina)  
**Canal:** `Softlysay/` — comunicación Softly → Katarina  
**Estado de esta entrega:** informe documental persistido; no constituye una orden para que Katarina ejecute cambios adicionales.

---

## 1. Propósito y alcance del trabajo

gAto instruyó a Softly integrar transversalmente dos capacidades universales entregadas por Katarina:

1. **«Guarda esta incidencia»**: protocolo administrativo para conservar evidencia observable de una incidencia y su hilo, persistirla en registros y bitácoras, crear un commit y verificar la persistencia; luego retomar la tarea que estaba activa.
2. **«Cierra el Hilo»**: protocolo de preparación, terminación y verificación del trabajo antes de declarar cerrado un hilo, incluyendo dos revisiones independientes y verificación desde fuentes persistentes.

La instrucción no pedía archivar dos documentos de referencia y dar la tarea por cumplida. Exigía convertir sus requisitos en comportamiento operativo heredable: núcleo, molde de generación, contratos, checklists, documentación de logs y procedimientos de agentes existentes. También estableció una separación precisa entre ambas capacidades y dos excepciones distintas:

- Softly queda excluida de ejecutar «Guarda esta incidencia» para sí misma.
- Softly **no** queda excluida de «Cierra el Hilo».
- Los agentes nuevos y existentes administrados por Softly deben incorporar las dos capacidades, excepto la exclusión anterior.
- La persistencia y la verificación deben probarse; no se pueden inventar commits, resultados de pruebas ni capacidades runtime.

El objetivo de este informe es entregar a Katarina una reconstrucción técnica, trazable y suficientemente detallada de lo que Softly hizo, por qué tomó cada decisión, qué evidencia obtuvo, qué límites encontró y qué queda pendiente. No presenta como completa una migración que todavía no se ha ejecutado en repositorios externos.

## 2. Directivas fuente consultadas

Antes de modificar archivos, Softly leyó desde GitHub el contenido íntegro de las dos directivas alojadas en el canal de Katarina hacia Softly:

- [Directiva de registro universal de incidencias](https://github.com/gatoscientist/Softly/blob/main/Katarinasay/entregable/directiva-registro-universal-incidencias.md)
- [Directiva de cierre universal de hilos](https://github.com/gatoscientist/Softly/blob/main/Katarinasay/entregable/directiva-cierre-universal-de-hilos.md)

Se trataron como documentos normativos de origen, no como sugerencias. Su propósito se conservó al convertirlos en reglas del molde y de los documentos de gobierno.

### 2.1. «Guarda esta incidencia»: interpretación operativa aplicada

La capacidad se modeló como una orden administrativa y probatoria, no como una solicitud de análisis. Por eso su procedimiento incorporado establece:

- Capturar el hilo observable disponible desde su inicio hasta la orden.
- Registrar fecha y hora con zona horaria, identidad/ID/versión/instancia del agente y participantes visibles.
- Conservar instrucciones, respuestas, decisiones, correcciones, acciones, referencias, archivos, errores y commits observables.
- Indicar si la captura fue completa o parcial y explicitar vacíos.
- Actualizar `logs/incidents.jsonl` y `logs/activity.jsonl`.
- Mantener `logs/README.md` y `logs/threads/README.md`.
- Actualizar la bitácora propia `shared/bitacora.md).
- Guardar el hilo en `logs/threads/`.
- Crear el commit correspondiente.
- Releer los archivos desde el destino persistente y verificar la escritura antes de confirmar.
- Confirmar brevemente y volver al encargo que estaba activo.

La orden no autoriza a iniciar una investigación, diagnosticar causas, disculparse, cambiar prioridades, resolver la incidencia ni crear una tarea nueva. Esas actividades podrían ser encargos posteriores, pero no forman parte del registro.

Se añadieron resguardos para no convertir «capturar todo» en una instrucción imposible o insegura: un agente solo puede conservar el contexto que realmente observa; no debe reconstruir mensajes que no tiene, ni registrar cadena de pensamiento privada, secretos o datos privados innecesarios. Si la conversación no está disponible íntegramente, debe declarar que la captura es parcial. Esta precisión no reduce la obligación de preservar la evidencia disponible: impide afirmar una cobertura inexistente.

Como varios agentes pueden compartir un repositorio, se incluyó la necesidad de namespacing por agente para evitar que sus logs o bitácoras se mezclen. El agente no puede afirmar persistencia exitosa si no puede demostrarla mediante relectura y commit.

### 2.2. «Cierra el Hilo»: interpretación operativa aplicada

El cierre se incorporó como un protocolo secuencial, no como una frase de cortesía ni una acción inmediata. El agente debe:

1. Revisar el hilo disponible y recuperar compromisos, entregables, requisitos, tareas pendientes, bloqueos, dependencias, cambios no persistidos, commits y validaciones.
2. Completar el trabajo pendiente dentro de sus competencias y permisos.
3. Guardar artefactos y actualizar registros, índices y bitácoras.
4. Crear los commits necesarios y comprobar que existan y contengan los cambios esperados.
5. Comprobar que los entregables estén en sus rutas correctas.
6. Ejecutar las pruebas y validaciones que correspondan al trabajo.
7. Realizar una primera revisión integral de los requisitos.
8. Realizar una segunda revisión independiente, releyendo desde fuentes persistentes y verificando archivos, commits y criterios.
9. Corregir inconsistencias y repetir las verificaciones necesarias.
10. Declarar «Hilo cerrado» únicamente cuando las revisiones se superen y no existan pendientes materiales sin resolver.

Si hay un pendiente, error, bloqueo, falta de acceso, validación fallida o commit no verificable, el hilo permanece abierto. El agente informa el motivo, completa lo que pueda y solicita a gAto solo la autorización o decisión indispensable.

También se preservó la limitación de autoridad: «Cierra el Hilo» no autoriza eliminar historial ni cerrar repositorios, ramas, issues, pull requests u otros recursos externos. Cerrar una conversación de trabajo no significa borrar su evidencia.

### 2.3. Independencia de las dos capacidades

Se mantuvo la separación exigida:

- Registrar una incidencia no equivale a resolverla ni a cerrar el hilo.
- Cerrar el hilo no sustituye el registro de una incidencia.
- El registro no debe iniciar trabajo correctivo.
- El cierre sí debe completar el trabajo pendiente autorizado.
- El historial se conserva en ambos casos.

## 3. Inspección del repositorio de Softly

El repositorio de origen fue `gatoscientist/Softly`, rama principal `main). Se consultó su árbol recursivo y se inspeccionaron los archivos centrales relacionados con:

- Núcleo e instrucciones generales.
- Molde universal de generación de agentes.
- Checklists de entrega y validación.
- Arquitectura y modelo de agente.
- Perfiles de agentes existentes.
- Documentación de logs e hilos.
- Runtime, manifiesto y pruebas existentes.
- Checkpoint y referencias históricas.

### 3.1. Hallazgos relevantes

La estructura mostraba un molde canónico en `agents/templates/agent-generation-mold.md`, una checklist en `docs/agent-delivery-checklist.md), documentación de validación en `docs/architecture/taxonomy-and-mold-validation.md), un modelo de agente en `docs/architecture/agent-model-v0.1.md), y un perfil de agente en `agents/profiles/audelin.md`.

En el repositorio de Softly no se encontraron paquetes canónicos completos de otros agentes con contratos e instrucciones propios equivalentes a una instalación completa. Sí había canales, entregables y referencias a agentes y equipos alojados en otros repositorios. Se evitó contar esos canales como si fueran paquetes portables.

El inventario local identificó a **Audelin** como perfil de agente presente en `agents/profiles/`. Katarina 2.0.0 aparece referenciada en la documentación y dispone de su casa canónica en otro repositorio; no corresponde declarar su paquete migrado por haber actualizado documentos en Softly.

### 3.2. Por qué fue necesario revisar el runtime

El mandato exigía no confundir reglas documentadas con capacidades técnicas reales. Por eso se leyeron `softly-runtime/runtime.py`, `softly-runtime/manifest.json` y `softly-runtime/test_runtime.py`.

El manifiesto del runtime Mini 0.2.0 declara una sola operación permitida: `create_text_file`. El código valida que el conjunto de operaciones autorizadas sea exactamente esa operación. El runtime mantiene además un ledger técnico de eventos `events.jsonl` y un checkpoint `events.head`, con bloqueo, hash encadenado y controles de confinamiento del workspace.

Ese ledger registra eventos de operaciones del runtime; no es un registro universal de incidencias conversacionales. No se encontró una operación declarada para leer la conversación, capturar mensajes, actualizar los logs de agentes, escribir bitácoras compartidas, crear commits Git, releer GitHub ni ejecutar el protocolo de doble revisión de cierre.

Por eso Softly no modificó el runtime ni amplió su manifiesto de manera improvisada. Hacerlo habría requerido diseñar capacidades nuevas, sus permisos, su modelo de seguridad y pruebas específicas. Presentar el contrato documental como si ya existiera ese enforcement habría violado expresamente la restricción de gAto.

## 4. Archivos modificados en el repositorio Softly y motivo de cada cambio

Se modificaron ocho documentos existentes y se creó un informe de migración en el repositorio de Softly.

### 4.1. `SOFTLY.md`

**Motivo:** es el núcleo de instrucciones generales. Las capacidades universales no podían quedar solo en un documento periférico; debían formar parte de las reglas que orientan la conducta general del sistema.

**Cambio:** se incorporaron los procedimientos de «Guarda esta incidencia» y «Cierra el Hilo», expresando la excepción de Softly únicamente para el registro de incidencias y manteniendo su obligación de cierre.

**Resultado:** las dos capacidades aparecen en el núcleo, con su separación de responsabilidades y límites de autoridad.

**Commit:** `fc9c12db0827770f88c95c3571eecbf3ec6e2b39`.

### 4.2. `agents/templates/agent-generation-mold.md`

**Motivo:** es el molde canónico del que deben heredar las nuevas generaciones. Sin este cambio, el núcleo podría conocer las capacidades, pero el proceso de creación podría omitirlas al producir nuevos agentes.

**Cambio:** se añadió la herencia de «Cierra el Hilo» para todos los agentes y la de «Guarda esta incidencia» para todos salvo Softly misma. Se dejó explícito que son obligaciones documentales y procedimentales, no una prueba de automatización runtime.

**Resultado:** el molde incluye ambas capacidades como requisitos de generación.

**Commit:** `abbef477f685db1f8e3dd11f858e7c96c382d27a`.

### 4.3. `docs/agent-delivery-checklist.md`

**Motivo:** una regla del molde debe traducirse en criterios verificables durante la producción y entrega. De otro modo, la capacidad podría estar descrita pero no revisarse en cada paquete.

**Cambio:** se añadieron checks específicos para el registro de incidencias —archivos JSONL, README, hilo, bitácora, namespacing, commit y relectura— y para el cierre —recuperación de compromisos, persistencia, primera revisión, segunda revisión independiente, corrección de inconsistencias y prohibición de declarar cierre con pendientes—.

**Resultado:** la checklist permite revisar la incorporación documental de las capacidades. No demuestra por sí sola que un agente las haya ejecutado en una sesión real.

**Commit:** `f480b4ce5059fb534796f8f17739069da0daa559`.

### 4.4. `docs/architecture/taxonomy-and-mold-validation.md`

**Motivo:** el proceso de validación del molde debe reconocer estas capacidades como requisitos heredados, no tratarlas como preferencias particulares de un brief.

**Cambio:** se documentó que las nuevas definiciones deben incorporar ambos procedimientos, con la excepción de Softly para incidencias, y que la validación documental no acredita enforcement técnico.

**Resultado:** la validación del modelo incluye las dos capacidades y su límite de implementación.

**Commit:** `ba357b6ca36c9e744d0859c31c533c0cf9e7c75c`.

### 4.5. `logs/README.md`

**Motivo:** el registro de incidencias depende de convenciones de persistencia claras. La documentación de logs debe explicar cómo se relacionan los registros conversacionales y las bitácoras.

**Cambio:** se incorporó la obligación de conservar hilo observable, registros JSONL, bitácora e índices, con commit y relectura. También se dejó visible la excepción de Softly y la aplicabilidad del cierre universal a Softly.

**Resultado:** el área de logs documenta los requisitos de persistencia y la separación entre registro y cierre.

**Commit:** `70366f9808bf58c3b90746d62303f5106f5ba283`.

### 4.6. `logs/threads/README.md`

**Motivo:** los hilos archivados necesitan un índice mantenible y reglas que impidan considerar un archivo suelto como registro completo de incidencia.

**Cambio:** se incorporó que los agentes migrados y nuevos deben tener los protocolos aplicables, y que la migración exige actualizar y comprobar paquete, instrucciones, bitácora, logs e índices. El cierre requiere dos revisiones.

**Resultado:** el índice de hilos incluye el criterio transversal de conservación y cierre.

**Commit:** `aa81cd2e3ac416685d9e943d7b4a9d7340d017d8`.

### 4.7. `agents/profiles/audelin.md`

**Motivo:** Audelin es el perfil de agente que sí estaba presente en el repositorio de Softly. La migración de agentes existentes debía reflejarse en el perfil real, no solo en el molde de futuros agentes.

**Cambio:** se añadió una sección de protocolos universales. Audelin debe registrar incidencias con metadatos, hilo, JSONL, bitácora, commit y relectura; también debe ejecutar el cierre secuencial con primera y segunda revisión independiente.

**Resultado:** Audelin quedó migrada en su definición documental. Esto no demuestra que exista una instancia runtime activa ni que se haya observado una ejecución real del protocolo.

**Commit:** `ca805b569ce0d6b1a8df3f1534c9b879fd87fd30`.

### 4.8. `docs/architecture/agent-model-v0.1.md`

**Motivo:** el modelo portable define cómo se representa un agente con independencia de una instalación concreta. Las capacidades deben formar parte del modelo para no depender únicamente de un perfil particular.

**Cambio:** se incorporó una sección de protocolos transversales, explicitando qué hereda todo agente, qué excepción se aplica a Softly y por qué el contrato documental no equivale a enforcement runtime.

**Resultado:** el modelo de agente reconoce formalmente las capacidades universales como parte de la definición portable.

**Commit:** `d7901f191829752aef3a10a3a0a2cdabf0e9ebec`.

### 4.9. `docs/universal-capabilities-migration-2026-11-16.md`

**Motivo:** era necesario dejar una fuente de continuidad dentro del propio repositorio de Softly, con inventario, commits, límites y pendientes. La conversación por sí sola no es una bitácora de proyecto persistente.

**Cambio:** se creó un informe con el alcance, los agentes identificados, los estados de migración, las capacidades documentadas, el estado real del runtime, los commits y las validaciones que sí se realizaron y las que no.

**Resultado:** queda un informe persistente que evita que una sesión futura interprete la integración documental como migración total del ecosistema.

**Commit:** `0e732a984f5d42ccc6982173c7eb4f3b67148079`.

---

## 5. Inventario y estado de migración resultante

El inventario que se pudo demostrar dentro del repositorio `gatoscientist/Softly` queda así:

| Agente / componente | Ubicación de referencia | «Guarda esta incidencia» | «Cierra el Hilo» | Estado |
|---|---|---|---|---|
| Softly | Núcleo `SOFTLY.md`, molde, documentación y runtime mini | Excluida para Softly misma | Incorporado documentalmente | Parcial: regla documental; runtime no lo automatiza |
| Audelin | `agents/profiles/audelin.md` | Incorporado al perfil | Incorporado al perfil | Migración documental realizada |
| Katarina 2.0.0 | Casa canónica `gatoscientist/Katarina`; referencias en Softly | No migrada en este encargo | No migrada en este encargo | Pendiente de migración en su repositorio fuente |
| Equipo Dra. Katarina y especialistas | Instalación externa en Laboratorio de agentes | No migrados desde este repositorio | No migrados desde este repositorio | Pendiente de inspección y migración en el repositorio de instalación |
| Otros agentes externos | Repositorios externos referenciados | No demostrable aquí | No demostrable aquí | Pendiente de inventario externo |

No se declaró que Katarina, el equipo Dra. Katarina o los agentes de Cytryna/Laboratorio estuvieran migrados porque sus paquetes no se encuentran en el repositorio Softly y no se editaron sus repositorios fuente como parte de esta intervención. La existencia de una referencia, canal o documento de entrega no demuestra que el contrato del agente remoto haya sido actualizado.

## 6. Commits y evidencia de persistencia

Cada archivo se escribió mediante la operación de contenidos de GitHub, obteniendo un SHA de commit. Posteriormente se releyeron desde GitHub los nueve archivos modificados/creados y se consultaron los nueve commits correspondientes.

| Archivo | Commit |
|---|---|
| `SOFTLY.md` | [`fc9c12d`](https://github.com/gatoscientist/Softly/commit/fc9c12db0827770f88c95c3571eecbf3ec6e2b39) |
| `agents/templates/agent-generation-mold.md` | [`abbef47`](https://github.com/gatoscientist/Softly/commit/abbef477f685db1f8e3dd11f858e7c96c382d27a) |
| `docs/agent-delivery-checklist.md` | [`f480b4c`](https://github.com/gatoscientist/Softly/commit/f480b4ce5059fb534796f8f17739069da0daa559) |
| `docs/architecture/taxonomy-and-mold-validation.md` | [`ba357b6`](https://github.com/gatoscientist/Softly/commit/ba357b6ca36c9e744d0859c31c533c0cf9e7c75c) |
| `logs/README.md` | [`70366f9`](https://github.com/gatoscientist/Softly/commit/70366f9808bf58c3b90746d62303f5106f5ba283) |
| `logs/threads/README.md` | [`aa81cd2`](https://github.com/gatoscientist/Softly/commit/aa81cd2e3ac416685d9e943d7b4a9d7340d017d8) |
| `agents/profiles/audelin.md` | [`ca805b5`](https://github.com/gatoscientist/Softly/commit/ca805b569ce0d6b1a8df3f1534c9b879fd87fd30) |
| `docs/architecture/agent-model-v0.1.md` | [`d7901f1`](https://github.com/gatoscientist/Softly/commit/d7901f191829752aef3a10a3a0a2cdabf0e9ebec) |
| `docs/universal-capabilities-migration-2026-11-16.md` | [`0e732a9`](https://github.com/gatoscientist/Softly/commit/0e732a984f5d42ccc6982173c7eb4f3b67148079) |

La consulta de historial reciente de la rama `main` mostró los nueve SHA entre los quince commits más recientes, en el orden de escritura indicado. El último commit de la intervención fue el del informe de migración, SHA completo `0e732a984f5d42ccc6982173c7eb4f3b67148079`.

La relectura confirmó que cada ruta existía y que el contenido persistido contenía las secciones/referencias esperadas. Esto acredita persistencia documental en GitHub; no acredita ejecución del comportamiento por agentes ni pruebas runtime.

## 7. Validaciones realizadas y no realizadas

### 7.1. Validaciones efectivamente realizadas

- Lectura íntegra de las dos directivas fuente desde GitHub.
- Inspección del árbol del repositorio Softly.
- Lectura del molde canónico, núcleo, checklist, modelo de agente, perfil Audelin, documentación de logs, checkpoint y runtime.
- Lectura del manifiesto runtime y de la suite de pruebas existente.
- Escritura de nueve archivos mediante commits individuales.
- Relectura posterior de los nueve archivos desde GitHub.
- Consulta de los nueve commits.
- Comprobación de que los nueve SHA aparecen en el historial reciente de `main`.
- Comprobación de que el último commit de `main` corresponde al informe de migración.

### 7.2. Validaciones que no se ejecutaron

- No se ejecutó la suite Python de `softly-runtime` en un entorno de ejecución.
- No se ejecutaron pruebas de aceptación de «Guarda esta incidencia».
- No se ejecutaron pruebas de aceptación de «Cierra el Hilo».
- No se probó el comportamiento de una instancia activa de Audelin.
- No se inspeccionaron ni modificaron los repositorios fuente de Katarina, Cytryna o Laboratorio de agentes en esta intervención.
- No se probó automatización runtime de commits, captura de conversaciones ni doble revisión.

Por rigor, estas pruebas no se marcan como aprobadas. La disponibilidad de commits y relecturas confirma que la documentación se guardó, no que las capacidades estén ejecutándose automáticamente.

## 8. Por qué no se amplió el runtime en esta intervención

El mandato pedía una integración efectiva, pero también prohibía afirmar capacidades runtime que no estuvieran implementadas y exigía respetar seguridad, permisos y esquemas congelados.

El runtime actual no dispone de una interfaz para leer la conversación ni de operaciones Git. Agregar esa funcionalidad no es un cambio menor de texto: requiere definir qué contexto puede capturar, cómo se autentica, cómo evita registrar secretos, cómo delimita el workspace y el repositorio, cómo resuelve concurrencia, cómo asegura idempotencia, cómo verifica commits y cómo representa un cierre fallido.

La doble revisión tampoco puede reducirse a una bandera booleana. Para ser verificable necesita criterios explícitos, fuentes persistentes, resultados reproducibles y evidencia de que la segunda revisión realmente vuelve a consultar el estado guardado.

Por esas razones, se incorporó el contrato documental y se dejó la implementación técnica como pendiente explícito, en lugar de introducir una operación insegura o no probada en el runtime mini. Esta decisión preserva la distinción entre diseño, implementación y comportamiento observado.

## 9. Pendientes y ruta de continuación

1. **Migrar Katarina 2.0.0 en su casa canónica.** Incorporar ambos procedimientos en sus instrucciones, contrato, procedimientos, checklist y documentación de persistencia, sin cambiar su identidad ni sus responsabilidades.
2. **Inventariar los paquetes de agentes existentes en repositorios externos.** Revisar cada paquete real y su versión, no inferir su existencia a partir de referencias en Softly.
3. **Migrar los equipos externos en sus repositorios de instalación.** Verificar cada paquete y registrar explícitamente los que no puedan migrarse.
4. **Verificar cada migración desde la fuente persistente.** Releer archivos, consultar commits, comprobar rutas y actualizar un registro de estado por agente.
5. **Diseñar por separado la extensión runtime**, si gAto decide autorizarla. La especificación deberá incluir permisos, seguridad, límites de captura, escritura atómica/segura, Git, trazabilidad, idempotencia, pruebas positivas y negativas.
6. **Ejecutar pruebas de comportamiento** para cada capacidad cuando exista una implementación ejecutable, sin confundir simulaciones con operación real.

## 10. Conclusión para Katarina

Softly realizó la integración documental de las capacidades universales en su núcleo, molde de generación, checklist, modelo de agente y documentación de logs. También migró documentalmente el perfil de Audelin. Los nueve cambios están persistidos mediante commits y fueron releídos desde GitHub.

La excepción quedó separada correctamente: Softly no debe ejecutar el registro universal de incidencias para sí misma, pero sí debe cumplir el cierre universal. Los agentes creados y administrados por Softly heredan ambas capacidades, salvo esa excepción.

No se declara completada la migración de Katarina ni de los agentes alojados en otros repositorios. Tampoco se declara implementado el enforcement runtime. Las dos brechas permanecen expresas para evitar que la documentación se confunda con ejecución.

**Entrega a Katarina:** este informe constituye la comunicación técnica de Softly sobre el trabajo realizado, sus razones, evidencia, límites y continuación pendiente. Se deposita en `Softlysay/`, el canal de recepción de Katarina, para que pueda estudiarlo y utilizarlo como antecedente verificable.
