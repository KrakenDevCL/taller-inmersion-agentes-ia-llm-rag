# 🤖 Agente Híbrido de IA: RAG + Web Search (Proyecto Carrarurquía)

Este repositorio contiene la implementación de un **Agente de Inteligencia Artificial Híbrido** diseñado para resolver consultas complejas. El sistema decide de forma autónoma si debe buscar respuestas en **documentos técnicos internos** (PDFs de reportes empresariales) o realizar una **búsqueda en tiempo real en la Web**.

Desarrollado en el marco de la *Inmersión de Agentes de IA - Marzo 2026*.

## 🚀 Características Principales

* **Clasificación Inteligente:** Utiliza un nodo "Agente" que actúa como router para decidir la fuente de información más fiable.
* **RAG (Retrieval-Augmented Generation):** Procesamiento de reportes trimestrales de *Carrarurquía* mediante segmentación de texto (`RecursiveCharacterTextSplitter`) e indexación vectorial con `FAISS`.
* **Web Searching:** Integración con `SerpAPI` para obtener datos de actualidad que no están presentes en los documentos locales.
* **Arquitectura de Grafos:** Implementado con `LangGraph` para una gestión de estados robusta y circular.
* **Modelos Utilizados:** * **Generación:** `gemini-2.5-flash`
    * **Embeddings:** `models/gemini-embedding-001`

## 🛠️ Stack Tecnológico

* **Lenguaje:** Python 3.x
* **Orquestación:** LangChain & LangGraph
* **LLM:** Google Generative AI (Gemini API)
* **Base de Datos Vectorial:** FAISS (Facebook AI Similarity Search)
* **Búsqueda Externa:** SerpAPI

## 📐 Flujo del Grafo (Arquitectura)

El flujo lógico del agente es el siguiente:

1.  **START:** El usuario ingresa una pregunta.
2.  **Agente:** Clasifica la pregunta como `RAG` (específica de la empresa) o `Web` (general/actualidad).
3.  **RAG / Web:** Se ejecutan los nodos de extracción de contexto correspondientes.
4.  **Markdown:** Un nodo final sintetiza la respuesta con formato enriquecido.
5.  **END:** Entrega del resultado al usuario.

## 📋 Requisitos e Instalación

### 1. Variables de Entorno
Es necesario configurar los siguientes "Secrets" en tu entorno de ejecución (Google Colab o archivo `.env`):
* `API_KEY_GENAI`: Tu API Key de Google AI Studio.
* `SERPAPI_API_KEY`: Tu API Key de SerpAPI.

### 2. Librerías Necesarias
```bash
pip install -q google-genai langchain-community pypdf \
               langchain-text-splitters langchain-google-genai \
               faiss-cpu langgraph google-search-results
