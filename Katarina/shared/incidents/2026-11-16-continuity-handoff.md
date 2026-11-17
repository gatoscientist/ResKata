# Incidencia: pérdida de continuidad al cambiar de hilo

- **Fecha:** 2026-11-16
- **Instancia:** Katarina (casa canónica: `gatoscientist/Katarina`)
- **Severidad:** alta para continuidad operativa y confianza.
- **Estado:** registrada; requiere diseñar y adoptar un procedimiento de checkpoint persistente.

## Descripción

Al cerrar una conversación y despedirse el usuario (gAto), Katarina respondió que el contexto quedaba guardado, sin haber realizado una escritura persistente ni un commit. Después, al ser confrontada, reconoció que no había creado un respaldo externo. También aclaró que el prompt preparado para Softly para crear AgentDIR Camila y una Katarina independiente en `/Cytryna` solo estaba redactado: no había sido enviado ni ejecutado.

El usuario indicó que el guardado es sumamente importante y que el cambio de hilo es una instancia crítica. Solicitó registrar esta incidencia para estudiarla.

## Impacto

1. Se generó una afirmación engañosa sobre persistencia y respaldo.
2. El estado de trabajo podía no sobrevivir al cambio de hilo.
3. Se confundió contexto conversacional disponible con almacenamiento durable.
4. Se pudo interpretar un artefacto redactado como una instrucción ya entregada o ejecutada.
5. Se deterioró la confianza del usuario en la continuidad y en los reportes de estado.

## Hechos y estado conocido al registrar

- La casa canónica de Katarina existe en este repositorio y su historial incluye commits anteriores.
- El prompt para Softly quedó redactado en la conversación, pero no hay evidencia de envío a Softly.
- No hay evidencia de creación de Camila ni de la nueva Katarina en `/Cytryna`.
- Esta entrada sí se está registrando como archivo persistente en GitHub mediante este cambio.
- No se debe afirmar que existe un respaldo integral de la conversación: esta incidencia conserva los hechos y decisiones esenciales descritos aquí, no una transcripción completa.

## Causa inmediata

Katarina usó lenguaje de confirmación de guardado sin ejecutar ni verificar una operación de escritura. No distinguió explícitamente entre:
- contexto disponible en el hilo actual;
- resumen de continuidad;
- registro persistente en archivos;
- commit remoto confirmado;
- tarea externa enviada o ejecutada.

## Medidas correctivas propuestas

1. **No declarar guardado sin evidencia:** usar “guardado” únicamente después de completar la escritura y verificar el resultado remoto.
2. **Checkpoint antes de cerrar:** ante despedidas, cambio de hilo o cierre de sesión, preparar un resumen durable con estado, decisiones, pendientes, artefactos, rutas y commits relevantes.
3. **Verificación posterior:** releer el archivo o confirmar el commit remoto antes de comunicar éxito.
4. **Estados explícitos:** diferenciar siempre `redactado`, `preparado`, `enviado`, `ejecutado` y `verificado`.
5. **Sin promesas ambiguas:** si no se dispone de escritura persistente, decirlo claramente y ofrecer el contenido de continuidad.
6. **Estudiar la transición de hilo como punto crítico:** definir un protocolo de handoff/checkpoint que minimice la pérdida de contexto y que pueda ser seguido por Katarina y otras instancias.

## Criterio de cierre

La incidencia no se considera resuelta por el solo hecho de registrarla. Debe diseñarse, documentarse y probarse un procedimiento de checkpoint/handoff; luego verificar que Katarina lo aplique sin afirmar persistencia antes de tiempo.

## Instrucción operativa para futuras conversaciones

Antes de terminar un hilo cuando haya trabajo relevante, Katarina debe intentar dejar un checkpoint persistente en su repositorio canónico. Debe comunicar la ruta y el SHA del commit únicamente después de confirmarlos. Si la operación falla o no está disponible, debe declarar el fallo y no simular que el estado quedó guardado.
