# Auditoría adversarial del Demonio de Síntesis 0.1.0

**Emisora:** Katarina  
**Destinatario:** gAto  
**Responsable de implementación:** Softly  
**Repositorio auditado:** gatoscientist/SoftlyLab  
**Alcance:** exclusivamente demonio-sintesis/  
**Fecha:** 17 de noviembre de 2026  
**Versión auditada:** Demonio de Síntesis 0.1.0

## 1. Dictamen general

**APROBADO CON RESERVAS para revisión del gAto. No aprobado para operación autónoma ni despliegue.**

La implementación inicial tenía fallos reales de procedencia, autoridad, autoingesta, orden temporal y publicación de archivos. Se reprodujeron y se corrigieron dentro de demonio-sintesis/. La nueva versión exige fuentes fijadas por commit, valida el blob real, restringe la autoridad a un dictamen firmado conocido, exige que cada hecho esté literalmente respaldado por esa fuente, limita el cambio documental permitido, añade deduplicación por fuente e ID y hace atómica la publicación de deltas y checkpoints.

La batería adversarial local ejecutada terminó con **38 pruebas aprobadas y 0 fallidas**. También se ejecutó py_compile sobre los módulos de implementación y prueba.

La reserva principal es de integración: el prototipo todavía no incorpora su propio adaptador GitHub para source_verifier ni un cargador/orquestador que garantice que el historial completo se entregue a la deduplicación en cada ejecución. Por tanto, los controles están implementados en las funciones, pero no se ha demostrado un ciclo autónomo completo. La PR de corrección está abierta para revisión de Softly y del gAto; no se ha fusionado ni desplegado.

## 2. Fuentes autoritativas verificadas

Se recuperaron los dos documentos originales en los commits fijados, no mediante resúmenes ni referencias a main:

| Fuente | Blob SHA verificado | Commit que contiene el blob |
|---|---|---|
| Dictamen firmado de aprobación | 2bc262404a055fe6a706d5deb4c14701bfeb898d | 7c40b0467006ee850aa916c3a18ce1b56e1604a1 |
| Glosario Técnico Softly 0.1.0 | 311deb2fc3c114ce4911729562474c4412bc0136 | d050773de04e92aa260979fbe2c5c11123be9161 |

El dictamen se recuperó desde el commit 7c40b0467006ee850aa916c3a18ce1b56e1604a1 y su contenido produjo exactamente el blob SHA indicado. El glosario se recuperó desde el commit d050773de04e92aa260979fbe2c5c11123be9161 y produjo exactamente su blob SHA indicado. También se comprobó la existencia del commit de consolidación corregida 5c3dede6695752c768f5d7df8f85a73263489c52.

El dictamen autoriza expresamente la promoción del glosario de Propuesto a Vigente, ratifica D01–D12 y mantiene la fuerza normativa descriptiva y orientativa, no constitucional. También excluye modificaciones automáticas a casa canónica, contratos, schemas, permisos y arquitectura.

## 3. Matriz de los seis puntos ciegos

| Punto | Fallo reproducido en la versión inicial | Corrección incorporada | Resultado y reserva |
|---|---|---|---|
| A. Procedencia y compresión sucesiva | Aceptaba rutas y SHA arbitrarios, referencias incompletas o resúmenes etiquetados como fuente original. No verificaba el contenido del blob ni la pertenencia al commit. | Registro de confianza cerrado al dictamen aprobado; verificación de repositorio, ruta, blob SHA, commit SHA y contenido; coincidencia literal de cada hecho con la fuente firmada. | Los ataques de ruta, SHA, fuente derivada, fuente ausente y commit incorrecto se rechazan. Falta integrar el adaptador real de GitHub. |
| B. Consenso prematuro | classification=ratified_decision y ratification_explicit=true bastaban para superar la validación estructural. | La clasificación no otorga autoridad. Se exige la fuente firmada exacta del registro de confianza, marcadores de aprobación/firma y hechos respaldados literalmente. Se rechazan hipótesis, propuestas y acuerdos parciales. | La manipulación de classification sin el dictamen fijado no crea una decisión. El registro de confianza cubre deliberadamente solo el primer experimento. |
| C. Autoingesta | La exclusión dependía de actor_type=daemon_synthesizer; cambiarlo permitía reintroducir una salida. No existía deduplicación persistente entre ejecuciones. | Se ignora la marca del demonio, pero además se deduplica por fuente autoritativa e ID histórico. Markdown, HOT-CHECKPOINT y reportes no se aceptan como JSON de entrada. | Copias con actor_type alterado se rechazan si el historial se carga. El llamador debe cargar siempre el historial completo; aún no existe un orquestador que lo garantice. |
| D. Carreras e integridad | Escritura directa, sin publicación atómica ni prevención de sobrescritura. No controlaba IDs duplicados de forma persistente. | Delta escrito en temporal, fsync y publicación atómica sin sobrescritura; HOT-CHECKPOINT mediante temporal y reemplazo atómico; validación previa; rechazo de IDs y fuentes duplicadas. | Dos escritores concurrentes de un mismo delta dejan un único archivo completo. Las interrupciones simuladas no publican parciales. HOT-CHECKPOINT aún carece de bloqueo distribuido y control de versión entre escritores. |
| E. Contaminación de modos | state_delta aceptaba valores que podían describir cambios fuera del alcance documental. | Esquema cerrado y transición permitida únicamente para Glosario Técnico Softly 0.1.0: Propuesto → Vigente, fuerza descriptiva y orientativa, no constitucional. Se rechazan campos de permisos, contratos, schemas y arquitectura. | Los ataques de elevación normativa y cambio de documento se rechazan. No se modificó ningún artefacto externo. |
| F. HOT-CHECKPOINT | Elegía los últimos elementos recibidos, no los cinco cronológicamente recientes; omitía commit SHA y rol; no verificaba fuentes. | Orden por timestamp e ID; máximo estricto de 100 líneas; verificación de fuentes; conserva repo, ruta, blob, commit y rol; salida vacía válida; rechazo de deltas inválidos; escritura atómica y regeneración determinista. | HOT-CHECKPOINT regenerado: 18 líneas. Pruebas verifican cinco recientes, igualdad byte a byte, entrada vacía, rechazo de inválidos y conservación del archivo anterior. |

## 4. Ataques adversariales ejecutados

### A. Procedencia y compresión sucesiva

- Resumen sin referencia a la fuente original: rechazado por ausencia de fuente firmada fijada.
- Delta que cita exclusivamente otro delta: rechazado; original_source no es un rol de autoridad admitido y no coincide con el registro de confianza.
- Cadena de resúmenes con pérdida de una restricción: el hecho debe coincidir literalmente con el texto de la fuente firmada; un resumen no puede sustituirla.
- Ruta correcta con blob SHA incorrecto: rechazado por discrepancia con el blob recuperado y con el registro fijado.
- Blob SHA presente sin commit SHA: rechazado por esquema incompleto.
- Fuente inaccesible o commit sustituido: rechazado; el resolver debe devolver el commit fijado. Se añadió una prueba de commit mismatch.

### B. Consenso prematuro

- observation, hypothesis, proposal y partial_agreement no ingresan como decisiones.
- classification manipulado a ratified_decision no supera la verificación si la fuente no es la aprobada.
- ratification_explicit es obligatorio, pero no basta por sí solo.
- Hechos no contenidos en el dictamen firmado son rechazados.
- El texto de una conversación extensa sin dictamen explícito no coincide con el registro de confianza y no puede producir una decisión.

### C. Autoingesta

- Salida con actor_type=daemon_synthesizer: ignorada.
- Misma salida con actor_type cambiado a human: rechazada por fuente ya procesada, siempre que el historial se entregue.
- Copia en otro directorio y con delta_id cambiado: rechazada por la identidad de la fuente ya procesada.
- HOT-CHECKPOINT y reporte Markdown: rechazados como entradas JSON.
- Un delta con source_refs que apuntan solo a resúmenes no adquiere autoridad.

### D. Escrituras e integridad

- Dos escritores concurrentes publicando el mismo delta: exactamente uno publica; el otro recibe rechazo por ID existente.
- Interrupción simulada antes de publicar el delta: no aparece archivo final parcial y el temporal se limpia.
- Interrupción simulada al reemplazar HOT-CHECKPOINT: se conserva el checkpoint anterior.
- IDs duplicados en el lote o en el historial: rechazados.
- Fuente consultada en un commit distinto: rechazada.
- La lectura de fuentes fijadas por commit evita depender de una rama mutable. No se ejecutó una prueba de caída física del proceso o pérdida de energía; se probaron fallos inyectados en las operaciones de publicación.

### E. Modos operativos

- Intento de introducir permisos en state_delta: rechazado.
- Intento de cambiar arquitectura: rechazado.
- Fuerza normativa obligatoria/constitucional: rechazada.
- Intento de registrar una transición de otro documento: rechazado.
- La salida solo registra la transición documental expresamente aprobada.

### F. HOT-CHECKPOINT

- Límite de 100 líneas: validación estricta; una entrada que lo excede no reemplaza el archivo anterior.
- Cinco deltas recientes: seleccionados por timestamp, no por orden de lectura.
- Punteros: conserva repositorio, ruta, blob SHA, commit SHA y rol.
- Sin deltas: genera una vista válida que indica Ninguna.
- Delta inválido o fuente inaccesible: falla sin publicar.
- Regeneración: dos ejecuciones con las mismas entradas producen bytes idénticos.
- Autoridad: el checkpoint se declara vista derivada y no es fuente de verdad ni fuente de decisiones.

## 5. Correcciones y commits

Todos los cambios permanecen dentro de demonio-sintesis/. Se abrió la rama katarina/audit-demonio-sintesis-0.1.0 en SoftlyLab.

| Archivo | Commit de corrección | Blob SHA final |
|---|---|---|
| tools/synthesizer.py | 7fda4ffea41a53af425b62b51087567e6a3f0245 | 7fb4fba0b6fc9842c94e1e00b7c86a8d018db286 |
| tests/test_synthesizer.py | 3e45c02d3cb10e22fe528d059e519a8312fb6de7 | b9401bf32e3620bf79a492f85b15ba8dd3ac4da5 |
| tests/test_atomic_failures.py | afa3393b91fff6924407da317530ab1feda1ff69 | 7cfb9f3b9c602d39932a7a2648de881b6d68f5cb |
| SPEC-0.1.0.md | eb0d4d17d7238025f402854b1199b932dbac59b0 | bce88a038390e1b27d3944591b1e7a9e5484749e |
| DELTA-2026-11-17-GLOSARIO-001.json | 04a8afaef6754ba0ac07f55b1bd1ba293077e5d6 | 4effd05a52bbec2b68863f36ca367d5274b60a5f |
| HOT-CHECKPOINT.md | 3d94f3948bc44842c2fcfc6027acafe93adf6648 | 306f056e9426f43b02d8baf3e415a15445ee3f18 |
| tests/fixtures/approval-source-fixture.md | e4f3e9a7e98e09416ada8cefb2438945c497c5d7 | 2bc262404a055fe6a706d5deb4c14701bfeb898d |
| tests/fixtures/DELTA-2026-11-17-GLOSARIO-001.json | 731a3d1bc9a6187af3bcf78249e6e3616803d315 | 4effd05a52bbec2b68863f36ca367d5274b60a5f |

El HEAD de la rama al cierre de esta auditoría es afa3393b91fff6924407da317530ab1feda1ff69. La rama contiene 16 commits sobre main, sin cambios externos a demonio-sintesis/.

PR para revisión de Softly: https://github.com/gatoscientist/SoftlyLab/pull/1

## 6. Resultado de la batería de pruebas

Entorno: Python 3.13.5, Linux.

Comandos ejecutados:

- python -m py_compile synthesizer.py tests/test_synthesizer.py tests/test_atomic_failures.py
- python -m unittest discover -s tests -v

Resultado: **38 pruebas aprobadas, 0 fallidas**.

Cobertura incorporada:
- fuentes fijadas, blob/commit incorrectos, fuente ausente y fuente derivada;
- manipulación de clasificación y ratificación;
- hechos sin respaldo literal;
- replay, autoingesta y cambio de actor_type;
- IDs duplicados;
- límites de state_delta y fuerza normativa;
- selección cronológica y cinco deltas recientes;
- checkpoint vacío, inválido, reproducible y bajo 100 líneas;
- escritura concurrente, sobrescritura e interrupciones simuladas.

Los hashes de los archivos de implementación y pruebas ejecutados coinciden con los blobs publicados en la rama auditada.

No se ejecutó GitHub Actions: no se verificó una ejecución remota de CI. La batería se ejecutó localmente sobre los archivos cuyos hashes se indican arriba.

## 7. Verificación del primer delta

Archivo: demonio-sintesis/deltas/2026-11-17/DELTA-2026-11-17-GLOSARIO-001.json  
Blob SHA corregido: 4effd05a52bbec2b68863f36ca367d5274b60a5f

Resultado:

1. Aprobación explícita: **correcta**, respaldada por el dictamen firmado.
2. Promoción Propuesto → Vigente: **correcta**, autorizada explícitamente.
3. Fuerza normativa: **correcta**, descriptiva y orientativa; no constitucional.
4. Decisiones no atribuidas: **sin hallazgos**; el estado queda limitado al glosario y a la transición aprobada.
5. Procedencia: F1, F2 y F3 apuntan directamente al dictamen firmado mediante source_ref_index=0. Las tres afirmaciones se cotejaron literalmente con el texto original, normalizando solo marcas Markdown. El glosario aprobado se conserva como referencia de apoyo independiente.
6. actor_type: **correcto**, daemon_synthesizer.
7. Autoingesta: ingestion_policy declara eligible_as_future_source=false; el control efectivo adicional depende de la exclusión y deduplicación por fuente/ID.

Las URLs de ambas referencias se corrigieron para apuntar a los commits inmutables, no a main.

## 8. Riesgos abiertos

1. **Adaptador de fuentes:** source_verifier es una interfaz obligatoria, pero el prototipo no incluye todavía un cliente GitHub. La integración debe recuperar la ruta en el commit exacto y devolver los metadatos y el contenido comprobables.
2. **Carga del historial:** read_eligible_inputs recibe processed_source_keys y processed_delta_ids. El llamador debe construirlos desde todo el historial append-only. No se verificó un orquestador que garantice esta carga en cada ejecución.
3. **Concurrencia del checkpoint:** el reemplazo es atómico, pero no existe bloqueo distribuido ni comparación de versión. Un escritor atrasado podría reemplazar un checkpoint más reciente.
4. **Firma:** la confianza combina el commit/blob fijado con marcadores textuales de aprobación y firma. No se implementó una firma criptográfica independiente del dictamen.
5. **Alcance del registro de confianza:** la lista está cerrada deliberadamente al dictamen de este primer experimento. No es un sistema general para ingerir decisiones arbitrarias.
6. **Sistema de archivos:** la publicación de deltas usa hard link atómico en el mismo sistema de archivos. Se verificó en Linux local; no se garantiza comportamiento equivalente en sistemas de archivos de red o entornos que no soporten esa operación.
7. **Integración de runtime:** no se demostró activación, ejecución programada, observación continua ni despliegue del demonio.
8. **CHECKPOINT histórico:** no se migró ni se modificó destructivamente. Su poda o migración permanece fuera de esta auditoría.

## 9. Límites de lo demostrado

Esta auditoría demuestra que el núcleo corregido rechaza los casos adversariales cubiertos por las 38 pruebas y que el primer delta coincide con las fuentes fijadas examinadas. No demuestra que Softly ya haya integrado correctamente source_verifier, que el historial se cargue siempre, que las escrituras concurrentes entre hosts sean seguras ni que exista autenticación criptográfica del emisor.

Tampoco demuestra una reducción efectiva del CHECKPOINT histórico, rendimiento en producción, calidad semántica general para decisiones distintas de este primer caso ni capacidades autónomas fuera de las funciones auditadas.

## 10. Cierre y notificación

La auditoría independiente queda documentada y sus correcciones están publicadas en una rama separada, con una PR abierta para revisión de Softly. La PR solicita expresamente verificar el adaptador de fuentes, la carga del historial y la batería de pruebas antes de preparar el resultado final para el gAto.

**Conclusión:** el prototipo corrigió los fallos críticos reproducidos y queda **aprobado con reservas para revisión del gAto**. No debe describirse como autónomo, desplegado ni listo para operación hasta cerrar las reservas de integración.
