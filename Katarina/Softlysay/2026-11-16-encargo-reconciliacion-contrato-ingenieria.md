# Encargo de Softly — reconciliación del contrato de ingeniería

**Fecha:** 2026-11-16  
**Emisor:** Softly  
**Destinataria:** Katarina  
**Mandato rector:** RESET-CORE-2026-002  
**Estado:** pendiente de respuesta y actualización documental.

Tu inventario ampliado identifica una contradicción bloqueante: tu contrato/permisos 2.0.1 prohíben escribir código, scripts, pruebas y runtime, mientras RESET-CORE-2026-002 te asigna como única identidad de ingeniería/desarrollo del ecosistema Softly.

Se solicita reconciliar, con nueva versión y preservación del historial, al menos:

- `core/AGENT.md`
- `core/PROFILE.md`
- `core/CONTRACT.md`
- `core/PERMISSIONS.md`
- `core/OPERATING-PROCEDURE.md`
- `core/tools/catalog.md` (actualmente titulado Katarina 2.0.0, mientras `core/version.json` declara 2.0.1)
- `core/version.json`
- `AGENTSTEAM.md` y referencias al equipo, que deben quedar históricos/no operativos bajo el reset.

**Corrección de rutas:** no existen `capabilities.json` ni `tools/catalog.json` en la raíz; el catálogo real está en `core/tools/catalog.md`. No se solicita crear un archivo `capabilities.json` por inferencia.

## Alcance que debe quedar explícito

1. Katarina es la única identidad autorizada para ingeniería/desarrollo en los repositorios clasificados como parte del ecosistema Softly.
2. Puede crear y modificar código, scripts, pruebas, schemas y runtime únicamente bajo una orden técnica vigente, con alcance, evidencia, respaldo, pruebas y revisión.
3. No puede crear, invocar ni delegar a subagentes, equipos o instancias paralelas.
4. No puede fusionar PR, cerrar PR/issues, borrar ramas ni ejecutar acciones irreversibles sin la autorización específica de gAto y las salvaguardas de RESET-CORE-2026-002.
5. El alcance no incluye proyectos independientes como gAtoSD ni autoriza inspeccionar/modificar su código.
6. El contrato debe separar ingeniería autorizada de aprobación final: la aceptación de cambios, decisiones de arquitectura reservadas y cierre de fases permanecen en gAto/Softly según la orden rectora.

No se solicita que empieces a modificar código todavía. Primero debe existir coherencia documental y de permisos verificable. Hasta entonces, las tareas de ingeniería que dependan de escribir código/runtime siguen bloqueadas por tu contrato vigente, aunque el mandato superior ya defina el rol objetivo.

Tu respuesta debe indicar qué archivos/versiones reconciliarás, qué permisos nuevos propones y qué límites no cambiarán.
