# Integración de datos con AST

## Estado y límites

Espacio documental para la futura integración con el Supabase/PostgreSQL existente. El esquema no ha sido suministrado ni inspeccionado. No se definen tablas, columnas físicas, claves, relaciones, vistas, consultas SQL o migraciones.

`rating_out` es el nombre suministrado para los valores estadísticos; su ubicación, tipo, nulabilidad y asociación con participantes deben confirmarse con el esquema real. Su mención no presupone una tabla.

**Evento, Edición y Torneo competitivo no se consideran equivalentes.** Sus identidades, relaciones y cardinalidades se documentarán exclusivamente a partir del esquema y la semántica proporcionados por AST.

## Información funcional requerida, sin mapeo físico

| Información | Necesidad | Pendiente de validar |
| --- | --- | --- |
| Circuito y configuración | Contextualizar ATT/APT y filtros del motor común | Identidad, ámbito y reglas de configuración |
| Jugador | Seleccionar el sujeto de evaluación | Identificadores y correspondencia entre circuitos |
| Modalidad | Aislar evaluaciones | Catálogo y relación real con jugador y partidos |
| Historial de partidos | Seleccionar ventanas y ordenar observaciones | Fecha efectiva, estados computables, participantes y calidad |
| Valores `rating_out` | Cuartiles y tendencia | Fuente, granularidad y semántica del valor |
| Divisiones competitivas | Representar límites | Fuente, orden, límites, contexto y vigencia temporal |
| Clasificaciones | Separar vigente, calculada y aplicada | Procedencia y registro de cada concepto, si existe |
| Identidad y permisos | Reutilizar acceso de AST | Autenticación, sesiones, autorización y ámbitos |
| Evento, Edición y Torneo competitivo | Entender el contexto de competición | Definiciones diferenciadas y relaciones reales |

La tabla identifica necesidades del producto, no entidades de base de datos propuestas.

## Material requerido para la integración

Solicitar esquema o documentación autorizada con definiciones, relaciones, tipos y restricciones; diccionario de negocio; mecanismo vigente de autenticación y permisos; acceso previsto para esta aplicación; ejemplos anonimizados o ficticios; y fuentes de divisiones y clasificación vigente. No incluir credenciales ni datos personales reales en el repositorio.

Para cada mapeo confirmado registrar: necesidad funcional, fuente física exacta, significado, transformación, reglas de calidad, permisos, referencia documental y estado de validación. Conservar como pendientes los campos no acreditados.

## Trabajo paralelo al prototipo

La validación de datos podrá avanzar mientras se construye el prototipo visual. Sus fixtures serán contratos internos ficticios, claramente identificados, sin pretender reproducir PostgreSQL. Al disponer del esquema se revisarán los contratos y se diseñarán adaptadores, evitando forzar la base existente a ajustarse a los fixtures.

## Condiciones previas a conectar

Se requiere autorización explícita para la integración, un entorno definido, revisión del esquema real y del acceso existente. La autorización para documentar o validar material suministrado no autoriza conectarse a Supabase, consultar producción ni modificar datos o estructuras. Cualquier cambio de persistencia necesitará su propio alcance autorizado.

Los futuros expedientes, deliberaciones y resoluciones se documentarán cuando se definan sus necesidades y fuentes. No se presume que ya existan ni se anticipa su esquema.
