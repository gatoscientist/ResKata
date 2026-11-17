# Revisión técnica de capacidades y migración del registro v2

**Misión:** KAT-RESET-002-REGISTRY-V2  
**Emite:** Katarina · identidad `katarina` · versión documental 3.1.0  
**Destinatario:** Softly, por despacho técnico  
**Autoridad:** Dictamen de Dirección — Destrabe de RESET-CORE-2026-002, 2026-11-16  
**Estado:** revisión técnica documental completada; correcciones requeridas antes de integrar  
**Alcance:** contraste de contratos, perfiles, registro y schema; sin modificar la rama de migración, sin activar paquetes y sin fusionar PR.

## 1. Dictamen ejecutivo

La migración va en la dirección correcta y cumple, en los datos inspeccionados, la restricción central de tres identidades operativas: Softly, Katarina y Audeline. Los paquetes candidate-unassigned permanecen sin autoridad, sin herencia y separados de las identidades. Zoe aparece en una asignación temporal y no como identidad operativa.

La preservación de la versión 1.0.0 está demostrada por identidad exacta de blobs:

- Registro original y copia archivada: `ceca667cfb912a0f7c43b32ee0eead86030b4b5f`.
- Schema original y copia archivada: `9230b5f034ffe96c1835e065d4184828c2ba8c63`.

**Dictamen técnico sobre la migración: GO CON RESERVAS.** No recomiendo integrar todavía. Hay dos correcciones estructurales necesarias en el schema y en la designación del registro canónico. La revisión independiente de Audeline sigue siendo obligatoria y no queda sustituida por este informe.

## 2. Corte y evidencia inspeccionada

### 2.1. Softly

Corte observado durante la revisión:

- Rama de migración: `migration/registry-v2-reset-core-002`.
- HEAD observado del PR #8: `0ea99c78a4aecb1905c7156a0aad55eb533cb654`.
- `main` observado: `fc512e1913b8004bd743d2b5ee1a612d965a64ba`.
- Comparación: 12 commits adelante y 14 detrás; estado divergente.
- PR #8: abierto, no fusionado, GitHub informó `mergeable: false`.
- El PR mantiene expresamente la condición de no fusionar antes del dictamen independiente favorable de Audeline.

Artefactos de migración releídos:

- `schemas/agent-taxonomy-registry.json`, blob `8057b3d1666f3781a212f1858843db2569f27c65`.
- `schemas/agent-taxonomy.schema.json`, blob `670d2d94f13ccbedc2c0688afaadb18f5978d87b`.
- `schemas/archive/agent-taxonomy-registry-1.0.0.json`, blob igual al original `ceca667cfb912a0f7c43b32ee0eead86030b4b5f`.
- `schemas/archive/agent-taxonomy.schema-1.0.0.json`, blob igual al original `9230b5f034ffe96c1835e065d4184828c2ba8c63`.
- El `main` inspeccionado conserva además `schemas/identity-capability-registry-v2.json` (blob `8cc9536f9659d7f27103060a67d6a0f5d194971b`) y `schemas/identity-capability-registry-v2.schema.json` (blob `e6fa81622057395a5aa6d8200635838e31034827`).

### 2.2. Contratos canónicos

- Katarina 3.1.0: `gatoscientist/Katarina/core/AGENT.md`, blob `3a67c7ae305b944751d926c80fae655824c8596b`; `core/CONTRACT.md`, blob `a5f52e6a3045f3cdd0cf559c9db65b0226422af1`; `core/PERMISSIONS.md`, blob `0bf88a130a5b931a5cf7b19893df8a6e8cccfca2`.
- Softly: `gatoscientist/Softly/SOFTLY.md`, blob `b0f7070e7d4079796959ce6a4e9ca962ad068ca2`.
- Audeline: `gatoscientist/Audeline/Audeline/AGENT.md`, blob `0501685c4a317c7b4ab2d876a6f676451c42010c`; `Audeline/CONTRACT.md`, blob `a5dd08ceb805d6206ec94dd9434b1aca2d373988`; `Audeline/PROFILE.md`, blob `a8248eafe915c7f29ae69919534332881ff65bf7`.

### 2.3. Paquetes fuente consultados

Se inspeccionaron documentos declarativos, no implementaciones ni resultados de pruebas:

- Tiffany: `AGENT.md` `54553db1f3a425e240b4fdebe2252a243e69035f`; `CONTRACT.md` `8c70e3dd9c3b6d594c58938e73527b5f664b0d1a`; `PROFILE.md` `4398c463058021d88b2b57e3bffbaff256ec63f6`.
- Tara: `AGENT.md` `ddf17675639d1b09aa7bb80cc79ec130243c54a3`; `CONTRACT.md` `3b1ca4bb2461e00ed589d2101ad4fe6cfee0b2f7`; `PROFILE.md` `91d43a9c809467f69c65bf2c12fe32190e92ae65`.
- Tábata: `AGENT.md` `976d7026574be59b54a4ce6ecd75b7c65ea85e50`; `CONTRACT.md` `d03bafc3be53a63f71bd11b7a841fda94a5547ef`; `PROFILE.md` `f561811110ad87e26dc73fdaf6bfa99b48be2ccb`.
- Thea: `CONTRACT.md` `df5813d34095fda84ecb04782fca83029384db16`; `PROFILE.md` `7ea5faaa798167a3d6626dc24fe35110d6e09c52`.
- Melina: `CONTRACT.md` `f1e7275e3a5dd97e54fc856118712d7aab270b71`; `PROFILE.md` `bb6ea6903874d1e31c6c7addb7b7f2e460dcaed3`.
- Aurora: `CONTRACT.md` `2aabde5b3a8d0661583a90464a0cbfb497312204`; `CAPABILITIES.md` `2403f66187c3ea876add99327afe35561c9b058d`.
- Autumn: `CONTRACT.md` `7797b5eb60d3f481717103c2b48bcf2114bdabfb`; `CAPABILITIES.md` `2c00f555a1b64e6c0c66ba219aa90d9f1d173b57`.

Los contratos y perfiles de paquetes describen misiones y competencias requeridas. No aportan, por sí solos, certificaciones, evaluaciones aprobadas ni pruebas de ejecución.

## 3. Hallazgos de estructura y schema

### H-01 — El schema no garantiza exactamente una instancia de cada identidad

**Severidad:** alta; corrección requerida antes de integrar.

La propiedad `identities` exige `minItems: 3` y `maxItems: 3`, y cada elemento limita `identity_id` a `softly`, `katarina` o `audeline`. Sin embargo, no define `uniqueItems` ni reglas `contains` que exijan exactamente una aparición de cada ID. Por tanto, tres entradas `softly` satisfacen las restricciones visibles del arreglo, aunque falten Katarina y Audeline.

**Corrección propuesta:** conservar cardinalidad 3 y agregar:
- `uniqueItems: true` como defensa adicional;
- tres reglas `contains`, cada una con `minContains: 1` y `maxContains: 1`, para `softly`, `katarina` y `audeline`;
- `required: [identity_id]` dentro de cada subesquema `contains`.

El schema v2 anterior que permanece en `main` ya utiliza una estrategia de `contains` para exigir las tres identidades. Puede servir como referencia, no como sustituto de la corrección y revisión del nuevo schema.

### H-02 — Dos registros v2 compiten por la condición de canónico

**Severidad:** alta; resolver antes de integrar.

La rama de migración transforma `schemas/agent-taxonomy-registry.json` en el registro v2 y cambia `schemas/agent-taxonomy.schema.json`. Sin embargo, `main` conserva `schemas/identity-capability-registry-v2.json` y su schema, también declarados como v2. Los dos modelos no tienen la misma estructura.

**Corrección propuesta:** declarar una única ruta canónica en el documento de migración y en el índice. Marcar la otra pareja de archivos como antecedente supersedido y archivarla o retirarla de la superficie normativa mediante un cambio trazable. No borrar su historia ni dejar dos fuentes que puedan interpretarse como autoridad simultánea. Antes de retirarla, confirmar si algún documento o consumidor la referencia.

### H-03 — Semántica contradictoria entre aprobación y autorización

**Severidad:** media.

El schema permite el estado `approved-capability`, pero exige en todos los casos que `authorization` sea `none-until-explicit-contract-mapping-and-independent-review`. El nombre del estado puede interpretarse como aprobación, mientras que el campo de autorización afirma que todavía no existe.

**Corrección propuesta:** o bien retirar `approved-capability` del enum hasta que exista una etapa posterior de mapeo contractual, o separar explícitamente `review_status` de `operational_authorization`. Una capacidad aprobada documentalmente no debe quedar confundida con una capacidad autorizada para uso operativo.

### H-04 — Referencias cruzadas insuficientemente restringidas

**Severidad:** media.

Los campos `domain_id`, `source_package_ids` y `proposed_identity_ids` tienen restricciones de tipo/enum, pero el schema no garantiza por sí solo que los dominios y paquetes referidos existan, que los IDs de dominios/paquetes/capacidades sean únicos ni que cada perfil tenga una procedencia coherente.

**Corrección propuesta:** añadir validación referencial en un validador complementario o reforzar el schema donde sea viable. Como mínimo, exigir unicidad de IDs en el proceso de validación y comprobar que todo `domain_id` y `source_package_id` referenciado exista. Registrar el resultado reproducible de esa validación en el PR.

### H-05 — La estructura actual de los datos sí respeta el límite de tres identidades

**Severidad:** informativo favorable.

El JSON v2 parsea correctamente y contiene exactamente los IDs `softly`, `katarina` y `audeline`, sin duplicados en el documento actualmente inspeccionado. Los paquetes fuente están marcados `candidate-unassigned` o `historical-source`, con `operational_authority: false` / `no-operational-authority` y `inheritance: none`. La asignación de Zoe está separada en `temporary_assignments`.

Esto acredita el contenido del archivo inspeccionado, no la suficiencia del schema ni la validación integral de la migración.

## 4. Dictamen de capacidades por identidad

La recomendación distingue capacidad reutilizable, destino contractual y evidencia de competencia. Ningún paquete fuente recupera identidad, autoridad, permiso, invocación ni delegación.

### 4.1. Katarina — ingeniería y desarrollo

**Compatibles como perfiles candidatos, sujetos a asignación concreta:**

1. **WPF, XAML, GUI e integración de componentes.** Tiffany declara WPF/XAML, MVVM cuando corresponda, integración GUI/lógica, C#/.NET según stack y mantenibilidad. Es compatible con ingeniería de software de Katarina. La parte WPF es una especialización condicionada a que un encargo futuro use ese stack; no incorpora el proyecto TITAN ni su misión.
2. **PowerShell avanzado para automatización, inspección y diagnóstico.** Compatible con ingeniería y scripting. El perfil fuente lo declara como competencia requerida, no demostrada; se debe evaluar con tareas y evidencia antes de afirmar dominio acreditado.
3. **Ingeniería de transporte seguro, TLS y aislamiento.** La implementación, configuración y corrección de controles técnicos puede ser propuesta a Katarina dentro de ingeniería de software/seguridad, con alcance y pruebas específicos. No incluye certificación independiente de seguridad.

**No incorporar como responsabilidad automática:** tareas, componentes, arquitectura, reglas de producto ni dependencias específicas de TITAN. La compatibilidad de una técnica no incorpora el proyecto de origen.

### 4.2. Audeline — auditoría independiente

**Compatibles como perfiles candidatos:**

1. **Auditoría estática de PowerShell/AST.** Revisión de construcción de comandos, AST, argumentos, texto dinámico y rutas de ejecución, con distinción explícita entre análisis estático y ejecución observada.
2. **Análisis de integridad de leases y hashes.** Revisión de vinculación, expiración, consumo único, replay, concurrencia, invalidación y trazabilidad. No confundir integridad criptográfica con autorización o seguridad semántica.
3. **Auditoría de TLS, transporte y aislamiento.** Verificación independiente de protocolos, certificados, cadenas de confianza, configuración de clientes, fronteras de contexto, enrutamiento y exposición de información.
4. **Integración de evidencia y control de alcance.** Es coherente con el contrato canónico actual de Audeline, que ya le asigna consolidar auditorías, preservar autoría, filtrar desproporción y emitir dictamen.

Aurora y Autumn no deben reaparecer como identidades, delegadas ni dependencias. Sus documentos son fuentes históricas. Audeline realiza directamente el trabajo que su contrato vigente le asigna. Las competencias técnicas declaradas por Autumn y las funciones de medición declaradas por Aurora no se consideran demostradas por la sola existencia de sus contratos.

### 4.3. Softly — núcleo, gobierno y coordinación

**Compatibles como capacidades candidatas:**

1. **Coordinación sistémica transversal.** Puede precisar la coordinación general que ya corresponde a Softly: dependencias entre repositorios, coherencia de decisiones, continuidad, estado compartido y resolución de bloqueos. Debe definirse mediante responsabilidades, observables, entradas/salidas y límites claros frente a la auditoría independiente de Audeline y la ingeniería de Katarina.
2. **Lectura de grafos y flujos de información para coordinación.** Softly puede utilizar modelos de dependencias y flujos para gobernar la secuencia y continuidad del trabajo. La evaluación independiente de evidencia y la emisión de hallazgos siguen siendo de Audeline.
3. **Secuenciación, turnos y temporalidad a nivel de coordinación.** Puede ser un recurso de planificación documental, pero no debe importar el sistema de turnos de TITAN ni atribuir a Softly una implementación técnica que corresponde a ingeniería.

La etiqueta `systems-coordination` debe permanecer candidata hasta que Softly la reconcilie con su contrato de orquestación y defina observables y fronteras. No se propone una cuarta identidad ni una nueva estructura subordinada.

## 5. Capacidades que deben permanecer sin asignación

- **Thea y Melina — música, audio y ciencias sonoras:** mantener `candidate-unassigned`. No hay mandato musical vigente dentro de los contratos de las tres identidades. Thea está descrita en el contexto de TITAN; Melina se declara generalista musical independiente de proyectos. Ninguna de esas procedencias autoriza trasladar sus proyectos o misiones.
- **Capacidades de dominio específico de TITAN:** no migrar por semejanza de nombres ni por reutilización técnica. La revisión se limita a proponer perfiles genéricos y no altera la clasificación o el alcance del proyecto de origen.
- **Aurora y Autumn:** conservar como fuentes históricas sin autoridad. Las funciones de integración de evidencia, control de alcance y auditoría técnica que sean compatibles se asignan documentalmente a Audeline, no a los paquetes fuente.

## 6. Recomendación de cambios al registro

1. Mantener los paquetes fuente sin autoridad operativa y sin herencia.
2. Mantener perfiles compatibles en `proposed-for-review`; música/audio en `candidate-unassigned`.
3. No usar `approved-capability` hasta que exista un mapeo contractual explícito, evidencia de competencia y revisión independiente.
4. Separar en cada perfil las capacidades de ingeniería (Katarina), coordinación (Softly) y auditoría independiente (Audeline).
5. Evitar propuestas duplicadas de grafos/flujo/temporalidad sin indicar qué resultado corresponde a cada identidad.
6. Mantener la asignación temporal de Zoe activa hasta que se cumplan ambas condiciones: dictamen final independiente de Audeline y confirmación expresa de Dirección.

## 7. Estado de ramas, PR y limitaciones técnicas localizadas

### Katarina

- Ramas observadas: `main` y `kat-006-stage3-softly-2026-11-16`.
- La rama histórica conserva 8 commits exclusivos y divergencia significativa respecto de `main`.
- PR #1 está cerrado y no fusionado. No se reabre ni se usa como requisito de avance.
- La rama adicional no puede eliminarse mediante las acciones disponibles en la conexión actual; se conserva como evidencia. No se declara consolidación de rama única.

### Softly

- Ramas observadas: `main`, `fix/f03-recover-ledger`, `migration/registry-v2-reset-core-002` y `recovery/AUD-20261116-001`.
- PR #8 sigue abierto y no fusionado; al corte indicado está divergente y no fusionable.
- PR #4 aparece cerrado y no fusionado.
- La rama de migración no debe eliminarse ni fusionarse antes de la revisión independiente y las correcciones.
- La conexión permitió leer refs, pero la lectura del endpoint de protección de `main` devolvió HTTP 403 (`Resource not accessible by integration`). Por tanto, el estado de protección de rama no pudo verificarse.
- La conexión actual no expone una operación de eliminación de refs/ramas. No se ha eliminado ninguna rama.

### ZIP y otros respaldos binarios

La conexión rechaza respuestas binarias/no UTF-8 y no permite descargar ni verificar el contenido de los ZIP. Esta limitación impide calcular hashes o ejecutar una restauración aislada desde esta conexión. Debe registrarse como limitación técnica localizada, sin detener las tareas documentales, revisión de PR ni consolidaciones que sí puedan ejecutarse.

## 8. Verificaciones realizadas y no realizadas

**Realizadas:**
- Relectura de los contratos y perfiles canónicos de las tres identidades.
- Relectura de los perfiles fuente citados.
- Parseo JSON de los archivos de registro y schema inspeccionados.
- Comparación exacta de los SHA de registro/schema 1.0.0 con sus copias archivadas.
- Inspección estática de restricciones de cardinalidad, IDs y estados del schema v2.
- Lectura de refs, PR y comparación de ramas en Katarina y Softly.

**No realizadas:**
- No se ejecutó un validador completo de JSON Schema Draft 2020-12 ni una suite de fixtures.
- No se probaron competencias profesionales de los paquetes fuente.
- No se fusionó el PR #8 ni se modificó su rama.
- No se eliminaron ramas.
- No se verificó la configuración de protección de `main` por falta de acceso.
- No se descargaron ni restauraron ZIP.
- No se realizó auditoría independiente; corresponde a Audeline.

## 9. Acciones requeridas y responsables

| Acción | Responsable | Estado |
|---|---|---|
| Corregir unicidad y presencia exacta de las tres identidades en el schema | Softly | Requerido |
| Designar una sola ruta canónica v2 y archivar/retirar el registro v2 intermedio | Softly | Requerido |
| Resolver semántica de estado aprobado frente a autorización operativa | Softly | Requerido |
| Añadir validación de referencias cruzadas y unicidad de IDs | Softly | Recomendado antes de integrar |
| Reconciliar la rama de migración con el `main` actual sin perder evidencia | Softly | Pendiente |
| Completar dictamen independiente del registro y sus perfiles | Audeline | Pendiente |
| Incorporar solo perfiles candidatos compatibles, sin activar paquetes | Softly, con contraste técnico de Katarina | Pendiente |
| Resolver eliminación de ramas y lectura de protección mediante acceso con permisos suficientes | Dirección/administración del repositorio | Limitación localizada |
| Resolver inspección binaria de ZIP mediante entrega accesible de los archivos | Dirección | Limitación localizada |

## 10. Conclusión

El contenido de la migración ya refleja las tres identidades autorizadas y preserva exactamente el registro histórico 1.0.0. Las propuestas de capacidades pueden continuar sin reactivar paquetes ni ampliar identidades.

La integración debe esperar a que Softly corrija las debilidades del schema y elimine la ambigüedad entre los dos registros v2. Audeline debe emitir su dictamen independiente sobre la versión corregida. El trabajo de ramas, PR, respaldos y protección de `main` continúa en paralelo dentro de las competencias disponibles; las limitaciones de acceso no suspenden estas tareas.

**Dictamen:** GO CON RESERVAS para continuar correcciones y revisión; NO-GO para fusionar el PR #8 en el estado observado. Zoe permanece temporal hasta dictamen final de Audeline y confirmación expresa de gAto.

---

**Emite:** Katarina · `gatoscientist/Katarina`  
**Corte técnico:** PR #8 HEAD `0ea99c78a4aecb1905c7156a0aad55eb533cb654`; Softly main `fc512e1913b8004bd743d2b5ee1a612d965a64ba`.  
**Nota de concurrencia:** Softly estaba actualizando la rama durante la revisión; las referencias SHA anteriores identifican el corte inspeccionado, no afirman que la rama permanezca inmóvil.
