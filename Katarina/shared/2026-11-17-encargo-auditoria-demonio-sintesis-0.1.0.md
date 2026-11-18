# Encargo de auditoría independiente: Demonio de Síntesis 0.1.0

**Destinataria:** Katarina  
**Emisora:** Softly  
**Repositorio de implementación:** gatoscientist/SoftlyLab  
**Prioridad:** Alta  
**Estado:** Solicitud de revisión

## Objetivo
Auditar con criterio crítico el primer prototipo del Demonio de Síntesis. No abrir deliberación teórica ni ampliar alcance. Revisar el código, la especificación, el delta inicial y HOT-CHECKPOINT.

## Archivos
- `demonio-sintesis/SPEC-0.1.0.md`
- `demonio-sintesis/tools/synthesizer.py`
- `demonio-sintesis/tests/test_synthesizer.py`
- `demonio-sintesis/deltas/2026-11-17/DELTA-2026-11-17-GLOSARIO-001.json`
- `demonio-sintesis/HOT-CHECKPOINT.md`

## Fuentes originales que deben comprobarse
- Dictamen firmado: `2026-11-17-dictamen-gato-aprobacion-glosario-tecnico-softly-0.1.0.md`, blob `2bc262404a055fe6a706d5deb4c14701bfeb898d`.
- Glosario vigente: `2026-11-17-glosario-tecnico-softly-0.1.0-propuesto.md`, blob `311deb2fc3c114ce4911729562474c4412bc0136`.

## Dagas obligatorias
1. ¿Puede una hipótesis o conversación exploratoria entrar como decisión ratificada?
2. ¿Puede un resumen o delta convertirse en fuente única de una decisión posterior?
3. ¿Se conservan punteros inmutables completos hasta la fuente original?
4. ¿La salida del demonio queda excluida de futuras ingestas mediante `actor_type: daemon_synthesizer`?
5. ¿Se evita la autoingesta aunque el delta se encuentre dentro del árbol que el demonio inspecciona?
6. ¿Se evitan borrados, movimientos o escrituras destructivas ante carreras?
7. ¿El HOT-CHECKPOINT respeta el límite de 100 líneas y no suplanta autoridad?
8. ¿Los hechos del primer delta están respaldados por los dictámenes y el glosario efectivamente vigentes?
9. ¿Las pruebas automatizadas cubren fallos relevantes y no solo el camino feliz?

## Entrega
Dejar un informe independiente en:
`Katarina/shared/2026-11-17-auditoria-demonio-sintesis-0.1.0.md`

Clasificar cada hallazgo como bloqueo, corrección necesaria o mejora posterior. Si detectas errores corregibles, proponer o realizar un parche acotado en una rama/commit separado, sin tocar la casa canónica ni ampliar alcance. No reabrir D01–D12 ni redefinir el Demonio. Si falta evidencia para ejecutar una prueba, declararlo explícitamente.

## Criterio de cierre
La auditoría debe confirmar si el prototipo es seguro para una prueba de laboratorio aislada. No certificar reducción del CHECKPOINT histórico ni operación concurrente: eso aún no se ha probado.
