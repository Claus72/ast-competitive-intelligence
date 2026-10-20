# Arquitectura técnica

## Estado

Propuesta documental del 20 de octubre de 2026. React + TypeScript + Vite y el prototipo ficticio están aprobados provisionalmente. No se crean todavía carpetas de código, contratos ejecutables ni dependencias.

## Responsabilidades

| Capa | Responsabilidad | Límites |
| --- | --- | --- |
| Aplicación | Navegación, selección de contexto y coordinación de evaluación | No calcula estadísticas en componentes |
| Dominio | Selección automática de muestra, estadísticas y futura clasificación | Independiente de React, gráficos, Supabase, OpenAI y circuito |
| Datos | Adaptación de fixtures y, posteriormente, del backend AST | No interpreta reglas ni presume estructuras PostgreSQL |
| Visualización | Evolución, divisiones, boxplot e indicadores | Consume el resultado común; no selecciona otra muestra |
| Interpretación | Narrativa sobre evaluación y contexto autorizados | No recalcula, clasifica ni aplica reclasificaciones |

El motor compartido atenderá ATT y APT mediante filtros y configuraciones explícitos. No habrá motores duplicados por circuito. Cada evaluación conservará un contexto de circuito, jugador y modalidad, sin mezclar modalidades. El mecanismo concreto de configuración se definirá antes de implementar el motor.

## Organización futura orientativa

```text
src/
  app/
  features/
    competitive-profile/
  domain/
    sampling/
    statistics/
    classification/
  data/
    contracts/
    fixtures/
    adapters/
  visualization/
  interpretation/
  shared/
```

Estas rutas describen responsabilidades futuras, no tablas ni servicios existentes. El módulo de clasificación es una reserva arquitectónica: no autoriza implementar reglas no suministradas. Los futuros expedientes y flujos del Comité serán módulos adicionales que consuman evaluaciones, conservando su separación respecto del motor.

## Flujo de evaluación

Selección de contexto → datos normalizados → selección de muestra en el dominio → estadísticas → resultado común de evaluación → gráfico, boxplot, indicadores y, posteriormente, narrativa.

El resultado común deberá expresar conceptualmente:

- Contexto evaluado, fecha de referencia y configuración/metodología utilizada.
- Partidos considerados, pertenencia a la muestra y razones de inclusión o exclusión.
- Estrategia temporal elegida, número de partidos y suficiencia o carácter diagnóstico.
- Q1, mediana y Q3 sobre `rating_out`; tendencia sobre la misma muestra en puntos por partido.
- Advertencias de calidad y procedencia ficticia o real.

Esto es una propuesta de contrato interno, pendiente de validación; no un esquema de persistencia. Cambiar contexto o fecha deberá actualizar a todos los consumidores con el mismo resultado. Los límites de división son contexto de visualización cuya fuente y vigencia deben confirmarse, sin deducirlos del rating.

## Prototipo previo al motor

El prototipo usará fixtures ficticios con resultados precalculados y estados de muestra simulados. Permitirá validar selección, sincronización, leyendas, divisiones e interpretación visual sin implementar todavía los algoritmos. Tanto los datos como los resultados mostrarán su naturaleza ficticia. No se presentará como validación matemática o reglamentaria del motor.

## Integración e identidad

Supabase/PostgreSQL es el backend existente previsto; su integración requiere autorización posterior y el esquema real. Primero se revisarán autenticación, sesiones, permisos y mecanismos de acceso del ecosistema AST. La ubicación definitiva del frontend dentro del ecosistema y la ejecución del motor en cliente o servidor permanecen abiertas. Los cálculos deben ser portables para no decidir esa ubicación prematuramente.

La futura narrativa con OpenAI necesitará definir ejecución, protección de credenciales, datos permitidos y trazabilidad. No se enviarán datos ni se incorporará un cliente de IA durante el prototipo.

## Verificación prevista por fase

- Documentación: coherencia de reglas, pendientes y restricciones entre documentos.
- Prototipo: validación funcional y visual con escenarios ficticios, incluida muestra insuficiente.
- Motor: pruebas de ventanas, límites, orden cronológico, cuartiles, tendencia y aislamiento por modalidad/circuito con los casos suministrados.
- Integración: contrastar contratos con esquema e identidad reales y verificar acceso en un entorno autorizado.
- IA: fidelidad al resultado común y ausencia de decisiones o cifras inventadas.

## Decisiones abiertas

Librería de gráficos; integración del frontend en AST; ubicación de ejecución del motor; detalles metodológicos enumerados en BUSINESS_RULES.md; contratos reales de datos y autenticación; políticas y modelo para narrativa. No es necesario resolverlas para cerrar esta fase documental. Cada dependencia futura deberá tener una necesidad concreta y someterse a revisión antes de incorporarla.
