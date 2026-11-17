# Encargo a Katarina — implementación de la nueva arquitectura de coordinación en Softly

**Emisor:** Softly, núcleo operativo/generativo del ecosistema  
**Dirección humana:** gAto  
**Destinataria:** Dra. Katarina (ID: `katarina`, versión documental 2.0.1)  
**Repositorio de trabajo:** `gatoscientist/Softly`  
**Modo:** Fábrica / Entrega Directa  
**Etapa:** 1 de 5 — implementación de Katarina en Softly  
**Fecha:** 2026-11-16  
**Estado del encargo:** Emitido y persistido; ejecución de Katarina aún no verificada.

## Mandatos comunes para las cuatro etapas

1. Respetar la separación de autoría:
   - Katarina implementa en el repositorio de Softly.
   - Softly implementa en el repositorio de Katarina.
2. No copiar documentos literalmente entre repositorios. Adaptar la arquitectura a la identidad, estructura, mandatos y responsabilidades de cada agente.
3. No modificar componentes que no sean necesarios para la implementación.
4. Mantener trazabilidad de decisiones, archivos modificados, pruebas y commits.
5. No declarar una etapa terminada sin evidencias verificables.
6. No confundir coordinación con comunicación.
7. Mantener como hipótesis de trabajo las tres dimensiones:
   - Coordinación propia.
   - Coordinación entre pares.
   - Orquestación.
8. **La cobertura de la coordinación sistémica sigue siendo una pregunta abierta.** No declarar que está resuelta por el mero hecho de implementar las tres dimensiones.
9. La auditoría independiente de esta implementación corresponde exclusivamente a **Audeline**. No delegarla al equipo auditor completo.
10. gAto conserva la decisión final sobre aceptación de resultados y cambios de dirección.

---

# PROMPT 1 — Katarina implementa en Softly

## Objetivo

Implementar en el repositorio Softly la nueva arquitectura de coordinación acordada por gAto: un modelo de coordinación centrado en tareas y dependencias, utilizando las tres dimensiones acordadas como estructura inicial:

1. Coordinación propia.
2. Coordinación entre pares.
3. Orquestación.

## Instrucciones de ejecución

1. Lee los mandatos vigentes de Softly y los documentos arquitectónicos pertinentes antes de modificar archivos.
2. Examina especialmente los patrones de coordinación, el modelo de agentes, los contratos de handoff, los esquemas y las plantillas existentes.
3. Determina qué componentes deben modificarse, cuáles deben mantenerse y si se requieren nuevos artefactos.
4. Implementa el modelo de forma coherente en la arquitectura, mandatos, documentación y contratos que realmente corresponda modificar.
5. Evita duplicar mecanismos existentes o introducir estructuras innecesarias.
6. Conserva la trazabilidad de tareas, dependencias, responsables, resultados y bloqueos.
7. Documenta cómo se relacionan las tres dimensiones y qué responsabilidades corresponden a cada una.
8. No presentes la coordinación sistémica como resuelta. Registra explícitamente la pregunta pendiente y las consecuencias arquitectónicas de cada interpretación posible.
9. Ejecuta las validaciones pertinentes y comprueba la consistencia entre documentos, esquemas y plantillas.
10. Realiza los commits correspondientes y entrega sus identificadores.

## Entrega obligatoria

- Resumen ejecutivo.
- Diagnóstico de la arquitectura inicial.
- Inventario de archivos modificados y creados.
- Justificación técnica de cada modificación relevante.
- Descripción del funcionamiento de las tres dimensiones.
- Decisiones tomadas y alternativas descartadas.
- Pruebas y validaciones ejecutadas, con resultados.
- Riesgos y asuntos pendientes.
- Pregunta de coordinación sistémica expresamente preservada.
- Identificadores de commits.
- Handoff formal dirigido a Softly.

## Criterio de aceptación

Softly debe poder comprender, verificar y adaptar la arquitectura a su propia implementación en Katarina sin depender de explicaciones orales de Katarina.

**Límite de autoría:** no implementes en el repositorio de Katarina. Esa responsabilidad corresponde a Softly en la etapa 3.

## Condiciones de control

- Esta asignación activa la etapa 1; no autoriza a Katarina a ejecutar las etapas posteriores.
- No modificar componentes ajenos al alcance.
- No introducir cambios normativos que excedan la dirección adoptada por gAto.
- No resolver por inferencia la pregunta sobre coordinación sistémica.
- Distinguir diseño documental, implementación, validación, despliegue y aceptación humana.
- Si falta evidencia o existe un bloqueo esencial, documentarlo y detener únicamente la parte afectada; no simular resultados.
- Entregar por el canal de salida autorizado `Katarinasay/` en el repositorio Softly, identificando versión e instancia de origen.

---

## Secuencia global conocida (solo contexto; no ejecutar etapas futuras)

1. **Katarina:** implementar en Softly — esta asignación.
2. **Softly:** verificar la entrega de Katarina.
3. **Softly:** adaptar e implementar en Katarina.
4. **Audeline:** auditar independientemente ambas implementaciones.
5. **gAto:** revisar el expediente y decidir aceptación o correcciones.

La etapa siguiente no se considera iniciada hasta que la anterior entregue evidencia suficiente. La auditoría de esta implementación corresponde exclusivamente a Audeline y no debe anticiparse ni delegarse al equipo auditor completo.
