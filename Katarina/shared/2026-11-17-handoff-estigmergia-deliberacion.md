# Handoff a Katarina — deliberación sobre estigmergia

**Fecha:** 2026-11-17  
**Instancia destinataria:** Katarina 0.2.0-experimental  
**Casa:** `gatoscientist/ResKata`, rama `main`  
**Participantes de la próxima deliberación:** gAto, Softly y Katarina  
**Estado:** material de lectura y deliberación; no es orden de implementación.

## Encargo

gAto entregó a Softly dos Deep Research y decidió que el primero, sobre estigmergia, es el que más puede ayudar a terminar de definir Softly 2.0. El segundo, sobre capacidades estocásticas sin núcleo blindado, queda como contexto complementario; no debe recibir el mismo peso ni desplazar el foco.

Katarina debe estudiar el primer informe y deliberar con gAto y Softly en un hilo separado. No debe asumir que las conclusiones de Softly son decisiones cerradas. Debe aportar criterio independiente, cuestionar las inferencias y distinguir evidencia, interpretación e hipótesis.

## Fuente primaria

*Estigmergia en la Coordinación de Sistemas Multiagente: Fundamentos Teóricos, Arquitecturas de Middleware y Fronteras en Inteligencia Artificial Generativa* (PDF de 29 páginas, entregado por gAto el 2026-11-17).

El PDF original fue entregado en la conversación de Softly. Este handoff transmite una síntesis sustantiva de su contenido para que Katarina pueda iniciar la deliberación; no afirma que el archivo PDF original se haya copiado a ResKata. La síntesis consolidada también está en el repositorio privado `gatoscientist/SoftlyLab`, archivo `Estigmergia-Deliberacion-Softly-2.0.md`.

## Tesis central de la investigación

La estigmergia es coordinación indirecta y mediada por el entorno: una acción deja una traza perceptible en un medio compartido y esa traza estimula acciones posteriores del mismo agente o de otros. La coordinación puede emerger sin comunicación directa constante, sin que los agentes se conozcan entre sí y sin planificación global.

El entorno no es necesariamente un depósito pasivo. Puede actuar como memoria colectiva externa y como mecanismo de coordinación.

## Conceptos que deben quedar claros

La fuente identifica cinco componentes: acción, agente, medio, traza y coordinación. La traza no tiene que ser un mensaje intencional; puede ser un efecto secundario observable del trabajo.

La taxonomía de Parunak cruza dos distinciones:
- basada en marcadores / sematectónica;
- cuantitativa / cualitativa.

Esto produce cuatro modalidades. La estigmergia cognitiva extiende la idea a agentes con metas, razonamiento y planificación que interpretan artefactos de un espacio de trabajo compartido.

## Arquitecturas revisadas por la fuente

- Linda y TuCSoN: espacios compartidos de tuplas.
- TOTA: tuplas activas que se propagan o evolucionan.
- CArtAgO / JaCaMo: artefactos como abstracciones de primera clase para agentes cognitivos.
- Buzz: estigmergia virtual y memoria compartida para enjambres.
- Campos de presión: modificaciones locales sobre artefactos compartidos orientan el trabajo posterior de agentes.

No hay decisión de adoptar una tecnología específica.

## Dinámica y gobernanza

La estigmergia necesita retroalimentación positiva para reforzar trazas útiles y retroalimentación negativa para evitar estancamiento y conservar adaptación. La investigación describe evaporación, difusión y decaimiento temporal.

El entorno compartido también es una superficie de riesgo. Una traza puede ser incorrecta, obsoleta, maliciosa o estar mal atribuida. La investigación menciona aislamiento de espacios de nombres, procedencia, TTL, permisos y tolerancia a fallos como salvaguardas.

Los resultados experimentales citados por el informe, incluidos los de campos de presión y coordinación espontánea en memorias compartidas, deben leerse bajo sus condiciones concretas. No son garantías generales ni evidencia automática de rendimiento para Softly.

## Relación con Softly 1.1

Softly 1.1 ya establece:
- tarea como unidad canónica de coordinación;
- GitHub como superficie persistente de señales estigmérgicas;
- cuatro clases de artefactos operativos: Paquete, Tarea, Entregable y Checkpoint;
- `inbox` y `outbox` como vistas lógicas;
- archivos y commits sin capacidad de despertar sesiones ni conceder autoridad.

La investigación debe ayudarnos a evaluar si estos acuerdos son suficientes, qué falta y qué conviene cambiar para Softly 2.0. No se debe asumir que GitHub, tal como está usado hoy, ya materializa toda la estigmergia cognitiva descrita en el informe.

## Preguntas para la deliberación conjunta

1. ¿Qué significa exactamente que el entorno sea un mecanismo activo de coordinación y no solo memoria persistente?
2. ¿Qué tipos de trazas deberían existir en el espacio de trabajo de Softly?
3. ¿Cómo puede un agente descubrir trabajo pendiente observando trazas sin que eso equivalga a recibir autoridad o una orden?
4. ¿Qué diferencia debe haber entre observar, proponer, escribir y validar cambios en el entorno?
5. ¿Cómo se identifica la procedencia, vigencia, confianza y caducidad de una traza?
6. ¿Cómo se manejan trazas contradictorias, duplicadas, obsoletas o contaminadas?
7. ¿Qué debe coordinarse por interacción local y qué requiere orquestación explícita?
8. ¿La tarea actual puede evolucionar como artefacto cognitivo compartido o necesitamos otra representación?
9. ¿Qué elementos de Softly 1.1 debemos conservar, revisar o descartar al definir Softly 2.0?

## Uso del segundo Deep Research

*Ventajas y Desventajas de las Capacidades Estocásticas Sin Núcleo Blindado en Sistemas Multiagente* (23 páginas) queda como referencia complementaria para discutir exploración, límites de ejecución, errores encadenados, procedencia y controles. No es el tema central de esta deliberación.

Una distinción útil que puede someterse a examen es: libertad para explorar y proponer no equivale a autoridad para modificar el estado común.

## Límites del encargo

- Esta etapa es deliberativa.
- No modificar `gatoscientist/Softly` ni iniciar Softly 2.0.
- No implementar Runtime.
- No convertir hipótesis de los informes en contratos vigentes.
- No abrir nuevas investigaciones redundantes antes de comprender el informe principal.
- Katarina debe discrepar cuando la evidencia o el razonamiento lo exijan y conservar la responsabilidad de integrar sus conclusiones.

**Resultado esperado:** deliberación conjunta sobre la investigación de estigmergia y su pertinencia para definir la arquitectura de Softly 2.0. No se espera implementación en este hilo.
