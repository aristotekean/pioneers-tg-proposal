# Gemelo digital urbano para pérdidas por inundación pluvial en Chapinero

Propuesta de trabajo de grado: un gemelo digital urbano de la localidad de Chapinero, Bogotá, que estima pérdidas económicas directas por inundación pluvial en edificaciones mediante simulación hidrodinámica, modelos de IA y funciones de daño.

El documento final es [`propuesta.pdf`](propuesta.pdf).

| | |
|---|---|
| Autores | Kevin Andrey Bueno Solano y Diego Alejandro Cortes Suarez |
| Programa | Maestría en Inteligencia Artificial, Pontificia Universidad Javeriana |
| Curso | Seminario de investigación. Profesor: Andrés Moreno Barbosa |
| Tutor | Andrés Oswaldo Calderón Romero |
| Estado | Propuesta en revisión; la revisión final del tutor está pendiente |

## Compilar

Requiere una distribución de LaTeX con `latexmk` y la clase `IEEEtran`.

```bash
latexmk -pdf propuesta.tex
```

El resultado es `propuesta.pdf`, de cinco páginas en formato IEEE de revista.

## Archivos

| Archivo | Contenido |
|---|---|
| `propuesta.tex` | Fuente de la propuesta. Es la versión de referencia. |
| `propuesta.pdf` | PDF compilado desde `propuesta.tex`. |
| `propuesta.docx.md` | Versión en Markdown de una revisión anterior. Puede no reflejar los últimos cambios. |
| `arquitectura.png` | Diagrama de arquitectura. El `.tex` no lo usa; sus figuras se dibujan con TikZ. |

## Contenido de la propuesta

1. Estado del arte y lectura crítica de las fuentes.
2. Pregunta de investigación y objetivos.
3. Aproximación metodológica: alcance, arquitectura de cinco capas, datos con Medallion, valoración, protocolo de evaluación y uso responsable de las estimaciones.
4. Socialización y retroalimentación del tutor.

## Uso de IA generativa

Los autores usaron Claude Code (Anthropic) con el modelo Claude Fable 5.2, configurado con [gentle-ai](https://github.com/Gentleman-Programming/gentle-ai), como apoyo en la redacción y la revisión de estilo. La declaración completa está en la sección de agradecimientos del documento.
