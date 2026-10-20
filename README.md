# AST Competitive Intelligence

Aplicación web del ecosistema AST, plataforma de gestión de circuitos deportivos. Su primer producto es un **Explorador de Perfiles Competitivos** de jugadores de tenis y pádel que proporciona información técnica para apoyar las evaluaciones del Comité de Clasificación.

## Estado y decisiones

Fase exclusivamente documental. No hay aplicación, dependencias instaladas, motor implementado ni conexión con Supabase. React + TypeScript + Vite y un prototipo con datos ficticios están aprobados provisionalmente. La librería de gráficos está pendiente.

Las decisiones metodológicas suministradas están registradas en [BUSINESS_RULES.md](BUSINESS_RULES.md): se deben contemplar, aunque su contraste con el reglamento y los casos de prueba sigue pendiente. Una evaluación calculada no equivale a una reclasificación aplicada.

## Alcance inicial

- Selección de circuito, jugador y modalidad; evaluación independiente por modalidad.
- Evolución temporal del rating y representación de los límites de divisiones competitivas.
- Selección automática de muestra como capacidad del dominio.
- Identificación de partidos incluidos y excluidos, con razones trazables.
- Boxplot sincronizado con el gráfico temporal a partir del mismo resultado de evaluación.
- Q1, mediana, Q3, tendencia en puntos por partido y suficiencia de muestra.
- Interpretación narrativa mediante OpenAI en una fase posterior.

El motor estadístico y de clasificación será común a ATT y APT, con filtros y configuraciones específicos. La futura gestión de expedientes, deliberaciones y resoluciones del Comité se incorporará de forma modular.

## Límites actuales

No implementar todavía la aplicación ni algoritmos de clasificación. No instalar dependencias, conectarse a Supabase, consultar o modificar producción, inventar esquemas o relaciones, ni crear autenticación sin revisar la existente. Todos los datos iniciales serán ficticios y estarán identificados en la interfaz y en su origen.

## Hoja de ruta aprobada

1. Documentación: visión, arquitectura, reglas, integración e instrucciones permanentes.
2. Prototipo visual con datos ficticios y validación funcional. Los resultados precalculados serán simulaciones explícitas, sin acreditar cumplimiento reglamentario.
3. Implementación y pruebas del motor estadístico, contrastando reglamento y casos aportados. Las reglas de clasificación aún no suministradas no se implementarán por inferencia.
4. Integración autorizada con Supabase y los mecanismos existentes de acceso e identidad.
5. Generación narrativa mediante IA sobre el resultado de evaluación.
6. Gestión de expedientes y flujos del Comité.

La validación del modelo de datos puede avanzar en paralelo con el prototipo y no bloquea su desarrollo. La integración real sí requiere validar el esquema, los permisos y la autenticación existentes.

## Documentación

- [Arquitectura técnica](ARCHITECTURE.md)
- [Reglas de negocio y metodología](BUSINESS_RULES.md)
- [Integración y modelo de datos pendiente](DATA_MODEL.md)
- [Instrucciones de desarrollo asistido](AGENTS.md)

No se proporcionan comandos de instalación o ejecución porque esta fase no contiene software ejecutable.
