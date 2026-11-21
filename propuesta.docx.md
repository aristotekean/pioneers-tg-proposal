# Gemelo digital urbano para la estimación espacial de pérdidas económicas por inundación pluvial en Chapinero, Bogotá, mediante modelos de IA

Kevin Andrey Bueno Solano y Diego Alejandro Cortes Suarez

Pontificia Universidad Javeriana · Facultad de Ingeniería · Maestría en Inteligencia Artificial

Seminario de investigación · Profesor Andrés Moreno Barbosa

**Nota de revisión: el resaltado amarillo identifica los cambios aplicados a partir de la retroalimentación de Andrés Calderón Romero.**

Tutor y potencial director: Andrés Oswaldo Calderón Romero

Resumen. Se propone construir y evaluar un gemelo digital urbano de la localidad de Chapinero, Bogotá, para estimar pérdidas económicas directas por inundación pluvial y apoyar la gestión del riesgo. El prototipo integrará una representación urbana, un modelo hidrodinámico, inteligencia artificial y funciones de daño. La arquitectura de cinco capas organiza el sistema y Medallion gestiona la trazabilidad de los datos. La revisión crítica de seis fuentes identifica aportes y límites en representación, amenaza, vulnerabilidad y valoración. La evaluación distinguirá fidelidad al simulador y validez frente a observaciones, e incluirá precisión, costo computacional e incertidumbre. El alcance inicial corresponde a simulaciones por escenario con datos versionados, sin operación en tiempo real.

Palabras clave: gemelo digital urbano, gestión del riesgo, inundación pluvial, inteligencia artificial, pérdidas económicas, Medallion.

# I. ESTADO DEL ARTE Y LECTURA CRÍTICA

La evaluación de pérdidas por inundación requiere conectar amenaza, exposición, vulnerabilidad y valor económico. Se seleccionaron seis artículos de la biblioteca por su pertinencia para esa cadena, detalle metodológico, evidencia de evaluación y posibilidad de reutilización. La selección es temática y metodológica; no se atribuye centralidad bibliográfica sin verificar enlaces y leyendas de los grafos. Los estudios de otras amenazas se incluyen por sus métodos transferibles, no por equivalencia entre sus parámetros físicos.

Yu et al. \[1\], vinculados con la Earthquake Agency de Ningxia, la China Earthquake Administration y Nanjing Normal University, integran fotogrametría, LiDAR y respuesta estructural para representar daños sísmicos en Pingluo, China. La vinculación entre edificios y daño orienta la representación urbana propuesta. No obstante, su índice de daño y la ecuación estructural no equivalen a pérdidas monetarias. La lectura crítica de la sección 3.2 y las figuras 7 y 8 impide confundir visualización de daño con valoración económica.

Sañudo et al. \[2\], de Universidade da Coruña/CITEEC y RWTH Aachen, acoplan superficie 2D y drenaje 1D en IberSWMM+ para inundación pluvial. Sus ensayos y aplicaciones en Alemania y España respaldan avances computacionales, aunque Morón de la Frontera carece de observaciones para validar un evento real. Dellinger et al. \[3\], desde ICube, ENGEES, Université de Montpellier e INRAE en Francia, comparan modelos 2D y 3D con mediciones experimentales. La similitud global de caudales y las diferencias locales de velocidad orientan la complejidad del simulador según las variables de daño, sin asegurar mejoras equivalentes en la valoración económica.

Tascón-González et al. \[4\], del grupo Q-GEO de la Universidad de León, estiman vulnerabilidad por parcela con datos abiertos en Ponferrada, España. El índice evidencia heterogeneidad espacial: el 22,7 % de las parcelas supera 0,4. Sin embargo, es adimensional y corresponde a una rotura hipotética de presa. Su aporte es la integración parcelaria de información; no proporciona directamente una fracción monetaria de daño para lluvia urbana.

Zhu \[5\], de Nanjing University of Information Science and Technology, combina GAN-ALSTM, Monte Carlo y rentabilidad aseguradora para Estados Unidos y China. Lan y Wang \[6\], de Ocean University of China, relacionan pérdidas y factores de suscripción. Ambos aportan formulaciones financieras, pero la escala agregada y la documentación limitada de validación independiente restringen su transferencia a edificios de Chapinero. Sus resultados no justifican anticipar superioridad de una familia de IA ni precisión económica local.

La oportunidad consiste en integrar y evaluar estos componentes con trazabilidad entre datos, inundación, daño y pérdida. La interacción débil señalada en los grafos es un indicio que exige verificar cobertura y enlaces. Diversidad metodológica, multidisciplinariedad y menor ventana de citación de trabajos recientes son explicaciones posibles, no demostradas por la desconexión visual. Tampoco se concluye que no existan soluciones integradoras. La pregunta que cierra esta síntesis incorpora las tres dimensiones de evaluación recomendadas por el tutor: precisión, costo computacional e incertidumbre.

¿Con qué precisión, costo computacional e incertidumbre puede un gemelo digital urbano estimar las pérdidas económicas directas en edificaciones de la localidad de Chapinero, Bogotá, ante escenarios de inundación por lluvia intensa y limitaciones de información sobre la amenaza y la vulnerabilidad?

# II. PREGUNTA DE INVESTIGACIÓN Y OBJETIVOS

## *A. Pregunta de investigación*

¿Con qué precisión, costo computacional e incertidumbre puede un gemelo digital urbano estimar las pérdidas económicas directas en edificaciones de la localidad de Chapinero, Bogotá, ante escenarios de inundación por lluvia intensa y limitaciones de información sobre la amenaza y la vulnerabilidad?

## *B. Objetivo general*

Construir y evaluar un gemelo digital urbano de la localidad de Chapinero que integre simulación hidrodinámica, inteligencia artificial y valoración de daños para estimar espacialmente pérdidas económicas directas en edificaciones como apoyo a la gestión del riesgo de inundación pluvial, cuantificando su precisión, costo computacional e incertidumbre.

## *C. Objetivos específicos*

OE1. Construir la base del gemelo digital de la localidad de Chapinero mediante una arquitectura de cinco capas (servicios, cognitiva, virtual, datos y física) orientada a la gestión del riesgo de inundación pluvial.

OE2. Desarrollar un modelo de inteligencia artificial para estimar la inundación pluvial a partir de escenarios de lluvia y datos urbanos gestionados mediante la arquitectura Medallion.

OE3. Integrar el modelo de inteligencia artificial y la valoración económica de daños en el gemelo digital para consultar pérdidas por edificación y escenario.

OE4. Evaluar la precisión, el costo computacional y la incertidumbre del sistema integrado frente al modelo hidrodinámico de referencia y las observaciones disponibles.

# III. APROXIMACIÓN METODOLÓGICA

## *A. Alcance y condiciones de aplicación*

El ámbito geográfico es la localidad de Chapinero, Bogotá. Se inventariará la cobertura de datos para toda la localidad y se registrarán las zonas sin información suficiente. Los ensayos podrán usar subdominios computacionales sin modificar el alcance geográfico ni presentar zonas no modeladas como validadas. La salida será por edificación o predio, según la calidad del inventario.

El prototipo estimará daños económicos directos por inundación pluvial para apoyar la gestión del riesgo. Parqueaderos subterráneos se incluirán únicamente con cotas de acceso, geometría e inventarios suficientes. Deslizamientos, daños indirectos y tarificación de seguros se conservan como ampliaciones. La capa de servicios ofrecerá mapas e indicadores por escenario; no se plantea un sistema de alerta temprana operativo.

## *B. Organización del gemelo y datos*

Se adopta una organización de cinco capas: física, para identificar el territorio, el drenaje y los activos; datos, para gestionar fuentes y trazabilidad; virtual, para representar la ciudad y ejecutar el modelo físico; cognición, para inferencia mediante IA y análisis del daño; y servicio, para publicar consultas y visualización 2D/3D. Esta organización es una decisión del proyecto cuya referencia bibliográfica específica debe completarse.

El alcance inicial es un prototipo experimental con datos oficiales y simulaciones versionadas. No incluye sensores IoT, sincronización observada en tiempo real ni control del sistema físico. Estas limitaciones se harán explícitas al usar la denominación gemelo digital. El modelo de ciudad tendrá, según disponibilidad, edificios extruidos sobre el terreno (LoD1).

Medallion organiza la preparación de datos que alimenta la cognición: bronce conserva archivos originales y procedencia; plata contiene información validada y armonizada; oro contiene conjuntos para modelación y resultados analíticos. Se registrarán transformaciones, versiones y errores, sin descartar registros silenciosamente. Los cálculos espaciales utilizarán coordenadas y unidades apropiadas al modelo; las conversiones para visualización se verificarán por separado.

# TABLA I. OBJETIVOS, ACTIVIDADES, TAREAS Y ENTREGABLES

La secuencia separa la base urbana, el aprendizaje, la integración y la evaluación. Las actividades concretan los objetivos sin sustituirlos por una lista de operaciones.

| Objetivo | Actividad | Tareas principales | Entregable y comprobación |
| :---- | :---- | :---- | :---- |
| OE1 | Representación y base urbana | Inventariar topografía, drenaje, lluvia y edificaciones de toda la localidad. Registrar cobertura y vacíos. Armonizar unidades, coordenadas y cotas. Construir la representación 3D y definir contratos entre las cinco capas. | E1. Base geográfica versionada, representación urbana y diseño de arquitectura. Verificación de cobertura, procedencia y consistencia espacial. |
| OE2 | Modelación física y aprendizaje | Configurar y comprobar el simulador hidrodinámico. Generar escenarios. Organizar datos en bronce, plata y oro. Separar eventos de entrenamiento, validación y prueba. Comparar un predictor sencillo con al menos un candidato de IA. | E2. Modelo de IA, simulaciones de referencia y protocolo reproducible. Métricas en escenarios reservados, sin fuga de información. |
| OE3 | Integración y valoración | Conectar inferencias con edificios. Seleccionar y justificar funciones de daño y valores de reposición. Calcular pérdidas por escenario. Publicar mapas y consultas en la API y el visor 2D/3D. Probar el recorrido completo. | E3. Prototipo integrado y mapas de amenaza, daño y pérdida. Trazabilidad de cada resultado hasta datos, modelo y parámetros. |
| OE4 | Evaluación del sistema | Medir errores de profundidad y pérdidas, tiempo y memoria en el mismo equipo. Contrastar observaciones disponibles. Variar lluvia, rugosidad, funciones de daño y valores. Documentar fallos y límites de uso. | E4. Informe de evaluación, sensibilidad e incertidumbre. Separación explícita entre fidelidad al simulador y validez empírica. |

## *C. Valoración y protocolo de evaluación*

La pérdida por escenarios se calculará como Lₛ \= Σᵢ Vᵢ · dᵢ,ₛ, donde Vᵢ es el valor de reposición y dᵢ,ₛ una fracción de daño entre 0 y 1 obtenida de una función justificada. Se documentarán moneda, año de valoración, tipología y aplicabilidad local. Un índice multicriterio o una clase sísmica no se interpretarán directamente como porcentaje de pérdida. Sin probabilidades de ocurrencia suficientes, se reportarán pérdidas por escenario, no pérdidas anuales esperadas.

Se reservarán eventos o escenarios completos para prueba. Los conjuntos relacionados se agruparán para evitar que variantes casi idénticas contaminen entrenamiento y evaluación. El error de profundidad se medirá con MAE y RMSE; la pérdida se comparará por edificio y agregada. Se registrarán tiempos de entrenamiento e inferencia, memoria y características del equipo, distinguiendo el costo de generar simulaciones del costo de consulta.

La incertidumbre se analizará variando lluvia, parámetros hidráulicos, funciones de daño y valores expuestos. Los intervalos serán condicionados a esos supuestos. Se contrastarán observaciones independientes cuando existan. Si faltan daños económicos observados, se reportará sensibilidad y coherencia respecto al modelo de referencia, sin afirmar exactitud monetaria empírica. Los criterios de aceptación se acordarán antes de evaluar el conjunto de prueba.

# IV. SOCIALIZACIÓN Y RETROALIMENTACIÓN

La transcripción «seguimiento seminario de investigación .vtt», aportada por Diego, documenta la revisión de Andrés Oswaldo Calderón Romero con Kevin Andrey Bueno Solano y Diego Alejandro Cortes Suarez. El archivo contiene marcas relativas hasta aproximadamente 19 min 36 s, pero no identifica de forma explícita la fecha de la reunión. Constituye evidencia del intercambio, no una aprobación final de esta versión.

00:00:44–00:00:59. Incluir gestión del riesgo en las palabras clave. Se incorpora y se expresa el uso de las estimaciones como apoyo a su gestión.

00:01:46–00:02:12. Unificar el alcance en la localidad de Chapinero. Título, resumen, pregunta, objetivo general y metodología emplean la misma delimitación.

00:02:42–00:02:55. Añadir costo computacional a la pregunta. Se alinean pregunta, objetivo general y evaluación en precisión, costo e incertidumbre.

00:03:23–00:04:07. Vincular el propósito con la gestión del riesgo. Se conserva la estimación de pérdidas y se evita prometer mitigación física del daño.

00:04:32–00:07:33 y 00:15:13–00:18:13. Sintetizar objetivos y reorganizarlos en construcción, IA, integración y evaluación. Se formulan cuatro objetivos con un verbo principal y se trasladan las tareas a la metodología.

00:08:19–00:09:15. Organizar objetivos, actividades, tareas y entregables en una tabla. La tabla I establece esa correspondencia y añade criterios de comprobación.

00:09:40–00:10:34. Combinar estado del arte y lectura crítica. La sección I incorpora aportes, limitaciones y justificación de selección, sin un capítulo repetido.

00:16:00–00:16:16. Identificar una referencia para la arquitectura por capas. Permanece pendiente identificar el artículo mencionado por Kevin. Las cinco capas se presentan como organización adoptada, sin referencia inventada ni reivindicación de originalidad.

00:18:43–00:19:32. Remitir la nueva versión para un último chequeo. La revisión final del tutor sobre este documento continúa pendiente.

Los pasajes se sintetizan por contexto para no reproducir errores del reconocimiento automático. Las explicaciones de Kevin sobre Medallion y las capas se distinguen de las recomendaciones del tutor. La revisión final solicitada por Andrés permanece pendiente y no se presume realizada.

# REFERENCIAS

\[1\] S. Yu, Q. Lei, C. Liu, N. Zhang, S. Shan y X. Zeng, “Application research on digital twins of urban earthquake disasters,” *Geomatics, Natural Hazards and Risk*, vol. 14, n.º 1, art. 2278274, 2023\. [doi: 10.1080/19475705.2023.2278274](https://doi.org/10.1080/19475705.2023.2278274).

\[2\] E. Sañudo *et al.*, “IberSWMM+: A high-performance computing solver for 2D-1D pluvial flood modelling in urban environments,” *Journal of Hydrology*, vol. 651, art. 132603, 2025\. [doi: 10.1016/j.jhydrol.2024.132603](https://doi.org/10.1016/j.jhydrol.2024.132603).

\[3\] G. Dellinger *et al.*, “Assessing 3D and 2D hydrodynamic models for urban flood simulations: a district scale analysis with experimental street-level discharge, height and velocity,” *Urban Water Journal*, vol. 22, n.º 9, pp. 1084-1102, 2025\. [doi: 10.1080/1573062X.2025.2531460](https://doi.org/10.1080/1573062X.2025.2531460).

\[4\] L. Tascón-González, M. Ferrer-Julià y E. García-Meléndez, “Methodological approach for mapping the flood physical vulnerability index with geographical open-source data: an example in a small-middle city (Ponferrada, Spain),” *Natural Hazards*, vol. 120, pp. 4053-4081, 2024\. [doi: 10.1007/s11069-023-06370-7](https://doi.org/10.1007/s11069-023-06370-7).

\[5\] F. Zhu, “Forecasting Catastrophe: Integrating GAN-ALSTM and Monte Carlo Simulations for Insurance Underwriting in Extreme Weather,” en *2024 IEEE 2nd International Conference on Sensors, Electronics and Computer Engineering (ICSECE)*, pp. 928-932, 2024\. [doi: 10.1109/ICSECE61636.2024.10729306](https://doi.org/10.1109/ICSECE61636.2024.10729306).

\[6\] C. Lan y Z. Wang, “Risk Assessment and Pricing Model of Natural Disaster Insurance Based on EVM-Topsis,” en *2024 International Conference on Data Science and Network Security (ICDSNS)*, pp. 1-7, 2024\. [doi: 10.1109/ICDSNS62112.2024.10690990](https://doi.org/10.1109/ICDSNS62112.2024.10690990).