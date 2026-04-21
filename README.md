# Generador de Prompts para Búsqueda de Empleos IA (n8n + Gemini + Telegram)

<img width="3368" height="1798" alt="image" src="https://github.com/user-attachments/assets/cbc18284-9691-4cfa-8945-c7da1f9ca7a5" />

##  Descripción del Proyecto
Este repositorio documenta un sistema de automatización diseñado para optimizar la fase de búsqueda y filtrado de vacantes para los puestos destinados al área de tecnología. 

A diferencia de las búsquedas manuales o el uso de APIs de empleo limitadas, este flujo utiliza Inteligencia Artificial para leer el CV del candidato, analizar sus *hard skills*, y generar una estrategia de búsqueda que es enviada directamente a Telegram. Esta estrategia estructurada está lista para ser ejecutada en búsquedas manuales avanzadas o procesada por LLMs externos (como Claude) para descubrir vacantes ocultas en el mercado corporativo.

**Por políticas de ciberseguridad y protección de credenciales, el archivo exportable del flujo (`.json`) no se incluye en este repositorio público.** Los flujos de n8n almacenan la estructura completa de la integración, la cual puede contener punteros a variables de entorno, configuraciones de nodos de Telegram y accesos a la API de Google Gemini. Para mantener las mejores prácticas de seguridad, este repositorio documenta la lógica del negocio mediante la arquitectura visual (screenshot) y la explicación del código de transformación, demostrando la capacidad de integración sin comprometer el entorno.

## Arquitectura del Sistema 
El flujo de trabajo automatizado sigue esta secuencia lineal:
1. **Usuario adjunta CV:** Trigger inicial que recibe el documento PDF del perfil del candidato y además se procede a un filtraje mediante a un cuestionario donde se se elaboraron preguntas respecto a las comodidades y preferencias del usuario para su posible puesto.
2. **Edit Fields & Extracción:** Limpieza de metadatos y conversión del archivo PDF a texto plano procesable para el análisis.
3. **Análisis del CV (AI Agent):** El modelo de Google Gemini evalúa el perfil técnico y define una estrategia de zonas y palabras clave booleanas, para además de tener las comodidades adjuntadas mediante el cuestionario tambiñen tener el análisis del CV.
4. **Formato para organizar la inf:** Un nodo de Código (JavaScript) toma el JSON crudo del agente y lo consolida en un bloque de texto estructurado y legible.
5. **Envía mensaje a Telegram:** Consumo de la API de Telegram para enviar el reporte final instantáneamente al dispositivo móvil del usuario.

