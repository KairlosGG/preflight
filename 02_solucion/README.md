# Exportaciones de la solución

Aquí van las exportaciones de la solución de Power Platform (.zip).

Nombre: `Preflight_<versión>_<AAAA-MM-DD>_<managed|unmanaged>.zip`. Al exportar, Power Platform lo llama `Preflight_0_1_0_1.zip`; se renombra antes de guardarlo aquí.

Guarda siempre las dos versiones:

- **No administrada** (`unmanaged`): para seguir desarrollando.
- **Administrada** (`managed`): para instalar en pruebas y producción. La primera llegará con la v1.0.

| Archivo | Versión | Tipo | Fecha | Contenido |
|---|---|---|---|---|
| Preflight_0.1.0.1_2026-10-15_unmanaged.zip | 0.1.0.1 | No administrada | 2026-10-15 | Solución con las variables de entorno pft_VersionPreflight (0.1.0) y pft_VersionReglas (0.0.0), solo valor predeterminado |
| Preflight_0.1.0.2_2026-10-19_unmanaged.zip | 0.1.0.2 | No administrada | 2026-10-19 | Añade el agente Agent Tower vacío (pft_AgentTower, arnés estándar, español) con sus 13 temas del sistema |
| Preflight_0.1.0.3_2026-10-20_unmanaged.zip | 0.1.0.3 | No administrada | 2026-10-20 | Bienvenida con aviso legal, tema Evaluar un agente, bloque A de la entrevista con tarjeta de revisión y variables globales P00-P03 |
| Preflight_0.1.0.4_2026-10-20_unmanaged.zip | 0.1.0.4 | No administrada | 2026-10-20 | Bloque B (Valor) con tarjeta validada, regla de coherencia de usuarios con tarjeta de corrección y variables globales P04-P09 |
| Preflight_0.1.0.5_2026-10-21_unmanaged.zip | 0.1.0.5 | No administrada | 2026-10-21 | Bloques C (Funcionamiento) y D (Riesgo) con una tarjeta cada uno, reglas de coherencia de P15 y P19, tarjeta de la excepción del art. 6.3 y variables globales P10-P19 y P15b |
| Preflight_0.1.0.6_2026-10-21_unmanaged.zip | 0.1.0.6 | No administrada | 2026-10-21 | Motor de reglas deterministas (tema Clasificar riesgo, reglas 0.1.0) con variables R_*, pregunta de alcance P04b, observaciones P19b e interrupciones desactivadas en el bloque A |

## Fuente descomprimida

La carpeta `src` contiene la última exportación descomprimida (YAML de temas y componentes). Se sustituye en cada versión para que GitHub muestre los cambios línea a línea. El zip sigue siendo lo que se importa.
