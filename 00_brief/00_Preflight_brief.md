# Preflight · Brief del proyecto

Versión del brief: 14/10/2026.

## Nombres

- **Preflight**: el proyecto, el repositorio de GitHub y el concepto (la comprobación antes de construir). Comprobar en GitHub que no choca con otro repositorio conocido antes de publicar.
- **Agent Tower**: el agente que el empleado ve en Teams y al que le habla (quien da la autorización para despegar).
- Frase: "Ningún agente despega sin preflight. Ask the Tower before you build."
- Ojo: ServiceNow vende "AI Control Tower" en gobierno de IA. No es el mismo nombre, pero alguien del sector lo asociará.

## Qué es

Agente de admisión de agentes para Microsoft 365. Antes de que alguien construya un agente, Agent Tower le entrevista y devuelve una ficha con tres respuestas: valor de negocio, coste mensual estimado en Copilot Credits y riesgo regulatorio (AI Act y controles del Anexo A de ISO/IEC 42001). Propone una zona de gobierno de Microsoft y una decisión, lanza una aprobación con una persona en el circuito y deja el registro.

Construido con Copilot Studio y Power Automate. Distribución en código abierto: solución de Power Platform instalable en el tenant de cualquier organización, publicada en GitHub.

## Hueco que cubre

Las herramientas existentes actúan después de construir (Microsoft Agent 365, Copilot Agent Kit con Compliance Hub y Agent Review Tool, Modulos) o son plataformas GRC enterprise de pago (OneTrust, ServiceNow AI Control Tower, Credo AI). Ninguna junta coste en créditos, valor y riesgo antes de construir, dentro de Teams, en castellano y sin licencias E5/E7. Preflight debe complementar a Agent 365, no competir con él.

## Versiones

- v0.x: se construye siguiendo los tres módulos del máster de BIG School (Copilot Studio, Power Automate, LLMs local y nube).
- v1.0: se completa con lo que pide la AB-620 (evaluación con test sets, ALM con soluciones, variables de entorno y pipelines, MCP, multiagente).
- Producción = solución gestionada publicada, instalable con guía, con reglas versionadas y pruebas de regresión superadas.

## Requisitos de producción (desde la v0.1)

- Todo dentro de una solución de Power Platform y con variables de entorno desde el primer día.
- Tres entornos: desarrollo, pruebas, producción.
- Registro en Dataverse (permisos y auditoría). Si un instalador no tiene licencias premium, alternativa documentada con lista de SharePoint.
- Tarifas de créditos y reglas de clasificación en tablas con fecha de vigencia, no escritas dentro del prompt.
- Autenticación con Entra; registro de quién propuso, quién aprobó y con qué versión de reglas.
- Los 24 casos de prueba son regresión obligatoria antes de cada versión.
- Aviso legal en la bienvenida y en cada ficha: "Orientación preliminar generada con IA. No constituye asesoramiento jurídico ni evaluación de conformidad. La clasificación debe validarla una persona responsable."
- No incluir texto de la norma ISO/IEC 42001 (derechos de autor): solo resúmenes propios por control con su referencia. El AI Act sí puede usarse como fuente (EUR-Lex).
- Licencia de código abierto con exención de responsabilidad (Apache 2.0 o MIT).

## Entrevista (19 preguntas)

A. Identificación
1. Nombre provisional del agente y área.
2. Problema que resuelve, en una frase.
3. Propietario de negocio.

B. Valor
4. Personas que lo usarán al mes.
5. Cuántas tienen licencia de Microsoft 365 Copilot.
6. Minutos que ahorra por uso.
7. Usos por persona al mes.
8. Coste por hora cargado del perfil (€).
9. Métrica y umbral para retirarlo a los 90 días.

C. Funcionamiento
10. ¿Solo responde o también ejecuta acciones (crear o modificar registros, enviar correos)?
11. Fuentes: SharePoint o archivos concretos, todo Microsoft 365 (Graph), web o sistemas externos.
12. ¿Procesa documentos o imágenes? ¿Cuántas páginas al mes?
13. ¿Lo usarán personas externas?

D. Riesgo
14. ¿Trata datos personales? ¿De categorías especiales?
15. ¿Influye en decisiones sobre personas: selección, evaluación o promoción de empleados, formación, crédito, seguros o prestaciones?
16. ¿Una persona revisa cada resultado antes de que tenga efecto?
17. ¿Elabora perfiles o puntuaciones de personas?
18. ¿Genera contenido que se publicará fuera?
19. ¿Infiere emociones, usa biometría o manipula decisiones?

## Ficha

| Bloque | Campos |
|---|---|
| Identificación | ID, nombre, propietario, área, fecha |
| Valor | Usuarios, horas/mes, €/hora, valor bruto/mes, criterio de retirada |
| Coste | Créditos/mes bajo y alto, $/mes en pago por uso, % de usuarios con licencia, fecha de la tabla de tarifas, aviso de AI Builder |
| Riesgo | Categoría AI Act, artículo o punto del Anexo, hechos usados, rol (responsable del despliegue o proveedor), RGPD (EIPD sí/no, art. 22 sí/no), controles A.5–A.10 |
| Gobierno | Zona (Citizen, Partnered, Professional), decisión propuesta, aprobador, decisión final, comentario |
| Trazabilidad | Versión de Preflight, versión de reglas, aviso legal |

## Reglas de clasificación (deterministas; el modelo solo extrae hechos y redacta)

1. Prohibido (art. 5) si P19 indica manipulación, puntuación social, reconocimiento de emociones en trabajo o educación o categorización biométrica sensible → no construir.
2. Anexo III si P15 marca un ámbito de los puntos 3, 4 o 5.
   - Excepción art. 6(3) a confirmar si P17 = no y P16 = sí y la tarea es preparatoria o procedimental → construir con aprobación humana, documentar la excepción, revisar registro (art. 49(2)).
   - Sin excepción → alto riesgo: no construir en Copilot Studio sin asesoría jurídica; obligaciones aplicables desde el 2/12/2027.
3. Transparencia (art. 50, aplicable desde el 2/8/2026) si interactúa con personas externas (P13) o publica contenido generado (P18) → construir con aviso de IA.
4. Mínimo en el resto.

RGPD: P14 = sí → A.7 y pregunta de EIPD. P15 = sí y P16 = no → marcar art. 22 RGPD.

Zona: Citizen = personal o de equipo, solo lectura, sin acciones, riesgo mínimo. Partnered = varios equipos, acciones, datos personales o transparencia. Professional = externos a escala, alto riesgo, sistemas críticos o acción autónoma sobre datos de terceros.

## Coste

Tabla oficial: Microsoft Learn, "Billing rates and management" (última actualización consultada 1/10/2026). Respuesta clásica 1 crédito; generativa 2; acción de agente 5; grounding en Graph 10 por mensaje; agent flow 13 por cada 100 acciones; prompts básico 0,1, estándar 1,5 y premium 10 créditos por 1.000 tokens; procesamiento de contenido 8 por página. Uso interno de usuarios con licencia de M365 Copilot: sin cargo en esas filas (con límites de uso razonable).

Créditos por sesión = clásicas × 1 + generativas × 2 + acciones × 5 + mensajes con Graph × 10 + tokens/1.000 × (0,1 | 1,5 | 10) + acciones de flujo/100 × 13 + páginas × 8.

Créditos/mes = créditos por sesión × sesiones/mes × (1 − % usuarios con licencia de M365 Copilot, si es interno).

Rango alto = perfil máximo × 1,2. Precio: 0,01 $ por crédito en pago por uso; pack de 25.000 créditos por 200 $/mes.

AI Builder: el 1/11/2026 desaparecen los créditos incluidos en licencias premium de Power Apps y Power Automate; no se convierten en Copilot Credits.

## Valor

Valor mensual = usuarios × usos/mes × (minutos ahorrados/60) × €/hora × 0,5 (factor prudente, editable).
Ratio = valor mensual / (coste mensual + horas de mantenimiento × €/hora).
Ratio < 1 → no construir; 1–3 → piloto; > 3 → construir. El riesgo siempre prevalece sobre el valor.

## Flujo de aprobación

Ficha en tarjeta adaptable → el proponente confirma los hechos → agent flow: registro "Pendiente" → Approvals al responsable de IA (y a DPO o legal si alto riesgo, excepción 6(3) o art. 22) → actualizar estado y comentario → aviso por Teams → si falla, registrar error y avisar al administrador.

## Juego de 24 casos de prueba

Ver `04_pruebas/casos_prueba.csv`.

## Fechas normativas verificadas

AI Act modificado por el Reglamento (UE) 2026/1744 (DOUE 24/7/2026, en vigor 27/7/2026): art. 5 desde 2/2/2025; art. 50 desde 2/8/2026; Anexo III desde 2/12/2027; Anexo I desde 2/8/2028. Ley española de IA: proyecto en tramitación, no vigente.

## Estructura de la carpeta Preflight

- 00_brief: este brief e instrucciones del proyecto de Claude.
- 01_bitacora: bitacora.md, una línea por lección (qué decidí y por qué).
- 02_solucion: exportaciones de la solución de Power Platform (.zip), con fecha y versión.
- 03_docs: README, guía de instalación, guía del aprobador, aviso legal.
- 04_pruebas: casos_prueba.csv con los 24 casos y resultados de cada versión.
