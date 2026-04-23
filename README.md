# RAG sobre la Constitución del Ecuador
### Demo FLISOL 2026 · LangChain + Ollama

Sistema de consulta legal basado en **Retrieval Augmented Generation (RAG)** que responde preguntas sobre la Constitución del Ecuador de 2021, citando los artículos exactos que sustentan cada respuesta.

Desarrollado como demo para FLISOL 2026, usando únicamente herramientas locales y de código abierto — sin APIs externas ni datos enviados a la nube.

---

## Stack

| Componente | Herramienta |
|---|---|
| LLM | Ollama `llama3.1:8b` |
| Embeddings | Ollama `nomic-embed-text` |
| Vector Store | Chroma (local, persistente) |
| Orquestación | LangChain |
| Notebook | Jupyter |

---

## Requisitos previos

### 1. Python 3.10+

### 2. Ollama instalado y corriendo
Descarga desde [ollama.com](https://ollama.com) y descarga los modelos:

```bash
ollama pull llama3.1:8b
ollama pull nomic-embed-text
```

### 3. Dependencias Python

```bash
pip install -r requirements.txt
```

---

## Uso

Abre el notebook y ejecuta las celdas en orden:

```bash
jupyter notebook demo_constitución.ipynb
```

El notebook está dividido en secciones autoexplicativas:

| Sección | Contenido |
|---|---|
| 0 | Instalación de dependencias |
| 1 | Carga del CSV con artículos constitucionales |
| 2 | Chunking inteligente por artículo |
| 3 | Creación de embeddings con Ollama |
| 4 | Construcción del vector store con Chroma |
| 5 | Configuración del LLM |
| 6 | Demostración del problema de alucinación |
| 7 | MultiQueryRetriever |
| 8 | Cadena RAG completa con memoria conversacional |
| 9 | Validación con 10 preguntas de prueba |
| 10 | Demo de memoria conversacional |

> **Nota:** La primera ejecución de la sección 4 tarda ~2-3 minutos mientras genera los embeddings. Las ejecuciones posteriores cargan el vector store desde disco instantáneamente.

---

## Estructura del repositorio

```
.
├── demo_constitución.ipynb   # Notebook principal
├── constitución.csv          # Artículos de la Constitución del Ecuador 2021
├── requirements.txt          # Dependencias Python
└── README.md
```

---

## Conceptos demostrados

- **RAG (Retrieval Augmented Generation):** combinar recuperación semántica con generación de texto para anclar las respuestas en documentos reales.
- **Chunking artículo-aware:** estrategia de división de textos legales que preserva el contexto del artículo en cada fragmento.
- **MultiQueryRetriever:** generación automática de variaciones de la consulta para mejorar la cobertura semántica.
- **Memoria conversacional:** seguimiento del historial de conversación para preguntas de seguimiento.
- **LLMs locales con Ollama:** inferencia completamente local, sin dependencia de APIs externas.
