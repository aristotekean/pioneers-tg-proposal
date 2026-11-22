# Calendario de ejecución en 17 semanas

Plan para ejecutar la propuesta «Gemelo digital urbano para la estimación espacial de pérdidas económicas por inundación pluvial en Chapinero, Bogotá» (`propuesta.tex`). Las semanas son relativas (S1 a S17) porque la propuesta no fija fecha de inicio. Cada fase cierra con el entregable y la comprobación definidos en la tabla de objetivos de la propuesta.

## Vista rápida

| Semanas | Fase | Objetivo | Entregable al cierre |
|---------|------|----------|----------------------|
| S1–S4 | Representación y base urbana | OE1 | E1. Base geográfica versionada, representación urbana y diseño de arquitectura |
| S5–S10 | Modelación | OE2 | E2. Modelos de IA, simulaciones de referencia y protocolo reproducible |
| S11–S13 | Integración y valoración | OE3 | E3. Prototipo integrado y mapas de amenaza, daño y pérdida |
| S14–S16 | Evaluación del sistema | OE4 | E4. Informe de evaluación, sensibilidad e incertidumbre |
| S17 | Cierre | Todos | Documento final y socialización con el tutor |

## Hitos

| Semana | Hito | Comprobación |
|--------|------|--------------|
| S4 | E1 entregado | Cobertura, procedencia y consistencia espacial verificadas |
| S7 | Partición de eventos y criterios de aceptación acordados | Registrados antes de entrenar y de abrir el conjunto de prueba |
| S10 | E2 entregado | Métricas en escenarios reservados, sin fuga de información |
| S13 | E3 entregado | Cada resultado es trazable hasta datos, modelo y parámetros |
| S16 | E4 entregado | Fidelidad al simulador y validez empírica reportadas por separado |
| S17 | Cierre | Revisión final del tutor |

## Detalle semanal

### Fase 1. Representación y base urbana (OE1)

| Semana | Tareas | Resultado |
|--------|--------|-----------|
| S1 | Inventariar topografía, drenaje, lluvia y edificaciones de toda la localidad. Solicitar los datos oficiales que requieran trámite. Crear el repositorio y la capa bronce con archivos originales y procedencia. | Inventario de fuentes con condiciones de uso |
| S2 | Registrar cobertura y vacíos por zona. Marcar las zonas sin información suficiente. Decidir si la salida será por edificación o por predio según la calidad del inventario. | Mapa de cobertura y vacíos |
| S3 | Armonizar unidades, coordenadas y cotas en la capa plata. Registrar transformaciones, versiones y errores, sin descartar registros de forma silenciosa. | Capa plata validada |
| S4 | Construir la representación 3D (edificios extruidos, LoD1). Definir los contratos entre las cinco capas. Verificar consistencia espacial. | **E1** |

### Fase 2. Modelación (OE2)

| Semana | Tareas | Resultado |
|--------|--------|-----------|
| S5 | Configurar el simulador hidrodinámico sobre un subdominio computacional. Definir el diseño de escenarios de lluvia. | Simulador operativo en un subdominio |
| S6 | Comprobar el simulador (balance de masa, sensibilidad a malla y rugosidad). Iniciar la generación de escenarios. Registrar el costo de cada simulación. | Simulador comprobado y primeras simulaciones |
| S7 | Continuar la generación de escenarios. Organizar los conjuntos en la capa oro. Separar eventos completos en entrenamiento, validación y prueba, agrupando variantes relacionadas. Acordar los criterios de aceptación. | Partición fijada y criterios de aceptación registrados |
| S8 | Entrenar el predictor sencillo de referencia. Medir MAE, RMSE y CSI en validación. | Línea base con métricas |
| S9 | Entrenar al menos un candidato de IA. Registrar tiempos de entrenamiento e inferencia, memoria y equipo. | Candidato de IA entrenado |
| S10 | Comparar la línea base y el candidato en validación. Seleccionar el modelo. Documentar el protocolo reproducible. | **E2** |

### Fase 3. Integración y valoración (OE3)

| Semana | Tareas | Resultado |
|--------|--------|-----------|
| S11 | Conectar las inferencias con los edificios. Seleccionar y justificar funciones de daño y valores de reposición, con moneda, año de valoración, tipología y aplicabilidad local. | Profundidad por edificación y parámetros de valoración documentados |
| S12 | Calcular pérdidas por escenario. Publicar las consultas en la API. Definir el nivel de agregación espacial de los resultados publicados. | Pérdidas por edificación y escenario consultables |
| S13 | Publicar mapas en el visor 2D/3D con incertidumbre y límites de uso. Señalar las zonas no modeladas. Probar el recorrido completo, de los datos a la pérdida. | **E3** |

### Fase 4. Evaluación del sistema (OE4)

| Semana | Tareas | Resultado |
|--------|--------|-----------|
| S14 | Evaluar el conjunto de prueba una sola vez: errores de profundidad y de pérdida, por edificio y agregados. Medir tiempo y memoria en el mismo equipo, separando el costo de generar simulaciones del costo de consulta. | Resultados de precisión y costo computacional |
| S15 | Variar lluvia, rugosidad, funciones de daño y valores expuestos. Contrastar las observaciones independientes disponibles. | Análisis de sensibilidad e incertidumbre |
| S16 | Redactar el informe de evaluación. Documentar fallos y límites de uso. Separar fidelidad al simulador y validez empírica. | **E4** |

### Cierre

| Semana | Tareas | Resultado |
|--------|--------|-----------|
| S17 | Integrar los resultados en el documento final. Congelar versiones de datos, modelos y parámetros. Socializar con el tutor e incorporar sus observaciones. | Documento final y prototipo versionado |

## Dependencias y riesgos

| Riesgo | Efecto | Respuesta |
|--------|--------|-----------|
| Los datos oficiales de drenaje o topografía llegan tarde o incompletos | Retrasa E1 y la configuración del simulador | Solicitarlos en S1. Trabajar en subdominios con cobertura suficiente y registrar el resto como no modelado. |
| La generación de simulaciones tarda más de lo previsto | Reduce el conjunto de entrenamiento y retrasa E2 | Medir el costo por simulación en S6 y ajustar el número de escenarios o el subdominio antes de S7. |
| No hay daños económicos observados | Impide afirmar exactitud monetaria empírica | Reportar sensibilidad y coherencia respecto al modelo de referencia, como prevé la propuesta. |
| No hay funciones de daño específicas para inundación pluvial en Colombia | Aumenta la incertidumbre de la pérdida | Adelantar la lectura de funciones candidatas durante S9–S10 e incluirlas en la sensibilidad de S15. |

## Reglas de seguimiento

- [ ] Reunión de seguimiento con el tutor al cierre de cada fase (S4, S10, S13, S16).
- [ ] El conjunto de prueba no se abre antes de S14.
- [ ] Cada entregable se versiona junto con los datos y parámetros que lo originan.
- [ ] Si una fase se retrasa más de una semana, se reduce el subdominio computacional, no el protocolo de evaluación.
