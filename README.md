# Sistema RAG - Política Monetaria Banrep

## Descripción

Este repositorio contiene la implementación de un sistema de Generación Aumentada por Recuperación (RAG) avanzado, diseñado específicamente para el dominio financiero y macroeconómico. El sistema procesa, indexa y consulta los últimos Informes de Política Monetaria (IPM) emitidos por el Banco de la República de Colombia, garantizando respuestas precisas y fundamentadas en la documentación oficial.

## Arquitectura y Características Implementadas

El pipeline de recuperación y generación integra múltiples técnicas de vanguardia para maximizar la relevancia del contexto y mitigar alucinaciones:

* **Procesamiento de Documentos:** Extracción de texto puro desde archivos PDF (PyMuPDF), con limpieza automatizada y normalización de léxico financiero.
* **Clasificación Zero-Shot:** Detección y etiquetado automático de secciones temáticas (inflación, actividad económica, sector externo, riesgos) mediante modelos de inferencia de lenguaje natural (NLI).
* **Chunking Estratégico:** Partición recursiva de texto con solapamiento, optimizada tras el análisis comparativo de múltiples enfoques (fijo, tokens, recursivo).
* **Vectorización y Base de Datos:** Generación de embeddings utilizando OpenAI (`text-embedding-3-large`) e indexación en Pinecone, enriqueciendo los vectores con metadatos estructurados (año, trimestre, página, sección).
* **Recuperación Semántica Avanzada:** Capacidad de filtrado por metadatos (pre-filtering) durante la búsqueda vectorial.
* **Expansión de Consultas (Query Expansion):** Implementación de expansión léxica estándar y HyDE (Hypothetical Document Embeddings), fusionando resultados mediante Reciprocal Rank Fusion (RRF).
* **Reranking:** Reordenamiento de documentos candidatos utilizando un modelo Cross-Encoder (`mmarco-mMiniLMv2`) para perfeccionar la selección del contexto.
* **RAG Conversacional:** Gestión de memoria de sesión iterativa combinada con "Self-Querying" para la abstracción autónoma de filtros temporales y temáticos a partir de lenguaje natural.
* **Evaluación Automática:** Suite de evaluación LLM-as-a-judge que mide métricas críticas en sistemas RAG: Faithfulness (fidelidad al contexto) y Relevance (relevancia de la respuesta).
* **Análisis Dimensional:** Reducción de dimensionalidad mediante UMAP para el análisis espacial y agrupación semántica de los fragmentos indexados.

## Stack Tecnológico

* **Base de Datos Vectorial:** Pinecone
* **Modelos de Lenguaje (LLMs):** OpenAI (gpt-4o, gpt-4o-mini)
* **Modelos de Embeddings y Reranking:** text-embedding-3-large, BAAI/bge-m3, cross-encoder/mmarco-mMiniLMv2
* **Procesamiento de Texto:** LangChain (Text Splitters), Hugging Face Transformers (pipeline NLI)
* **Manipulación de Datos y Análisis:** Pandas, NumPy, Scikit-learn, UMAP-learn, PyMuPDF
