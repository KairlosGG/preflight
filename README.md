# Preflight · Agent Tower

> Ningún agente despega sin preflight. *Ask the Tower before you build.*

Preflight es un agente de admisión de agentes para Microsoft 365, de código abierto. Antes de que alguien construya un agente, **Agent Tower** entrevista a quien lo propone y devuelve una ficha con tres respuestas:

- **Valor de negocio**: horas ahorradas y valor mensual estimado.
- **Coste**: estimación mensual en Copilot Credits.
- **Riesgo regulatorio**: categoría del AI Act y controles del Anexo A de ISO/IEC 42001 (con resúmenes propios, sin texto de la norma).

Con esa ficha propone una zona de gobierno (Citizen, Partnered o Professional) y una decisión. Después lanza una aprobación en la que siempre decide una persona y guarda el registro.

Se construye con Copilot Studio y Power Automate. Se distribuye como una solución de Power Platform que se puede instalar en cualquier tenant.

## Estado

**v0.1 en construcción. No es apta para producción** hasta que supere los 24 casos de prueba de [`04_pruebas/casos_prueba.csv`](04_pruebas/casos_prueba.csv).

## Estructura

| Carpeta | Contenido |
|---|---|
| `00_brief` | Especificación del proyecto |
| `01_bitacora` | Decisiones, una línea por lección |
| `02_solucion` | Exportaciones de la solución de Power Platform (.zip), con versión, fecha y tipo |
| `03_docs` | Guía de instalación, guía del aprobador y aviso legal |
| `04_pruebas` | Los 24 casos de prueba y el resultado de cada versión |

## Aviso legal

Orientación preliminar generada con IA. No constituye asesoramiento jurídico ni evaluación de conformidad. La clasificación debe validarla una persona responsable.

## Licencia

[Apache License 2.0](LICENSE). El software se ofrece "tal cual", sin garantías de ningún tipo.
