# Instrucciones permanentes para desarrollo asistido

## Alcance y fase actual

Estas instrucciones se aplican a todo el repositorio. Leer README.md, ARCHITECTURE.md, BUSINESS_RULES.md y DATA_MODEL.md antes de intervenir y mantenerlos coherentes con las decisiones autorizadas.

La fase actual es exclusivamente documental: no implementar la aplicación, instalar dependencias ni desarrollar algoritmos. La aprobación provisional de React + TypeScript + Vite y del prototipo ficticio no autoriza por sí sola iniciar esa fase. Avanzar cuando el responsable solicite el trabajo correspondiente.

## Restricciones obligatorias

- No conectarse a Supabase ni consultar o modificar datos o estructuras de producción sin autorización posterior explícita y con alcance definido.
- No inventar esquemas PostgreSQL, tablas, campos, claves, relaciones o equivalencias entre Evento, Edición y Torneo competitivo.
- No desarrollar autenticación nueva sin revisar previamente la existente en AST.
- No implementar reglas de clasificación no suministradas ni inferirlas a partir de gráficos, ratings o resultados narrativos.
- No introducir dependencias sin una necesidad concreta; mantener pendiente la librería de gráficos hasta su selección aprobada.
- Usar inicialmente solo datos ficticios, identificados tanto en el origen como en las vistas y salidas. No presentar resultados precalculados del prototipo como resultados de un motor validado.
- No guardar secretos, tokens, credenciales ni datos personales reales en el repositorio.

## Dominio y reglas

Las reglas MET-01 a MET-08 de BUSINESS_RULES.md son decisiones metodológicas suministradas, pendientes de contraste documental y con casos de prueba. No marcarlas como enteramente desconocidas ni como reglamentariamente verificadas.

Mantener la evaluación independiente por modalidad, la secuencia seis meses → 52 semanas → últimos 12 disponibles, y el carácter exclusivamente diagnóstico con menos de 12 partidos totales. Calcular los futuros cuartiles y tendencia sobre los mismos `rating_out` seleccionados; la tendencia se expresará en puntos por partido con orden cronológico. Consultar los detalles pendientes antes de implementar comportamientos no definidos.

El motor estadístico y de clasificación será independiente del circuito y compartido entre ATT y APT, usando filtros y configuraciones. Separar estrictamente dominio, visualización, acceso a datos e interpretación mediante IA. La selección automática de muestra pertenece al dominio.

Gráfico, boxplot, indicadores y narrativa consumirán un resultado común de evaluación, con trazabilidad de muestra y suficiencia. No recalcular ni seleccionar muestras diferentes en los componentes o en la IA. Mantener separados rating, clasificación vigente, clasificación calculada y reclasificación aplicada. Una evaluación no autoriza aplicar cambios.

## Secuencia de desarrollo

Respetar la hoja de ruta: documentación → prototipo visual ficticio y validación funcional → motor estadístico y pruebas → integración autorizada con Supabase → narrativa mediante IA → expedientes y flujos del Comité. La validación documental del modelo de datos puede avanzar en paralelo con el prototipo sin bloquearlo.

No crear módulos vacíos o código especulativo para fases posteriores. Al iniciar una fase, resolver únicamente las decisiones necesarias para su alcance. Registrar supuestos y preguntas abiertas en el documento correspondiente; no convertirlos silenciosamente en reglas.

## Calidad y entrega

En cambios documentales, revisar enlaces locales, coherencia entre archivos y diferencias de Git. No instalar herramientas para validar solo documentación. En fases de implementación autorizadas, ejecutar verificaciones proporcionales; las pruebas del motor deberán cubrir los límites y casos de referencia acordados, además del aislamiento por modalidad y configuración.

Informar qué cambió, cómo se verificó y qué sigue pendiente. No afirmar ejecución de pruebas, validación reglamentaria, acceso al backend o funcionamiento de una aplicación sin evidencia. Mantener los cambios locales salvo instrucción de publicar o enviar a GitHub.
