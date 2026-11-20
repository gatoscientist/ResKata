# Katarina — Checkpoint de continuidad y estado transversal Zoftly
Fecha: 2026-11-20
Instancia: Katarina 0.2.0-experimental
Casa: gatoscientist/ResKata, rama main
Checkpoint anterior preservado: 2026-11-19-deliberation-and-zoftly.md
Estado: continuidad registrada; integración Zoftly no aceptada ni terminada

## 1. Precedencia y propósito

Este checkpoint complementa, no reemplaza, el checkpoint del 2026-11-19. El checkpoint anterior conserva la deliberación sobre cómo aprender de los errores, el trato entre colegas y el estado de Contract Discovery 0.1.0. Ese trabajo histórico no debe confundirse con el mandato actual de integración del Director de Zoe en la GUI de Softly.

La fuente operativa de la integración actual es Cytryna issue #15:
https://github.com/gatoscientist/Cytryna/issues/15

Este documento registra decisiones, estado verificable, bloqueos y continuidad. No declara aceptación, ejecución autónoma de otras instancias ni pruebas que no tengan evidencia.

## 2. Identidad, autoridad y reglas de colaboración

- gAto conserva autoridad estratégica y decisión final.
- Katarina dirige la integración transversal y responde por la coherencia, revisión y aceptación integral dentro del mandato.
- Camila conserva autoridad técnica y decisión de implementación de la GUI.
- Zoe conserva autoridad técnica sobre Director, runtime propio, CLI y contrato de integración.
- Softly aporta contraste independiente y protege la integridad del sistema.
- Las responsabilidades no se sustituyen por conveniencia. Katarina no debe apropiarse de la GUI ni modificarla directamente después de la instrucción expresa de respetar la autoridad técnica de Camila.
- Regla de trato: hard con el problema, soft con la persona. El desacuerdo técnico es legítimo; cambiar de opinión ante evidencia es aprendizaje.
- Escuchar las posiciones completas antes de concluir. No confundir extensión argumental con corrección.
- No crear tareas o burocracia para justificar revisiones. Reconocer expresamente lo que ya está resuelto.
- Distinguir siempre mandato, propuesta, deliberación, publicación, implementación, prueba, verificación y aceptación.
- No afirmar sesiones activas, comunicaciones, lecturas, commits autónomos, pruebas o despliegues sin evidencia directa.

## 3. Mandato y alcance actual de Zoftly

Objetivo: cerrar la integración funcional entre el Director de Zoe y la GUI de Softly, reutilizando el puente IPC local existente y manteniendo las consultas tipadas read-only.

Alcance:
- GUI Softly consume el CLI de diagnóstico de Zoe.
- Diagnóstico admite scopes runtime, project y both.
- GUI muestra informe estructurado completo, incluidos estado, fecha, evidencia, errores, cuatro dictámenes y limitaciones.
- Operación fuera del hilo visual, con timeout, salida acotada, cancelación y cierre de proceso controlados.
- Se reutiliza el puente Softly existente; no se crea un segundo IPC.
- PowerShell manual permanece separado y requiere confirmación explícita.
- No se incorporan scripts arbitrarios, ejecución privilegiada, servicios residentes ni expansión multi-Softly.
- No se incorporan TaskStore, Authorization Core o WebAuthn sin necesidad demostrada.

Fuera de alcance para Katarina:
- Runtime permanece excluido de su mandato general.
- No modificar el núcleo canónico de Softly ni ampliar alcance.
- No modificar la GUI de Cytryna por encima de la autoridad de Camila.
- No fusionar PRs ni declarar aceptación sin evidencia y autorización correspondiente.

## 4. Contrato de integración Zoe ↔ GUI

Contrato publicado en Zoe main:
https://github.com/gatoscientist/Zoe/blob/main/contracts/softly_gui_integration.md
Commit del contrato: ab5e23ec21495857a4a8d81e2de15f126d181910

Interfaz:
- CLI: python -m zoe_runtime diagnostic --scope runtime|project|both
- Schema del informe: zoe-director-report/1
- Configuración explícita de SOFTLY_ROOT para reutilizar el LocalDirectorBridge existente.
- Exit code 0: informe verified.
- Exit code 1: informe JSON válido incomplete. La GUI debe parsearlo y mostrarlo; no descartarlo como error de lanzamiento.
- Exit code 2 / salida ausente o malformada: error de argumentos/invocación según el caso.
- Timeout, fallo de lanzamiento/transporte, reporte malformado e informe incomplete son estados distintos.
- 35 s por operación IPC (30 s máximo interno del puente + 5 s de margen).
- scope=both ejecuta dos operaciones secuenciales; timeout externo GUI mínimo de 75 s.

Dependencia funcional: Zoe main todavía usa SoftlyClient(timeout=10.0). La corrección a 35 s está en Zoe PR #11, aún Draft y sin merge. End-to-end no se puede aceptar hasta integrar o desplegar inequívocamente esa versión y validarla.

## 5. Estado transversal de PRs al 2026-11-20

Todos los estados siguientes fueron consultados directamente en GitHub durante esta sesión. Los cuatro PR están abiertos, Draft, sin merge y reportados mergeable=true en el snapshot consultado. Mergeable no significa probado ni aceptado.

### Zoe PR #11 — contrato CLI, pruebas y timeout
https://github.com/gatoscientist/Zoe/pull/11
- Rama: zoe/director-cli-contract-tests
- HEAD: 0b162d8c2fd6fd09a843b7ecc1c4ae9ca9c3b868
- 7 commits, 4 archivos.
- Contiene pruebas de verified, incomplete con exit code 1, scope inválido, error de transporte y timeout.
- Eleva SoftlyClient a 35 s por operación y documenta al menos 75 s para GUI scope=both.
- El cambio resuelve documentalmente y en la rama la jerarquía de timeouts; pruebas aún sin ejecución verificable.
- CI run #5, ID 44660168364: seis jobs fallidos sin steps/logs recuperables. No demuestra que compileall/unittest hayan comenzado.
- Katarina no debe fusionar ni modificar el repositorio Zoe por iniciativa propia. Zoe conserva autoridad técnica.

### Cytryna PR #20 — propuesta GUI Director
https://github.com/gatoscientist/Cytryna/pull/20
- Rama: katarina/zoe-director-gui-integration
- HEAD: 59a393d7969b65139b27cd3a96140eaa6fd64457
- 14 commits, 5 archivos.
- Añade propuesta de pestaña Director, invocación del CLI mediante sys.executable, vector de argumentos, shell=False, timeout 75 s, SOFTLY_ROOT, entorno hijo mínimo sin claves API, validación del schema/campos/scope/cuatro dictámenes y redacción de secretos.
- PR abierto, Draft, sin merge. GitHub atribuye los commits a la cuenta gatoscientist; eso no acredita una sesión autónoma de Katarina ni de Camila.
- Camila conserva autoridad técnica GUI. Katarina no hará más cambios directos a esa capa.
- Hallazgos pendientes para Camila:
  1. El límite de salida se comprueba después de communicate(), que ya acumuló stdout/stderr completos. No limita el consumo de memoria durante captura. Se requiere captura acotada mientras se lee o mecanismo equivalente que termine el proceso al superar el límite.
  2. close() solicita terminate(), pero no espera un tiempo acotado ni escala a kill() si el proceso no termina. Debe resolverse sin bloquear el hilo Tk.
  3. Faltan pruebas deterministas de Popen/lanzamiento, timeout, stdout y stderr excesivos, cierre concurrente y recuperación del estado de controles.
- La validación end-to-end depende de Zoe #11 integrada y de Windows.
- No hay revisión formal registrada en la consulta; los hallazgos están en comentarios del PR.

### Cytryna PR #16 — aprobación por llamada de herramientas
https://github.com/gatoscientist/Cytryna/pull/16
- Rama: feature/gui-tool-approval-mainline
- HEAD: b851347552f6b6c5427c27f24d1f05821d8f1e79
- 19 commits, 7 archivos.
- Sustituye PR #14, que fue cerrado como reemplazado y no mergeado.
- La implementación incorpora aprobación individual, denegación por defecto, guardas de cierre, bloqueo compartido para solicitudes pendientes y redacción de salida CLI.
- Pruebas añadidas cubren denegación, callback, redacción, propuestas múltiples, cierre y estado disabled/readonly de controles.
- Falta una prueba de concurrencia real: iniciar un turno, mantener una aprobación pendiente, intentar un segundo send_message() y verificar que no aparece un segundo worker ni una segunda llamada chat_turn; luego resolver y comprobar que solo el turno original finaliza.
- Hallazgo nuevo de comentario 7029043791: la ruta manual /ejecutar llama execute_tool_cli() y tools.run() directamente sin pasar por _approve_cli_tool. /planes reutiliza esa ruta. Debe decidirse explícitamente si el comando manual constituye consentimiento suficiente o si toda ejecución CLI exige aprobación uniforme; documentar y probar /ejecutar y comandos derivados.
- Tool.permissions sigue siendo metadato declarativo, no enforcement central. No describirlo como autorización efectiva por scopes.
- CI run #521, ID 44659677539: nueve jobs failure sin steps/logs recuperables; no es PASS ni evidencia de que unittest haya empezado.
- Mantener Draft hasta resolver ambos puntos, obtener CI diagnosticable y validación Windows.

### Cytryna PR #19 — endurecimiento del puente IPC
https://github.com/gatoscientist/Cytryna/pull/19
- Rama: zoe/ipc-loopback-fallback-response-limit
- HEAD: 654efbd06e61043af3720161ad74f215fe30b8e0
- 9 commits, 2 archivos.
- Añade fallback AF_UNIX a TCP loopback solo ante errores reconocidos de soporte/path length; permisos/configuración fallan cerrados.
- TCP queda limitado a 127.0.0.1 y puerto efímero.
- Respuestas JSON del servidor acotadas; cliente rechaza respuestas excesivas o incompletas.
- PR abierto, Draft, sin merge. Tests no ejecutados de forma verificable.
- Es hardening útil, pero no se debe confundir con la dependencia funcional principal de GUI Director.

## 6. CI y validación

- Los runs recientes de Cytryna PR #16, #19 y #20 aparecen fallidos en sus matrices, pero la API devuelve jobs sin steps/logs utilizables; en algunos casos steps=[] y runner_id=0.
- Zoe PR #11 presenta el mismo patrón, con seis jobs fallidos sin steps/logs recuperables.
- Run Cytryna #534, ID 44664279645, nueve jobs; run #535 corresponde a PR #19 según comentarios de revisión. Runs #527–#533 de PR #20 presentaron patrón equivalente.
- No hay evidencia de que checkout, setup-python, instalación, compileall o unittest hayan comenzado.
- La causa exacta de la falla previa a ejecución no está identificada. No atribuirla al código ni afirmar que es infraestructura confirmada.
- Estado global de validación: bloqueado / no diagnosticable / no verificado. No PASS.
- Windows integrado sigue pendiente: arranque Softly, puente IPC, invocación Director, visualización GUI y cierre limpio.
- Los tests escritos no equivalen a tests ejecutados. Mergeable no equivale a aceptación.

## 7. Orquestación y disponibilidad de agentes

El issue #15 pide que Camila y Zoe coordinen directamente y ejecuten sus ciclos con autonomía, sin trasladar al gAto la administración cotidiana. Sin embargo:
- Los comentarios visibles del issue #15 y PRs consultados son de la cuenta gatoscientist.
- No hay revisiones registradas ni reviewers solicitados en los cuatro PR en la consulta actual.
- La publicación de issues, comentarios, ramas o commits no despierta sesiones ni acredita lectura/aceptación.
- No hay mecanismo disponible en esta sesión para activar sesiones reales de Camila o Zoe.
- Por tanto, no afirmar que sus instancias están apagadas; sí afirmar que no existe evidencia GitHub de ejecución autónoma o de respuesta de ellas en este trabajo.
- Esta brecha es un problema de orquestación/entrega de señales: contratos y artefactos publicados no garantizan recepción, ejecución ni devolución. No ocultar esa limitación creando más PRs.
- El gAto no debe convertirse en administrador técnico cotidiano. Escalarle solo conflictos de autoridad, alcance o decisiones estratégicas que no puedan resolverse dentro del mandato.

## 8. Secuencia de cierre y criterios de aceptación

1. Zoe resuelve, valida y entrega su cambio de timeout/contrato en #11; no aceptar el consumidor GUI contra el main de Zoe que todavía usa 10 s.
2. Camila revisa y conduce la implementación GUI, resolviendo los tres hallazgos de ciclo de proceso de #20. Katarina aporta revisión transversal, no ownership de GUI.
3. Camila resuelve el test de doble envío y la semántica de /ejecutar y /planes en #16; mantener clara la diferencia entre aprobación humana, permisos declarativos y enforcement.
4. Evaluar #19 como hardening del puente y validar su compatibilidad; no convertirlo automáticamente en bloqueo si no se demuestra dependencia.
5. Obtener CI con runner, steps y logs recuperables o ejecución local reproducible y documentada.
6. Ejecutar en Windows el flujo completo: inicio Softly, puente, diagnóstico Zoe, informe completo en GUI, estados de error/incomplete y cierre limpio.
7. Katarina contrasta las versiones reales integradas, revisa contrato, seguridad, documentación y evidencia, y emite aceptación o rechazo fundamentado.
8. Solo después de satisfacer criterios y autoridad correspondiente se considera integración terminada. No fusionar PRs por el mero hecho de que sean mergeable.

Criterios de aceptación del issue #15:
- GUI consume el contrato de Zoe y presenta diagnóstico completo.
- Director usa consultas tipadas read-only existentes.
- PowerShell manual permanece separado y explícitamente confirmado.
- Flujo de aprobación de herramientas revisado y resuelto.
- Tests automatizados cubren integración y estados de error.
- Flujo completo validado en Windows con comandos, resultados, logs y códigos de salida.
- Katarina revisa integración, seguridad, documentación y aceptación final.

## 9. Próxima acción habilitada para Katarina

Sin invadir la GUI ni runtime:
- Mantener el checkpoint y el mapa de dependencias.
- Revisar evidencia nueva que aparezca en PR #11, #16, #19 y #20.
- Hacer contraste contractual transversal cuando Camila/Zoe publiquen cambios verificables.
- No crear trabajo duplicado ni seguir editando GUI.
- Si la ausencia de recepción/ejecución impide avanzar, documentar la limitación real de orquestación; no fingir que un comentario GitHub equivale a una convocatoria atendida.

## 10. Trazabilidad de este checkpoint

Línea base ResKata/main consultada antes de escribir: 8bbac13a38e2de0c311d7010c9e941f7f2e541e4.
Los documentos normativos consultados fueron Katarina/README.md, core/AGENT.md, CONTRACT.md, PERMISSIONS.md, INSTANCE.md, PROFILE.md, OPERATING-PROCEDURE.md, version.json, shared/README.md, shared/bitacora.md, shared/DELIBERATION-START.md y shared/2026-11-17-handoff-estigmergia-deliberacion.md.
Checkpoint previo consultado: Katarina/checkpoints/2026-11-19-deliberation-and-zoftly.md.
La revisión de este checkpoint no modifica ni acepta ninguno de los PR externos.
