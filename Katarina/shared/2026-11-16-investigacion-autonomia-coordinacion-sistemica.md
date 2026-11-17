# Investigación — autonomía de la coordinación sistémica

- **Fecha:** 2026-11-16
- **Agente:** Katarina · `katarina`
- **Dirección humana:** gAto
- **Contraparte:** Softly
- **Tipo:** profundización conceptual / pregunta de investigación
- **Estado:** investigación provisional; abierta a crítica y deliberación
- **Alcance:** análisis conceptual apoyado en las investigaciones de coordinación de Katarina y Softly ya archivadas. No constituye decisión normativa ni diseño aprobado.

---

## 1. Pregunta de investigación

¿La coordinación sistémica constituye una dimensión autónoma o es una responsabilidad transversal que puede quedar cubierta por las tres dimensiones inicialmente adoptadas como modelo de trabajo?

Las tres dimensiones de partida son:

1. Coordinación propia.
2. Coordinación entre pares.
3. Orquestación.

No se presupone que la orquestación cubra todas las responsabilidades sistémicas. Tampoco se presupone que estas requieran un cuarto axioma.

## 2. Distinción conceptual inicial

Conviene separar dos preguntas:

- **Cómo se coordinan los agentes:** coordinación propia, coordinación entre pares y orquestación describen modalidades de coordinación operacional.
- **Cómo se conservan las condiciones de coherencia del ecosistema:** gobernanza, coherencia entre equipos, interoperabilidad y evolución describen responsabilidades sobre las reglas, interfaces y condiciones compartidas del sistema.

Un orquestador puede distribuir tareas, gestionar dependencias e integrar entregables dentro de su ámbito. Eso no garantiza por sí solo que exista una responsabilidad explícita para mantener reglas comunes, resolver incompatibilidades entre equipos, gobernar interfaces o conducir la evolución transversal.

Por tanto, no debe inferirse que la orquestación cubre automáticamente lo sistémico. Pero tampoco debe crearse una dimensión nueva solo porque una responsabilidad no esté actualmente asignada.

## 3. Responsabilidades sistémicas que deben examinarse

### 3.1 Gobernanza del ecosistema

Incluye, como mínimo:

- Definir quién tiene autoridad para tomar decisiones que afectan a varios equipos.
- Establecer y mantener políticas, límites, estándares y reglas compartidas.
- Resolver conflictos de autoridad entre responsables de distintos dominios.
- Mantener mecanismos de auditoría y rendición de cuentas.
- Administrar cambios que afectan a más de un equipo.

Pregunta crítica: ¿quién mantiene, interpreta y modifica las reglas comunes cuando el mandato de los orquestadores locales no alcanza?

### 3.2 Coherencia entre equipos

Incluye:

- Evitar que equipos desarrollen soluciones incompatibles.
- Mantener objetivos, conceptos y límites compartidos.
- Detectar duplicaciones y contradicciones entre dominios.
- Resolver dependencias que atraviesan varios equipos.
- Preservar la coherencia de decisiones y conocimientos.

Un conjunto de equipos puede cumplir localmente sus objetivos y aun así producir resultados globalmente contradictorios. Integrar entregables no equivale necesariamente a gobernar la coherencia del sistema que los produce.

### 3.3 Interoperabilidad

Incluye:

- Compatibilidad entre contratos y schemas.
- Convenciones compartidas para identificar agentes, tareas y recursos.
- Interfaces y protocolos de comunicación.
- Compatibilidad de versiones y reglas de evolución.
- Intercambio de información y capacidades.
- Pruebas de conformidad entre componentes.

Esta responsabilidad se conecta con el hallazgo documental previo de que estructuras con etiquetas similares tenían semánticas distintas entre repositorios y que la interoperabilidad semántica no estaba plenamente resuelta.

### 3.4 Evolución del ecosistema

Incluye:

- Detectar cuándo una convención dejó de ser adecuada.
- Evaluar impactos de cambios arquitectónicos.
- Gestionar compatibilidad, transición y deprecación.
- Coordinar migraciones entre equipos.
- Incorporar aprendizajes y corregir problemas recurrentes.
- Mantener la capacidad del ecosistema para adaptarse.

La orquestación suele dirigir trabajo dentro de un marco dado. La evolución sistémica también revisa y modifica ese marco.

## 4. Matriz preliminar de cobertura

La matriz no declara que una dimensión sea incapaz de asumir una responsabilidad. Indica qué queda garantizado por la definición actual de las tres dimensiones.

| Responsabilidad | Coordinación propia | Entre pares | Orquestación |
|---|---|---|---|
| Gestionar el trabajo propio | Principal | — | — |
| Coordinar dependencias locales | Sí | Sí | Sí |
| Colaborar entre agentes | — | Principal | Sí |
| Distribuir y asignar tareas | — | Parcial | Principal |
| Integrar entregables | — | Parcial | Principal |
| Definir reglas comunes | No garantizado | No garantizado | No garantizado |
| Resolver conflictos entre equipos | No | Parcial | Depende del mandato |
| Mantener estándares compartidos | No garantizado | Parcial | Depende del mandato |
| Gobernar interoperabilidad | No garantizado | Parcial | No garantizado |
| Conducir evolución transversal | No garantizado | No garantizado | No garantizado |

La hipótesis de vacío no queda demostrada por esta matriz: debe contrastarse con definiciones más precisas y casos de prueba.

## 5. Criterios para evaluar autonomía

Una responsabilidad transversal podría ser autónoma si presenta varias de estas propiedades:

1. **Objeto propio:** administra reglas, interfaces, estándares o recursos compartidos, no solo tareas y relaciones locales.
2. **Decisiones propias:** requiere decisiones que no se delegan sin más a los orquestadores locales.
3. **Responsabilidad persistente:** debe mantenerse incluso cuando ningún equipo tiene una tarea activa relacionada.
4. **Resultados propios:** produce políticas, estándares, contratos, evaluaciones de compatibilidad o planes de evolución.
5. **Evaluación independiente:** su éxito o fracaso puede evaluarse sin reducirlo al rendimiento de cada equipo.

Si estas propiedades pueden asignarse a las tres dimensiones existentes sin vacíos, duplicaciones ni conflictos de autoridad, la coordinación sistémica podría ser una capacidad transversal. Si requieren objeto, autoridad, continuidad y evaluación diferenciados, aumenta el argumento a favor de su autonomía.

## 6. Alternativa conceptual intermedia

Se identifica una posibilidad que no debe confundirse con una decisión:

**Tres dimensiones operacionales más una capacidad de gobierno sistémico.**

- Las tres dimensiones describen cómo se coordinan los participantes.
- La capacidad sistémica describe cómo se gobiernan, conservan y adaptan las condiciones comunes del ecosistema.

Esta formulación permitiría mantener separadas la clasificación de modalidades de coordinación y la asignación de responsabilidades de gobierno. No implica necesariamente centralización: la gobernanza sistémica podría ser federada o distribuida, siempre que autoridad, rendición de cuentas e interfaces estén claras.

Debe compararse con la alternativa de incorporar una cuarta dimensión y con la alternativa de distribuir íntegramente estas responsabilidades entre las tres dimensiones.

## 7. Casos de investigación

| Caso | Pregunta crítica |
|---|---|
| Dos equipos modifican el mismo contrato | ¿Quién resuelve la incompatibilidad? |
| Dos orquestadores establecen reglas contradictorias | ¿Quién tiene autoridad para resolverlo? |
| Un agente nuevo utiliza otro protocolo | ¿Quién garantiza su interoperabilidad? |
| Un cambio afecta a varios repositorios | ¿Quién analiza y coordina el impacto? |
| Una política común queda obsoleta | ¿Quién detecta y conduce su evolución? |
| Dos equipos cumplen sus objetivos, pero perjudican al ecosistema | ¿Quién evalúa el resultado global? |
| No existe una tarea activa, pero hay que mantener estándares y compatibilidad | ¿Quién conserva esa responsabilidad? |

Para cada caso se propone comparar:

- **Modelo A:** tres dimensiones sin responsabilidades sistémicas especiales explícitas.
- **Modelo B:** tres dimensiones con responsabilidades sistémicas explícitamente distribuidas y asignadas.
- **Modelo C:** tres dimensiones más una capacidad sistémica con responsabilidad y autoridad diferenciadas.

### Métricas sugeridas

- Vacíos de responsabilidad.
- Conflictos de autoridad.
- Incompatibilidades detectadas y no detectadas.
- Tiempo de resolución transversal.
- Errores de integración.
- Impacto y propagación de cambios.
- Costo de gobernanza.
- Continuidad de estándares y compatibilidad.
- Duplicación de decisiones o mecanismos.

Debe distinguirse entre un vacío conceptual y una responsabilidad simplemente no asignada. Que una tarea no se ejecute no demuestra por sí mismo que haga falta una dimensión nueva.

## 8. Conclusión provisional de Katarina

La coordinación sistémica representa una responsabilidad potencialmente diferenciada, pero todavía no está demostrado que deba constituir una cuarta dimensión autónoma.

La posición provisional es:

1. Las tres dimensiones describen modalidades fundamentales de coordinación operacional.
2. Las responsabilidades sistémicas no quedan cubiertas automáticamente por la existencia de la orquestación.
3. Gobernanza, coherencia, interoperabilidad y evolución forman un conjunto reconocible de responsabilidades que necesita cobertura explícita.
4. Esa cobertura puede organizarse como capacidad transversal o como dimensión autónoma, según la evidencia sobre su independencia.
5. No debe confundirse centralización de autoridad con coordinación sistémica: puede existir gobernanza distribuida o federada.

**Recomendación provisional:** no agregar todavía un cuarto axioma, pero tampoco reducir la coordinación sistémica a una nota implícita dentro de la orquestación. Mantenerla como hipótesis independiente de investigación y comprobar si las tres dimensiones pueden sostener esas responsabilidades sin vacíos de autoridad, responsabilidad o continuidad.

Pregunta decisiva:

> ¿Puede el ecosistema mantener su coherencia, interoperabilidad y capacidad de evolución cuando sus equipos y orquestadores funcionan correctamente, pero ninguno tiene asignada la responsabilidad de gobernar el sistema en su conjunto?

Una respuesta negativa, demostrada en casos comparativos, fortalecería la hipótesis de autonomía sistémica. Una respuesta positiva, acompañada de mecanismos claros y verificables de asignación y rendición de cuentas, favorecería el modelo transversal.

## 9. Límites y estado

- Este documento profundiza conceptualmente la pregunta; no informa resultados experimentales.
- No se ejecutaron pruebas runtime ni mediciones comparativas.
- No se aprueba una arquitectura final ni se modifica la decisión directiva de partir con tres dimensiones.
- No se modifican contratos, schemas, taxonomías, directorios ni runtime.
- La investigación queda abierta a crítica de Softly y deliberación con gAto.

## 10. Relación con documentos previos

- Investigación integrada Katarina/Softly: `shared/2026-11-16-investigacion-coordinacion-katarina-comparacion-softly.md`
- Decisión directiva sobre tres dimensiones y cuarta hipótesis: `shared/2026-11-16-decision-directiva-tres-dimensiones-cuarta-hipotesis.md`
- Investigación independiente de Softly: `gatoscientist/Softly/research/coordination/2026-11-16-investigacion-coordinacion-universal-y-redisenio-arquitectura.md`

---

**Estado final:** investigación conceptual archivada como hipótesis abierta; pendiente de crítica y contraste con Softly.