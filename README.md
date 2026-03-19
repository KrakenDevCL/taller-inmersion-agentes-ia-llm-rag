🤖 Agente Híbrido de IA: RAG + Web Search (Carrarurquía)
Este proyecto implementa un agente inteligente capaz de responder consultas de dos formas: analizando documentos internos (PDFs de reportes trimestrales de la empresa ficticia Carrarurquía) o realizando búsquedas en tiempo real en la web.

Utiliza una arquitectura de Grafo de Estados (LangGraph) para clasificar la intención del usuario y decidir la fuente de información más adecuada.

🚀 Características Principales
RAG (Retrieval-Augmented Generation): Extracción de conocimiento desde reportes en formato PDF utilizando FAISS como base de datos vectorial.

Web Search Integration: Capacidad de consultar internet mediante SerpAPI para preguntas de cultura general o actualidad (ej. deportes, eventos 2026).

Orquestación con LangGraph: Un flujo de control lógico que decide dinámicamente el camino de la respuesta.

Modelos de Última Generación: Implementado con Gemini 2.5 Flash para razonamiento y generación de contenido, y Gemini Embeddings para la vectorización.

Salida Multiformato: Respuestas siempre entregadas en un formato Markdown elegante y estructurado.

🛠️ Stack Tecnológico
Lenguaje: Python (Google Colab)

LLM: Google Generative AI (gemini-2.5-flash)

Orquestador: LangChain / LangGraph

Base de Datos Vectorial: FAISS (Facebook AI Similarity Search)

Herramientas de Búsqueda: SerpAPI

Procesamiento de Documentos: PyPDF / LangChain Document Loaders

📐 Arquitectura del Agente
El flujo del agente sigue el siguiente esquema lógico:

Agente (Clasificador): Recibe la pregunta y decide si es para "RAG" (Documentos locales) o "Web".

Nodo RAG: Si la pregunta es sobre Carrarurquía, busca en los fragmentos de PDF.

Nodo Web: Si la pregunta es general, realiza una búsqueda en Google.

Nodo Markdown: Recibe el contexto y genera la respuesta final formateada.

📋 Requisitos Previos
Necesitarás configurar las siguientes variables de entorno (Secretos en Colab):

API_KEY_GENAI: Tu clave de API de Google AI Studio.

SERPAPI_API_KEY: Tu clave de API de SerpAPI para búsquedas web.

💻 Instalación
Bash
pip install -q google-genai langchain-community pypdf langchain-text-splitters \
               langchain-google-genai faiss-cpu langgraph google-search-results
📖 Ejemplo de Uso
Consulta de Documentos Internos (RAG)
Pregunta: "¿Dónde se mantuvo concentrado el mix de productos?"
Decisión del Agente: RAG
Respuesta: "El mix de productos se mantuvo concentrado en circuitos combinados (Estambul + Capadocia)."

Consulta de Información General (Web)
Pregunta: "¿Cuántos mundiales de fútbol tiene Brasil?"
Decisión del Agente: Web
Respuesta: "Brasil ha conquistado la Copa Mundial de Fútbol en cinco (5) ocasiones (1958, 1962, 1970, 1994, 2002)..."

📂 Estructura de Datos
El sistema carga automáticamente los archivos PDF en la carpeta /PDFs, los divide en fragmentos de 400 caracteres con un solapamiento de 40 para no perder contexto y los indexa en la base vectorial.

Desarrollado como parte de la Inmersión en Agentes de IA - 2026.
