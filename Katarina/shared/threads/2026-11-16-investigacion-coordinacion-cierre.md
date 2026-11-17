# Hilo archivado — investigación de coordinación, comparación y profundización sistémica

- **Fecha:** 2026-11-16
- **Agente:** Katarina · `katarina` · versión normativa 2.0.1
- **Dirección humana:** gAto
- **Tipo:** investigación, comparación independiente y cierre documental
- **Estado:** investigación comparativa archivada; profundización sistémica incorporada; deliberación con Softly pendiente
- **Repositorio de archivo:** `gatoscientist/Katarina`

## 1. Objetivo del hilo

Investigar de forma independiente la coordinación entre agentes en el ecosistema autorizado, estudiar competencias universales y arquitectura de colaboración, contrastar hallazgos entre seis repositorios y comparar el resultado de Katarina con la investigación independiente de Softly.

## 2. Trabajo realizado

1. Katarina investigó los repositorios autorizados: Katarina, Cytryna, TITAN, Auditoria, Softly y Laboratorio-de-agentes.
2. Se revisaron estructuras, contratos, procedimientos, schemas, canales, registros y código relevante; se consultaron fuentes académicas y técnicas.
3. Katarina formuló el marco coordinar/coordinarse, competencias universales y por rol, hallazgos transversales y tres alternativas arquitectónicas.
4. La recomendación independiente de Katarina fue la Alternativa B: coordinación centrada en tareas, piloto medido y sin runtime inmediato.
5. Katarina leyó el informe final independiente de Softly: [investigación de coordinación universal y rediseño](https://github.com/gatoscientist/Softly/blob/main/research/coordination/2026-11-16-investigacion-coordinacion-universal-y-redisenio-arquitectura.md).
6. Se compararon ambos informes. Los dos convergen en la Alternativa B y en postergar runtime; permanecen diferencias sobre la jerarquía conceptual, la dimensión de coordinación sistémica y la representación física mínima.
7. Se integraron los hallazgos, límites, recomendaciones y decisiones reservadas a gAto en un informe persistente de Katarina.

## 3. Resultado principal

La recomendación integrada es tratar la tarea como unidad canónica de responsabilidad, vincular mensajes/eventos/artifacts a ella, mantener workspaces solo cuando exista un recurso genuinamente compartido, y derivar vistas de inbox/outbox cuando sea viable. La coordinación propia y entre pares debe ser universal; la orquestación requiere rol y autoridad.

La convergencia entre los informes no equivale a aprobación humana. No se implementó ni migró la arquitectura, no se modificaron schemas ni contratos, no se desplegó runtime y no se ejecutaron experimentos comparativos.

## 4. Diferencias y decisiones pendientes

- Resolver si «sistema de conocimiento y coordinación cognitiva» y «arquitectura de información operacional» tienen una jerarquía o se mantienen como perspectivas complementarias.
- Resolver si coordinación sistémica es una dimensión propia o parte de la orquestación.
- Definir el modelo conceptual y la estructura física mínima para un piloto.
- Autorizar o rechazar un piloto y determinar su alcance.
- Decidir si y cuándo actualizar moldes, contratos, schemas o directorios.
- Postergar cualquier runtime A2A/MCP/workflow hasta que exista evidencia de necesidad.

Todas estas decisiones permanecen reservadas a gAto.

## 5. Evidencia y commits

- Informe integrado de investigación y comparación: [shared/2026-11-16-investigacion-coordinacion-katarina-comparacion-softly.md](../2026-11-16-investigacion-coordinacion-katarina-comparacion-softly.md)
- Commit del informe integrado: `5b28aad053311245519288038ea0614192d1a2d7`
- Informe final independiente de Softly: commit reportado por el registro de Softly `709dfdbb43724b73ef10833f5743ebffeb615ebd`; referencia externa, no commit creado por Katarina.
- La investigación no modificó los seis repositorios autorizados. Los commits de este cierre se realizaron únicamente en `gatoscientist/Katarina`.

## 6. Límites de evidencia

La investigación fue documental. No se fijaron snapshots inmutables de cada repositorio para todas las observaciones, no se ejecutaron pruebas de runtime, no se midieron costos reales y no se validó experimentalmente la Alternativa B. El informe distingue hechos observados, inferencias, hipótesis y propuestas. La lectura de un documento o la existencia de un commit no prueba ejecución de un flujo.

## 7. Estado de cierre

- [x] Investigación independiente de Katarina documentada.
- [x] Informe final independiente de Softly leído.
- [x] Comparación de ambos informes documentada.
- [x] Acuerdos, diferencias y límites preservados.
- [x] Decisiones reservadas a gAto identificadas.
- [x] Informe persistido con commit.
- [x] Registro de cierre persistido con commit.
- [ ] Aprobación humana de la arquitectura.
- [ ] Autorización y ejecución de piloto.
- [ ] Cambios normativos o migraciones.
- [ ] Validación experimental o runtime.

**Cierre:** el hilo queda cerrado en cuanto a investigación y documentación. No se declara aprobada, implementada ni validada la arquitectura recomendada.


## 8. Continuación — autonomía de la coordinación sistémica

A petición de Softly, Katarina profundizó la pregunta que había quedado expresamente abierta: si la coordinación sistémica constituye una dimensión autónoma o una responsabilidad transversal cubierta por coordinación propia, coordinación entre pares y orquestación.

La profundización distingue coordinación operacional (cómo se coordinan los participantes) de gobierno del ecosistema (cómo se conservan y evolucionan las condiciones comunes de coordinación). Examina cuatro responsabilidades: gobernanza, coherencia entre equipos, interoperabilidad y evolución del ecosistema.

La conclusión de Katarina es provisional: estas responsabilidades requieren cobertura explícita y no quedan garantizadas por la mera existencia de la orquestación; sin embargo, todavía no está demostrado que deban constituir una cuarta dimensión. Se propone contrastar tres modelos: tres dimensiones sin cobertura sistémica explícita; tres dimensiones con responsabilidades sistémicas distribuidas y asignadas; y tres dimensiones más una capacidad de gobierno sistémico diferenciada.

Documento de profundización: [Investigación sobre autonomía de la coordinación sistémica](../2026-11-16-investigacion-autonomia-coordinacion-sistemica.md).

### Estado actualizado

- [x] Pregunta de investigación sobre autonomía sistémica preservada.
- [x] Responsabilidades de gobernanza, coherencia, interoperabilidad y evolución examinadas conceptualmente.
- [x] Hipótesis de autonomía y alternativa transversal mantenidas abiertas.
- [ ] Crítica y contraste de Softly.
- [ ] Deliberación y decisión de gAto.
- [ ] Diseño y ejecución de casos comparativos.
- [ ] Aprobación de una arquitectura final.

Esta continuación no modifica la decisión directiva de comenzar con tres dimensiones ni autoriza cambios normativos, schemas, contratos, taxonomías, directorios o runtime. El cierre documental anterior se conserva como cierre de la fase comparativa; la pregunta sistémica queda ahora abierta como una nueva línea de investigación.
