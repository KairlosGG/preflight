# Preflight · Registro de pruebas

Todas las evaluaciones hechas en el chat de prueba de Copilot Studio (Preflight-DEV), por lección y versión. Fuente: las conversaciones del proyecto (CS-C07, CS-C08, CS-C09 y CS-C10). Los valores de las tarjetas van en el orden en que salen en pantalla.

Leyenda: **OK** = resultado igual al esperado · **Fallo** = distinto, con su corrección · **Parcial** = lo principal correcto y un fallo secundario.

---

## Resumen por caso del brief

| # | Caso | Esperado (brief) | Probado | Último resultado |
|---|---|---|---|---|
| 3 | Redacción de ofertas con revisión humana | Anexo III, excepción 6(3)(d) a confirmar | CS-C07, CS-C08, CS-C10 | OK (0.1.0.8: reglas 0.2.0, prompts 0.1.1, ficha) |
| 7 | Emociones en videollamadas internas | Prohibido, art. 5(1)(f) | CS-C08 | OK (reglas 0.1.0) |
| 12 | Chatbot de clientes en la web | Transparencia, Professional | CS-C08 | OK (reglas 0.1.0) |
| 14 | Resumen de actas internas | Mínimo, Citizen | CS-C07, CS-C08, CS-C09, CS-C10 | OK (0.1.0.8) |
| 22 | Decide bajas sin revisión humana | Alto riesgo + art. 22 RGPD | CS-C08, CS-C10 | OK (0.1.0.8) |
| 23 | 5 usuarios, 2 minutos al mes | No construir por valor | CS-C10 | OK (0.1.0.8), también el camino de corrección |
| 24 | "Un agente para RR. HH." | Pedir más información | CS-C09, CS-C10 | OK (0.1.0.8): "Falta información" se impone al valor |
| Extra | Filtro de CV con contradicciones a propósito | Coherencia a_revisar | CS-C09, CS-C10 | OK la decisión (0.1.0.8: "Revisa tus respuestas"); limitación conocida: señala de más "Qué hará el agente" |

Casos sin probar todavía: 1, 2, 4, 5, 6, 8, 9, 10, 11, 13, 15, 16, 17, 18, 19, 20, 21. Los 24 son regresión obligatoria antes de la v1.0.

---

## CS-C07 · 21/10/2026 · solución 0.1.0.5 (entrevista A-D, sin reglas)

Dos evaluaciones seguidas en la misma conversación, para comprobar las correcciones de multiselección, la tarjeta 6.3 y el vaciado.

### Evaluación 1: caso 3
| Dónde | Valores |
|---|---|
| Chat | `Quiero un agente que redacte borradores de ofertas de empleo para que los revise el equipo de selección.` |
| A | `Redactor de ofertas de empleo` · `Recursos Humanos` · `Redactar cada oferta de empleo le lleva demasiado tiempo al equipo de selección.` · `Marta Gil, responsable de selección` |
| B | 5 · 0 · 30 · 6 · 35 €/h · `Menos de 10 ofertas redactadas al mes` |
| C | Solo responde · SharePoint · 0 · No |
| D | Sí, datos personales · Ninguno + Empleo: selección de personal · Sí · No · Sí, con revisión · Ninguna + Inferir emociones en el trabajo |
| Corrección | Ámbitos: solo selección de personal · Prácticas: solo Ninguna |
| 6.3 | Tarea preparatoria |
| **Resultado** | **OK**: tarjetas de corrección y tarjeta 6.3 aparecen; cierre provisional correcto |

### Evaluación 2: caso 14 (sin reiniciar)
| Dónde | Valores |
|---|---|
| Chat | `Quiero evaluar otro agente que resuma las actas de las reuniones internas.` |
| A | `Resumidor de actas` · `Dirección` · `Resumir las actas de las reuniones internas lleva mucho tiempo.` · `Pablo Ruiz, director de operaciones` |
| B / C / D | 20 · 5 · 15 · 4 · 40 · `Menos de 30 resúmenes al mes` / Solo responde · Conversación · 0 · No / No · Ninguno · Sí · No · No · Ninguna |
| **Resultado** | **OK**: tarjetas vacías al empezar (el vaciado funciona); sin ámbito no aparece la tarjeta 6.3 |

Incidencia: un tema duplicado "Entrevista D Riesgo" (EntrevistaDRiesgo_mOu) hacía que se editara la copia; se detectó en el zip y se eliminó.

---

## CS-C08 · 21/10/2026 · solución 0.1.0.6 · reglas 0.1.0

Cinco casos seguidos en la misma conversación. Revisión A siempre sin cambios.

| Caso | Chat y bloque A | B | C | D (+ 6.3) | Esperado | Resultado |
|---|---|---|---|---|---|---|
| 3 | `Quiero un agente que redacte borradores de ofertas de empleo para que los revise el equipo de selección.` · Redactor de ofertas de empleo · Recursos Humanos · Marta Gil | Mi equipo · 5 · 0 · 30 · 6 · 35 | Solo responde · SharePoint · 0 · No | Personales · Selección de personal · Sí · No · Con revisión · Ninguna · 6.3: preparatoria | excepcion_6_3 · Partnered · construir_con_aprobacion | **OK**. Referencias: Anexo III 4.a, art. 6.3 (art6_3d), RGPD/EIPD. Confirma que la multiselección separa con comas |
| 7 | `Quiero evaluar un agente que detecte las emociones de los empleados en las videollamadas internas.` · Detector de emociones · Recursos Humanos · Luis Pardo | Toda la organización · 300 · 0 · 5 · 8 · 30 | Solo responde · Graph · 0 · No | Especiales · Ninguno · No · Sí · No · Inferir emociones en el trabajo | prohibido · No aplica · no_construir | **OK**. Referencias: art. 5.1.f, RGPD/EIPD |
| 12 | `Quiero evaluar un chatbot en la web que responda a las preguntas de los clientes.` · Asistente web de clientes · Atención al cliente · Ana Torres | Otros equipos · 2000 · 0 · 3 · 2 · 25 | Solo responde · SharePoint + Web · 0 · Sí | No · Ninguno · No · No · No · Ninguna | minimo · Professional · construir_con_aviso_ia | **OK**. Referencias: art. 50 |
| 14 | `Quiero evaluar un agente que resuma las actas de las reuniones internas.` · Resumidor de actas · **Dirección** · Pablo Ruiz | Mi equipo · 20 · 5 · 15 · 4 · 40 | Solo responde · Conversación · 0 · No | No · Ninguno · Sí · No · No · Ninguna | minimo · Citizen · construir | **Fallo y OK**. 1.ª vez: "Dirección" disparó el tema Escalate. Corrección: interrupciones desactivadas en las 4 preguntas del bloque A. 2.ª vez: OK |
| 22 | `Quiero evaluar un agente que decida las bajas de empleados sin revisión humana.` · Gestor de bajas · Recursos Humanos · Elena Ríos | Otros equipos · 10 · 2 · 60 · 3 · 45 | Acciones autónomas · Otros sistemas · 0 · No | Personales · Condiciones laborales (4b) · No · Sí · No · Ninguna · 6.3: ninguna | alto_riesgo · Professional · no_construir_sin_asesoria | **OK**. Referencias: Anexo III 4.b, art. 22 RGPD, RGPD/EIPD |

---

## CS-C09 · 21/10/2026 · solución 0.1.0.7 · reglas 0.1.0 · prompts 0.1.0

### Revisar coherencia
| Evaluación | Valores | Esperado | Resultado |
|---|---|---|---|
| Filtro de CV (contradicciones a propósito) | Problema: `Lee los CV en PDF de cada oferta y ordena a los candidatos de mejor a peor para la primera criba.` · marcado: Solo responde, SharePoint, 0 páginas, sin datos personales, ningún ámbito, sin perfilado | a_revisar en P12, P14, P15 y P17 | **OK**: las cuatro contradicciones con su frase |
| Actas (caso 14) | `Quiero un agente que resuma las actas de las reuniones internas de mi equipo.` · Resumen de actas · Dirección · `Resume en una página las actas de las reuniones semanales del equipo que guardamos en SharePoint.` · Dirección general · B: Equipo · 8 · 0 · 20 · 4 · 60 · C: Solo responde · SharePoint · 40 · No · D: No · Ninguno · Sí · No · No · Ninguna | coherente · minimo · Citizen · construir | **OK** |

### Comprobar suficiencia (caso 24)
| Evaluación | Valores | Esperado | Resultado |
|---|---|---|---|
| 1. Ampliada | `Un agente para RR. HH.` + respuesta a la pregunta de detalle sobre vacaciones y permisos; alcance organización | Pregunta una vez, luego suficiente | **Parcial**: suficiencia OK; coherencia con falso positivo en P16 ("debería existir revisión humana") |
| 2. Sin ampliar | `Un agente para RR. HH.` · Agente RR. HH. · Recursos Humanos · `Ayudar a RR. HH.` · `Responsable de RR. HH.` · detalle: `Algo útil para el equipo.` | Insuficiente, sin bucle | **Parcial**: sin bucle e insuficiente, OK; coherencia con falso positivo en P14 ("un agente de RR. HH. normalmente trata datos personales") |
| 3. Actas | Como la evaluación de actas anterior | Sin pregunta de detalle; suficiente | **OK** |

Corrección: ejemplos de lo que es y no es contradicción en las instrucciones del prompt de coherencia. Repetidas las evaluaciones 1 y 2: **OK** sin falsos positivos.

Pendientes abiertos: el camino no_evaluada (no se puede provocar desde el chat) y que la decisión final proponga "pedir más información" (resuelto en CS-C10, falta repetir el caso 24).

---

## CS-C10 · 21-22/10/2026 · solución 0.1.0.8 · reglas 0.2.0 · prompts 0.1.1 · ficha

Configuración: `pft_CosteHora` 26.18 · `pft_PrecioCredito` 0.006932 · `pft_Moneda` EUR.

### Caso 14 (cuatro ejecuciones)
| Dónde | Valores |
|---|---|
| Chat | `Quiero crear un agente que resuma las actas de las reuniones internas de mi equipo` |
| A | `Resumidor de actas` · `Operaciones` · `Resume las actas de las reuniones semanales del equipo, guardadas en un sitio de SharePoint, y extrae los acuerdos y las tareas pendientes.` · `Lucía Martín, jefa de Operaciones` |
| B | Mi equipo · 10 · 0 · 15 · 4 · mantenimiento 1 · `menos de 20 resúmenes al mes` |
| C | Solo responde · SharePoint · 0 · No |
| D | No · Ninguno · Sí · No · No · Ninguna · vacío |
| Esperado | Construir (verde) · valor 130,90 EUR · 80 a 576 créditos · 0,55 a 3,99 EUR · 0,80 a 5,76 USD · ratio 4,34 · minimo · Citizen · coherente |

| Ejecución | Resultado |
|---|---|
| 1 (21/10, prompts 0.1.0) | **Parcial**: todas las cifras OK; coherencia a_revisar por P12 ("procesa actas") y el detalle mostraba el código `P12_PaginasMes (marcado: 0)` |
| 2 (22/10, pregunta P12 aclarada + nombres legibles) | **Parcial**: el detalle ya sale legible; sigue el falso positivo de P12 |
| 3 (22/10, prompts 0.1.1 con P12 redefinida) | **Parcial**: falso positivo de P12 por "extrae los acuerdos" |
| 4 (22/10, P12 fuera de la revisión de coherencia) | **OK**: coherente, prompts 0.1.1 |

Corrección de diseño: P12 solo alimenta la estimación de coste y depende de cómo se construya el agente, así que no la revisa el prompt de coherencia.

### Caso 23 y camino de corrección
| Dónde | Valores |
|---|---|
| Chat | `Quiero un agente que diga qué días son festivos en la oficina` |
| A | `Consulta de festivos` · `Administración` · `Consulta el calendario de festivos de la oficina, guardado en un sitio de SharePoint, y responde qué días son festivos.` · `Pablo Ruiz, responsable de Administración` |
| B | Mi equipo · 5 · 0 · 2 · 1 · 1 · `menos de 5 consultas al mes` |
| C | Solo responde · SharePoint · 0 · No |
| D | No · Ninguno · Sí · No · No · Ninguna · vacío |
| Corrección | Quiero corregir algo → Valor → minutos 30 · usos 20 |

| Ficha | Esperado | Resultado |
|---|---|---|
| 1.ª | No construir por valor (rojo) · 2,18 EUR · 10 a 72 créditos · 0,07 a 0,50 EUR · ratio 0,08 | **Parcial**: todas las cifras y la decisión OK; falso positivo de coherencia en P16 (`responde qué días son festivos` frente a revisión humana "Sí") |
| 2.ª (tras corregir) | Construir (verde) · 5 × 20 usos · 654,50 EUR · 200 a 1.440 créditos · 1,39 a 9,98 EUR · ratio 18,10 | **Parcial**: el camino de corrección recalcula todo y vuelve a la ficha; mismo falso positivo de P16. Confirmación OK |

Causa: P16 (revisión humana) solo cuenta para las reglas cuando hay un ámbito del Anexo III, pero se preguntaba siempre. Corrección: P16 pasa a la tarjeta del Anexo III (solo con ámbito) y el revisor de coherencia solo la recibe si se preguntó.

| Ejecución tras la corrección (22/10) | Resultado |
|---|---|
| Caso 23, mismos valores; tarjeta D sin la pregunta de revisión humana | **OK**: no construir por valor, coherente, "Supervisión humana: Solo informa, no ejecuta acciones" |

### Caso 24 (22/10)
| Dónde | Valores |
|---|---|
| Chat y A | `Un agente para RR. HH.` · `Agente RR. HH.` · `Recursos Humanos` · `Ayudar a RR. HH.` · `Responsable de RR. HH.` · detalle: `Algo útil para el equipo.` |
| B / C / D | Mi equipo · 10 · 0 · 10 · 4 · 1 · `menos de 10 consultas al mes` / Solo responde · SharePoint · 0 · No / No · Ninguno · No · No · Ninguna |
| Esperado | Falta información (ámbar) · 87,27 EUR · 80 a 576 créditos · ratio 2,89 (piloto) · insuficiente con detalle |
| **Resultado** | **OK** |

### Casos 3 y 22, regresión del bloque D (22/10, misma sesión)
| Caso | Valores | Esperado | Resultado |
|---|---|---|---|
| 3 | `Quiero un agente que redacte borradores de ofertas de empleo para que los revise el equipo de selección.` · Redactor de ofertas de empleo · Recursos Humanos · `Redacta borradores de ofertas de empleo a partir de la descripción del puesto, para que los revise el equipo de selección antes de publicarlos.` · Marta Gil · B: Mi equipo · 5 · 0 · 30 · 6 · 2 · C: Solo responde · SharePoint · 0 · No · D: Personales · Selección de personal · No · Con revisión · Ninguna · Anexo III: Sí revisa · Preparatoria | Construir con condición · 196,35 EUR · 60 a 432 · ratio 3,55 · excepción 6.3 · Partnered | **OK** |
| 22 | `Quiero evaluar un agente que decida las bajas de empleados sin revisión humana.` · Gestor de bajas · Recursos Humanos · `Decide y tramita las bajas de los empleados en el sistema de RR. HH., sin revisión humana previa.` · Elena Ríos · B: Otros equipos · 10 · 2 · 60 · 3 · 4 · C: Acciones autónomas · Otros sistemas · 0 · No · D: Personales · 4b · Perfilado Sí · No · Ninguna · Anexo III: No revisa · Ninguna | No construir sin asesoría · 392,70 EUR · 264 a 893 · ratio 3,54 · alto riesgo · art. 22 · Professional | **Parcial y OK**: 1.ª, falso positivo de coherencia por perfilado declarado de más. Corrección: el revisor solo señala lo declarado por debajo. 2.ª: **OK**, coherente |

### Filtro de CV (22/10)
| Dónde | Valores |
|---|---|
| Chat y A | `Quiero un agente que filtre los CV que llegan a RR. HH.` · Filtro de CV · Recursos Humanos · `Lee los CV en PDF de cada oferta y ordena a los candidatos de mejor a peor para la primera criba.` · Marta Gil |
| B / C / D | Mi equipo · 3 · 0 · 20 · 10 · 1 · `menos de 20 cribas al mes` / Solo responde · SharePoint · 0 · No / No · Ninguno · No · No · Ninguna |
| Esperado | Revisa tus respuestas (ámbar) · 130,90 EUR · 60 a 432 · ratio 4,49 · contradicciones en datos personales, decisiones sobre personas y perfiles |
| **Resultado** | **OK la decisión** (antes de la corrección salía "Construir" en verde). Señala además "Qué hará el agente" incluso tras definir "acción" en el prompt: limitación conocida, a medir con el conjunto de pruebas |
