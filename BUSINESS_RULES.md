# Reglas de negocio y metodología

## Fuentes y estado

Fuente inicial: instrucciones del responsable del proyecto del 20 de octubre de 2026. AST dispone de reglamento y decisiones metodológicas posteriores, aún no aportados al repositorio.

Las reglas siguientes tienen estado **decisión metodológica suministrada; pendiente de contraste documental y con casos de prueba**. No se consideran reglas desconocidas ni se afirma que su validación reglamentaria esté terminada. Al recibir las fuentes, registrar referencia, versión, fecha, discrepancias y resolución autorizada, sin sustituir silenciosamente estas decisiones.

## Registro inicial

| ID | Decisión suministrada |
| --- | --- |
| MET-01 | Evaluación independiente por modalidad. No mezclar sus historiales en una evaluación. |
| MET-02 | Usar los partidos de los últimos seis meses si existen al menos 12 en esa ventana. |
| MET-03 | Si no se cumple MET-02, usar los partidos de las últimas 52 semanas si existen al menos 12 en esa ventana. |
| MET-04 | Si tampoco se cumple MET-03, usar los últimos 12 partidos disponibles. |
| MET-05 | Si existen menos de 12 partidos totales, el resultado estadístico será exclusivamente diagnóstico. |
| MET-06 | Calcular Q1, mediana y Q3 sobre `rating_out` de la muestra seleccionada. |
| MET-07 | Calcular la tendencia mediante regresión lineal sobre esos mismos valores, ordenados cronológicamente, expresándola en puntos por partido. |
| MET-08 | Distinguir rating, clasificación vigente, clasificación calculada y reclasificación efectivamente aplicada. |

MET-02 y MET-03 seleccionan la muestra de la ventana correspondiente; no indican truncarla a 12. La elección entre estrategias es secuencial: primero seis meses, después 52 semanas y finalmente los últimos 12 disponibles. Si el total no llega a 12, se conservará el carácter diagnóstico, sin atribuirle suficiencia reglamentaria.

## Conceptos que deben mantenerse separados

| Concepto | Distinción de trabajo |
| --- | --- |
| Rating | Magnitud de rendimiento; los estadísticos aquí definidos utilizan `rating_out`. No es por sí mismo una división asignada. |
| Clasificación vigente | Clasificación reconocida actualmente por AST; su fuente y vigencia se confirmarán. |
| Clasificación calculada | Resultado de aplicar reglas de clasificación, todavía incompletas en esta documentación. No modifica la vigente. |
| Reclasificación aplicada | Cambio efectivamente realizado mediante el procedimiento autorizado. No se presume a partir de un cálculo o narrativa. |

## Decisiones arquitectónicas aprobadas relacionadas

- Selección automática de muestra en el dominio, independiente de la visualización.
- Motor común a ATT y APT con filtros y configuraciones respectivos.
- Un resultado de evaluación compartido por gráfico temporal, boxplot, indicadores y narrativa.
- La IA interpreta resultados; no sustituye reglas ni adopta decisiones del Comité.

## Detalles pendientes de suministro o confirmación

| Tema | Definición necesaria antes de implementar el comportamiento afectado |
| --- | --- |
| Ventanas | Fecha de referencia, zona horaria, extremos inclusivos/exclusivos y significado exacto de seis meses; no sustituirlo por 180 días. |
| Partidos computables | Estados válidos, abandonos, walkovers, anulaciones, duplicados y cualquier otra exclusión. |
| Orden | Fecha efectiva del partido y desempate de partidos con igual fecha/hora para últimas 12 observaciones y tendencia. |
| Calidad | Tratamiento de `rating_out` ausente o inválido; relación entre validez de observaciones y conteo de muestra. |
| Cuartiles | Convención de cálculo e interpolación, precisión y redondeo de presentación. |
| Tendencia | Detalles de ajuste y presentación; tratamiento de cero o una observación. No asumir puntos por día ni umbrales cualitativos. |
| Boxplot | Bigotes y tratamiento visual de valores atípicos; no excluirlos de la muestra por inferencia. |
| Clasificación | Límites, vigencia, reglas de asignación, excepciones, ascensos/descensos y alcance de resultados diagnósticos. |
| Aplicación | Autoridades, deliberación, resolución y proceso para aplicar una reclasificación. |

## Casos de contraste que se solicitarán

Sin resultados numéricos inventados: exactamente 12 en seis meses; menos de 12 en seis meses pero al menos 12 en 52 semanas; menos de 12 en ambas ventanas y al menos 12 en el historial; totales entre cero y 11; partidos en los límites temporales; fechas empatadas; datos inválidos; modalidades distintas; contextos ATT/APT con configuraciones diferentes.

Para cada caso se registrarán fuente, entrada, fecha de referencia, configuración, muestra esperada, estadísticos esperados y carácter diagnóstico o suficiente. Estos escenarios son un plan de validación, no pruebas ya implementadas o reglas adicionales.
