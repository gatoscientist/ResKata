# Informe de destrabes para Dirección — dictamen de decisiones y acciones pendientes

**Fecha de corte:** 2026-11-16  
**Emite:** Katarina · `katarina` · versión documental 3.1.0  
**Casa:** `gatoscientist/Katarina`, rama `main`  
**Destinatario:** gAto  
**Objeto:** identificar los puntos concretos donde una decisión, clasificación o intervención de Dirección puede acelerar el progreso del ecosistema, distinguiendo bloqueos reales, decisiones estratégicas y asuntos que ya no requieren intervención.

## 1. Dictamen ejecutivo

El avance no está detenido por falta de decisiones en todos los frentes. La evidencia consultada permite separar tres situaciones:

1. **Cierre del RESET-CORE-2026-002:** quedan dos limitaciones materiales verificadas: retirar físicamente siete ramas adicionales y resolver la condición de los diez ZIP cuyo contenido binario/restaurabilidad no se ha comprobado. La conexión GitHub utilizada por los agentes no ofrece borrado de refs ni descarga binaria.
2. **Clasificación de proyectos:** TITAN, Cytryna, Laboratorio de agentes y el Equipo del gAto todavía tienen límites de pertenencia/alcance que requieren una decisión clara de Dirección para evitar intervenciones por inferencia.
3. **Evolución posterior:** existen dos iniciativas independientes que pueden avanzar con autorización de gAto: el piloto documental de handoffs/dependencias y el experimento SOFTLY-MIN. No son requisitos para cerrar el reset.

**Dictamen global:** el reset está documentalmente muy avanzado, pero Audeline mantiene NO-GO para certificar su cierre global mientras no se resuelvan las dos limitaciones materiales y la clasificación final de los proyectos asociados. No corresponde reabrir asuntos ya cerrados ni pedir a gAto aprobaciones individuales que la orden vigente ya delegó.

## 2. Destrabes prioritarios para cerrar RESET-CORE-2026-002

### D-01. Retiro físico de las siete ramas adicionales

**Estado:** bloqueo técnico real.  
**Autoridad necesaria:** capacidad de administración Git o ejecución local con permisos de escritura.

El manifiesto de Audeline identifica las siete ramas, conserva sus HEAD SHA y clasifica sus cambios exclusivos. La comparación directa más reciente mantiene las siete ramas divergidas. No deben fusionarse por defecto.

| Repositorio | Rama | Commits exclusivos | Clasificación |
|---|---|---:|---|
| Softly | `fix/f03-recover-ledger` | 5 | Histórica/no operativa; no integrar |
| Softly | `recovery/AUD-20261116-001` | 3 | Supersedida por contenido ya publicado en main |
| Katarina | `kat-006-stage3-softly-2026-11-16` | 8 | KAT-006 cerrado; no integrar |
| Auditoria | `amelia/propuesta-mejora-auditoria-2026-11-15` | 2 | Propuesta histórica; no adoptar |
| Auditoria | `proposal/AUD-20261115-001-refactor-equipo-auditoria` | 2 | Propuesta histórica incompatible con la identidad auditora única |
| Auditoria | `recovery/AUD-20261116-001` | 19 | Recovery histórica; no integrar |
| Laboratorio-de-agentes | `proposal/auditoria-reforma-normativa-2026-11-15` | 1 | Propuesta histórica; no adoptar automáticamente |

**Total:** 40 commits exclusivos distribuidos en siete ramas.

**Qué destraba gAto:** facilitar una conexión Git con permiso `delete-ref` o ejecutar el retiro desde un clon local con permisos de escritura. Antes del borrado, preservar cada HEAD mediante una referencia/tag de archivo o un bundle Git y verificar que el HEAD siga coincidiendo con el manifiesto. Después, eliminar solo las siete refs listadas y comprobar que cada repositorio activo conserva únicamente `main`.

**No hacer:** fusionar las ramas para “salvarlas”; sus contenidos ya están clasificados y varias propuestas contradicen el estado vigente. Tampoco borrar una rama antes de preservar sus commits exclusivos.

**Dictamen:** GO para retiro físico una vez preservadas las referencias. No requiere una nueva decisión estratégica sobre el contenido de las ramas; la orden vigente ya define la política.

### D-02. Resolver el estado de los diez ZIP de preservación

**Estado:** bloqueo de evidencia para la certificación global, no para el trabajo cotidiano.  
**Autoridad necesaria:** decisión de preservación de gAto o acceso a los binarios.

Audeline cotejó ruta, tamaño y Git blob SHA de los diez ZIP. Los metadatos coinciden, pero los archivos no se descargaron ni extrajeron; no hay SHA-256 binario ni prueba de restauración. Por tanto, no se pueden describir como respaldos restaurables.

**Qué destraba gAto:**

- **Opción recomendada si no se necesita restaurarlos:** declarar los diez ZIP preservados exclusivamente como evidencia histórica, con restaurabilidad desconocida/no verificada y sin usarlos como salvaguarda para futuras eliminaciones.
- **Opción alternativa:** facilitar los diez archivos binarios por un canal accesible para calcular SHA-256, inspeccionar contenido y probar restauración en un entorno aislado.

**Dictamen:** GO para conservarlos como evidencia no restaurable si esa es la intención de Dirección. Si se espera que funcionen como respaldos, NO-GO hasta verificar contenido y restauración. No hay motivo para mantener indefinidamente el cierre global esperando una restauración que Dirección no necesita.

### D-03. Clasificar el alcance de los proyectos asociados

**Estado:** decisión de frontera pendiente.  
**Autoridad necesaria:** gAto, con recomendación de Softly y contraste de Audeline.

| Proyecto/activo | Evidencia actual | Decisión que destraba |
|---|---|---|
| **TITAN** | Proyecto asociado; mantiene paquetes de agentes diseñados y componentes propios. Audeline advierte riesgos técnicos y no puede inferir si es dependencia operativa o producto independiente. | Confirmar si TITAN es un producto independiente fuera del núcleo Softly o un activo operativo incorporado al ecosistema. Recomendación: mantenerlo como proyecto independiente en HOLD hasta una orden específica; no activar equipos ni migrar paquetes al registro Softly. |
| **Cytryna** | Su documentación la define como proyecto independiente. No figura como identidad del registro central. Su relación con la Dirección de Recuperación de Cytryna en TITAN no demuestra una autoridad única. | Confirmar su exclusión del núcleo Softly y mantenerla como proyecto independiente. Cualquier reparación o cambio debe tener un encargo propio, repositorio y responsable explícitos. |
| **Laboratorio-de-agentes** | Repositorio de investigación/archivo con paquetes y propuestas; mantiene paquetes definidos para invocación directa y duplicaciones históricas. | Clasificarlo expresamente como repositorio de investigación y archivo, no como fuente de identidades operativas invocables del ecosistema vigente. Preservar paquetes e historia, sin activarlos. |
| **Equipo del gAto** | El checkpoint lo deja pendiente de clasificación; no se debe asumir que pertenece al Equipo Softly ni al núcleo de tres identidades. | Determinar si es un proyecto privado/independiente del gAto o un activo incorporado al ecosistema Softly. Recomendación: mantenerlo fuera de alcance hasta que gAto indique lo contrario. |
| **gAtoSD** | Audeline lo clasificó como proyecto independiente, con Lucyna y Andy bajo restricción explícita de no inspeccionar código. | No requiere intervención para el reset. Mantener exclusión y restricción de inspección vigentes. |

**Dictamen:** GO para continuar el reset si se registran las clasificaciones recomendadas y se mantienen los proyectos externos sin intervención. La decisión sobre TITAN y el Equipo del gAto es la más importante para eliminar ambigüedad de alcance.

## 3. Decisiones para iniciar nuevas líneas de progreso

### D-04. Autorizar un piloto acotado de coordinación documental

**Estado:** propuesta pendiente; no bloquea el reset.  
**Fuente:** recomendaciones KFB-01 a KFB-15 de Katarina.

El piloto recomendado no necesita infraestructura adicional. Puede probar, en un conjunto pequeño de tareas reales:

- acuse explícito del receptor en cada handoff;
- owner único por resultado;
- integrador y autoridad aceptadora identificados;
- bloqueos con responsable de resolución;
- verificación de dependencias e IDs antes de declarar una tarea lista o aceptada;
- separación entre entregado y aceptado.

**Qué debe decidir gAto:** autorizar o no un piloto documental acotado, definir el proyecto piloto y los criterios de éxito. La propuesta es medir recepción, tareas huérfanas, retrabajo, tiempo de ciclo y exactitud del estado declarado.

**Dictamen:** GO para un piloto pequeño si se quiere reducir pérdidas de continuidad y ambigüedad de responsabilidad. NO-GO para convertir el piloto en una migración general de schemas o contratos antes de medir resultados.

### D-05. Autorizar o diferir SOFTLY-MIN

**Estado:** investigación documental terminada; experimento no ejecutado.  
**Fuente:** `research/syntheses/2026-11-16-softly-min-nucleo-minimo-y-equivalencia-funcional.md`.

La investigación propone construir una instancia paralela SOFTLY-MIN y comparar:

- A: Softly de referencia;
- B: SOFTLY-MIN, sin historia personal del director;
- C: núcleo mínimo sin memoria externa.

El objetivo es determinar si se conserva la capacidad funcional y qué contexto es realmente indispensable. La investigación no recomienda modificar el núcleo oficial antes de medir.

**Qué debe decidir gAto:** autorizar la construcción experimental de B y el protocolo comparativo A/B/C, o dejar la iniciativa archivada para más adelante.

**Dictamen:** GO para experimento aislado, con criterios de evaluación fijados antes de ejecutarlo. NO-GO para reemplazar SOFTLY.md, borrar memoria histórica o declarar equivalencia sin resultados.

### D-06. Mantener la decisión de tres dimensiones y evaluar la hipótesis sistémica con evidencia

**Estado:** decisión inicial ya tomada por gAto; no requiere una nueva decisión inmediata.

La decisión persistida establece tres dimensiones iniciales: coordinación propia, coordinación entre pares y orquestación. La coordinación sistémica permanece como hipótesis rival, no como cuarta dimensión aprobada ni descartada.

**Qué destraba gAto más adelante:** autorizar casos de prueba dentro del piloto D-04 y exigir evidencia de responsabilidades sistémicas que no queden cubiertas por la orquestación.

**Dictamen:** mantener el acuerdo actual. No reabrir la discusión conceptual sin evidencia nueva. No crear una cuarta dimensión ni una identidad adicional por anticipación.

### D-07. Decidir si se migran capacidades de paquetes históricos

**Estado:** opcional; no bloquea el reset.

El registro v2 mantiene cinco paquetes como candidatos no asignados: Tiffany, Tara, Thea, Tabata y Melina. Aurora y Autumn se conservan como históricos. Ningún paquete tiene autoridad operativa ni herencia automática.

**Qué debe decidir gAto:** mantenerlos archivados sin asignación, o autorizar una evaluación de capacidades concretas para integrarlas en Softly, Katarina o Audeline. La decisión debe ser por capacidad demostrable, no por reactivar identidades.

**Dictamen:** por ahora, conservar sin asignar. Solo abrir evaluación si existe una necesidad concreta que las tres identidades actuales no cubran.

### D-08. Autorizar protección de ramas principales

**Estado:** medida preventiva recomendada; no es criterio explícito para certificar el reset.

El último inventario de CHECKPOINT registra `protected:false` para main en nueve repositorios consultados. Esto deja abierta la posibilidad de pushes directos sin las salvaguardas de revisión que se definan.

**Qué destraba gAto:** autorizar una política de protección proporcional para los repositorios activos: revisión requerida, checks aplicables, restricción de force-push y control de borrado de main. Debe configurarse después de clasificar cada repositorio y confirmar quién puede administrar sus reglas.

**Dictamen:** GO como endurecimiento posterior a la consolidación. No retrasar por esto el cierre de los otros frentes.

## 4. Asuntos que no requieren una decisión de gAto ahora

- **KAT-006:** cerrado administrativamente como `not_planned`; Katarina PR #1 está cerrado sin merge. No queda decisión A/B/C ni aceptación técnica pendiente.
- **Softly PR #4:** cerrado como supersedido; los cambios vigentes de canal ya están en main. La rama residual está incluida en D-01.
- **Auditoria PR #1:** cerrado como supersedido; no fusionar. La rama residual está incluida en D-01.
- **Softly issues #2 y #3:** revisiones de investigación Godot independientes del reset. El issue #3 fue completado; no son bloqueos del reset.
- **Registro de identidades:** el registro v2 ya separa las tres identidades operativas, la asignación temporal y los paquetes sin autoridad. No reabrir el diseño para cerrar RESET-002.
- **Recepciones:** los acuses de Katarina, Audeline y Zoe están documentados. No hay una decisión pendiente de recepción.
- **Supervisión de Zoe:** continúa temporalmente hasta el dictamen final independiente de Audeline y la confirmación expresa de cierre por gAto. No corresponde cerrar su asignación antes de esas dos condiciones.
- **El asunto excluido por orden expresa anterior:** no es bloqueo, dependencia ni decisión pendiente del reset. No debe reintroducirse en el tablero.

## 5. Secuencia recomendada para destrabar sin mezclar frentes

1. **Resolver D-03:** fijar por escrito el límite de TITAN, Cytryna, Laboratorio y Equipo del gAto. Mantener gAtoSD excluido.
2. **Resolver D-02:** declarar los ZIP evidencia histórica no restaurable, o facilitar los binarios para su verificación.
3. **Ejecutar D-01:** preservar siete HEAD mediante tags/bundle, retirar las refs y verificar que solo quede `main` en los repositorios activos.
4. **Solicitar a Audeline el dictamen final:** actualizar issue #7, contrastar los criterios restantes y cerrar su misión solo con evidencia.
5. **Recibir el dictamen final y decidir el cierre global:** gAto confirma expresamente RESET-CORE-2026-002; entonces termina la asignación temporal de Zoe.
6. **Elegir D-04 o D-05 como siguiente iniciativa:** no iniciar ambas a la vez si compiten por el mismo tiempo de evaluación.

## 6. Matriz de decisión de Dirección

| ID | Acción de gAto | Efecto | Prioridad | ¿Bloquea cierre RESET? |
|---|---|---|---|---|
| D-01 | Facilitar borrado de refs o ejecutar retiro de siete ramas tras preservación | Permite cumplir rama única `main` | P0 | Sí |
| D-02 | Declarar ZIP solo evidencia o facilitar binarios | Resuelve la incertidumbre de respaldo | P0 | Sí |
| D-03 | Clasificar TITAN, Cytryna, Laboratorio y Equipo del gAto | Cierra ambigüedad de alcance | P1 | Parcialmente; afecta clasificación final |
| D-04 | Autorizar piloto de handoffs y dependencias | Mejora continuidad y responsabilidad | P2 | No |
| D-05 | Autorizar experimento SOFTLY-MIN | Prueba núcleo mínimo portable | P2 | No |
| D-06 | Mantener tres dimensiones y probar hipótesis sistémica | Evita reabrir arquitectura prematuramente | P2 | No; la decisión inicial ya existe |
| D-07 | Asignar o conservar paquetes de capacidades | Define uso futuro de capacidades históricas | P3 | No |
| D-08 | Proteger ramas main | Reduce riesgo de regresión | P3 | No |

## 7. Fuentes primarias

- [RESET-CORE-2026-002, versión 1.2.0](https://github.com/gatoscientist/Softly/blob/main/docs/governance/RESET-CORE-2026-002.md)
- [CHECKPOINT de Softly](https://github.com/gatoscientist/Softly/blob/main/CHECKPOINT.md)
- [Informe 22 de Audeline: corte final residual](https://github.com/gatoscientist/Audeline/blob/main/reports/RESET-CORE-2026-002/22-AUDELINE-CORTE-FINAL-ESTADO-RESIDUAL-2026-11-16.md)
- [Informe 23 de Audeline: manifiesto de preservación de ramas](https://github.com/gatoscientist/Audeline/blob/main/reports/RESET-CORE-2026-002/23-AUDELINE-MANIFIESTO-PRESERVACION-RAMAS-2026-11-16.md)
- [Adenda de clasificación TITAN/Cytryna/gAtoSD](https://github.com/gatoscientist/Audeline/blob/main/reports/RESET-CORE-2026-002/04-AUDELINE-ADENDA-PROYECTOS-TITAN-CYTRYNA-GATOSD-2026-11-16.md)
- [Registro v2 de identidades y capacidades](https://github.com/gatoscientist/Softly/blob/main/schemas/identity-capability-registry-v2.json)
- [Recomendaciones KFB de Katarina](2026-11-16-KAT-SOFTLY-FUTURE-BLOCKERS-2026-001-recomendaciones.md)
- [Investigación SOFTLY-MIN](https://github.com/gatoscientist/Softly/blob/main/research/syntheses/2026-11-16-softly-min-nucleo-minimo-y-equivalencia-funcional.md)

**Conclusión final:** gAto no necesita volver a dirigir cada tarea. Para cerrar el reset, los aportes directos de mayor impacto son resolver el acceso al retiro de ramas, decidir el estatus probatorio de los ZIP y fijar las fronteras de los proyectos ambiguos. Para abrir la siguiente etapa, basta elegir entre el piloto de coordinación documental y el experimento SOFTLY-MIN. El resto corresponde a ejecución de Softly, Katarina y Audeline dentro de sus mandatos.
