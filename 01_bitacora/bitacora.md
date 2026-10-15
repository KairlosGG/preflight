# Bitácora de Preflight

Una línea por lección o decisión: fecha · lección · qué decidí y por qué.

| Fecha | Lección | Decisión y motivo |
|---|---|---|
| 2026-10-14 | — | Proyecto Preflight (repositorio) y Agent Tower (agente en Teams). Código abierto. Se construye siguiendo CS, PA y LLM del máster; v1.0 con la AB-620. |
| 2026-10-15 | Auditoría | Curso filtrado: CS y PA según la auditoría (a fondo, en diagonal o fuera). Bloque LLM omitido: es optativo y el máster ya está certificado. Motivo: los conceptos valen y son el requisito previo de la AB-620; interfaz, precios y bloque LLM están caducados. |
| 2026-10-15 | Auditoría | Agent Tower en la experiencia clásica de Copilot Studio durante la v0.x. Motivo: la nueva es preliminar, no se puede convertir y el examen pregunta sobre todo funciones GA. Revisar en la v1.0. |
| 2026-10-15 | Auditoría | Flujos de Preflight como agent flows dentro de la solución, no flujos de nube sueltos. Motivo: los pide el brief, los mide la AB-620 y se cobran por acción en Copilot Credits. |
| 2026-10-15 | Auditoría | El agente de CS-C16 entra como caso de prueba de alto riesgo, no como plantilla. |
| 2026-10-15 | Auditoría | Nada sale del tenant: sin Make ni IA externa por HTTP. La fuente de conocimiento del AI Act se monta en Copilot Studio. |
| 2026-10-15 | Auditoría | Propietario de los agent flows en producción: cuenta de servicio dedicada con licencia, y conexiones mediante referencias de conexión de la solución. Motivo: es lo más barato que no depende de una persona concreta. A confirmar en la fase 3. |
| 2026-10-15 | Método | Sin vídeos del curso: Preflight se construye guiado paso a paso con la auditoría y Microsoft Learn. |
| 2026-10-15 | Entorno | Tenant de laboratorio a coste 0: Entra ID mediante cuenta gratuita de Azure, más Power Apps Developer Plan y prueba de Copilot Studio, en lugar de la prueba de Microsoft 365. Motivo: sin dinero para licencias, y la prueba de M365 borra los datos al terminar y acabaría durante el viaje a México (28/10–17/11). Teams se añade en la fase 4 con la prueba de Empresa Básico. |
| 2026-10-15 | CS-C01 | Base montada: tenant preflightlaboutlook.onmicrosoft.com (Preflight Lab), cuenta carlos@ con rol de administrador global (laboratorio), entorno de desarrollo Preflight-DEV (Dataverse, región Europa), editor Preflight con prefijo pft, solución Preflight 0.1.0.0 como solución preferida, variables pft_VersionPreflight = 0.1.0 y pft_VersionReglas = 0.0.0 (solo valor predeterminado). Motivo: todo nace dentro de la solución y con trazabilidad de versión desde el primer día. |
| 2026-10-15 | CS-C01 | Repositorio público KairlosGG/preflight en GitHub (licencia Apache 2.0) con la estructura del brief y la primera exportación no administrada (Preflight_0.1.0.1_2026-10-15_unmanaged.zip). Convención de nombre: Preflight_<versión>_<fecha>_<managed|unmanaged>.zip. Motivo: copia de seguridad fuera del tenant e historial de versiones desde el primer día. |
