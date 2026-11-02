# GBV Understanding RAG System

A Retrieval-Augmented Generation (RAG) system that helps users understand whether behaviours they describe may be associated with gender-based violence (GBV), using information retrieved from trusted guidance and relevant Kenyan legal sources.

## Project Overview

This project explores how document processing, semantic search, vector databases, and large language models can work together to retrieve and explain information from a specialised knowledge base.

The system accepts a user's description of a behaviour, retrieves relevant information from its document corpus, and uses Google Gemini to generate an evidence-informed explanation.

The goal is to make reliable GBV information easier to understand while maintaining clear boundaries around the system's intended use.

## Technical Stack

| Component | Technology |
|---|---|
| Programming Language | Python |
| Development Environment | Google Colab |
| Embedding Model | `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Database | ChromaDB |
| Language Model | Google Gemini API |
| Storage | Google Drive |
| Retrieval Approach | Semantic Search |
| API Authentication | Google Colab Secrets |

## System Pipeline

The system follows a document-processing and retrieval pipeline:

1. **Document Collection:** Collect trusted GBV guidance documents and relevant Kenyan legal sources.
2. **Document Processing:** Load and prepare documents for retrieval.
3. **Text Chunking:** Divide document content into smaller sections suitable for embedding and retrieval.
4. **Embedding Generation:** Use Sentence Transformers to convert text chunks into vector representations.
5. **Vector Storage:** Store embeddings and associated document information in a persistent ChromaDB collection.
6. **Semantic Retrieval:** Convert user queries into embeddings and retrieve relevant document sections based on semantic similarity.
7. **Response Generation:** Pass retrieved context to Google Gemini to generate an understandable, context-informed response.

### Pipeline Flow

`Source Documents → Document Processing → Text Chunking → Embeddings → ChromaDB → Semantic Retrieval → Gemini → Response`

## Data Sources and Provenance

The knowledge corpus is designed around trusted GBV information sources, including:

- World Health Organization (WHO)
- UN Women
- United Nations Population Fund (UNFPA)
- Kenyan government and GBV guidance publications
- Kenya Law

Each source should be documented with:

- Source name and publisher.
- Original document or source URL.
- Date accessed.
- File type.
- Local file size.
- Applicable licence or redistribution terms.

The corpus combines educational guidance with relevant legal information. Kenyan legal documents serve as a legal-information supplement rather than the sole basis for identifying potentially concerning behaviours.

## Models and Retrieval

### Embedding Model

`sentence-transformers/all-MiniLM-L6-v2`

The embedding model converts document chunks and user queries into numerical vector representations. These representations support semantic retrieval, allowing the system to retrieve conceptually related information rather than relying exclusively on exact keyword matches.

### Vector Database

ChromaDB stores the generated embeddings and associated document information.

The collection is persisted to Google Drive so that subsequent notebook executions can reuse the existing vector database instead of rebuilding it every time.

### Language Model

Google Gemini API generates responses using the information retrieved from the knowledge base.

The API key is accessed through Google Colab Secrets using `GEMINI_API_KEY` and is not hardcoded into the notebook.

## Evaluation and Reliability Considerations

The quality of a RAG system depends on both retrieval relevance and the quality of the generated response.

Important evaluation areas include:

- **Retrieval relevance:** Whether retrieved document sections are relevant to the user's question.
- **Context coverage:** Whether the retrieved information adequately addresses the behaviour being described.
- **Response grounding:** Whether generated explanations remain consistent with the retrieved information.
- **Source quality:** Whether retrieved documents come from trusted and appropriate sources.
- **Consistency:** Whether similar queries produce reasonably consistent and relevant explanations.

Potential limitations include incomplete document coverage, irrelevant retrieval results, ambiguous user descriptions, and generated responses that misinterpret retrieved context.

These are important areas for further testing and improvement.

## Reproducibility

The project is implemented in a Google Colab notebook.

To reproduce the workflow:

1. Open the notebook in Google Colab.
2. Mount Google Drive when prompted.
3. Provide the trusted GBV guidance documents used as the knowledge corpus.
4. Add `GEMINI_API_KEY` to Google Colab Secrets.
5. Run the notebook from top to bottom.
6. Allow the first execution to process the documents, generate embeddings, and build the ChromaDB collection.
7. Subsequent executions reload the persisted collection from Google Drive.

The notebook contains the processing and retrieval workflow.

## Security and Responsible Use

The project follows basic security practices:

- API credentials are stored in Google Colab Secrets.
- API keys are not hardcoded into the notebook.
- Document provenance and redistribution terms should be verified.
- Retrieved information is intended to support educational explanations, not automated decisions.

### Intended Use and Limitations

This system is an educational and supportive information tool.

It can explain forms of GBV, identify behaviours described by a user that may be associated with GBV, and explain why those behaviours may be concerning.

It does not:

- Diagnose GBV.
- Determine legal status.
- Label individuals as perpetrators.
- Make decisions on behalf of users.
- Replace professional, legal, medical, or emergency support.

## Future Improvements

Potential areas for further development include:

- Establishing a labelled evaluation dataset for retrieval testing.
- Measuring retrieval quality using Precision@K, Recall@K, and Mean Reciprocal Rank (MRR).
- Comparing embedding models to understand their effect on retrieval relevance.
- Evaluating chunk sizes and retrieval configurations.
- Introducing automated tests for document processing and retrieval.
- Improving source attribution and response grounding.
- Testing system behaviour against ambiguous and incomplete queries.

## Project Focus

This project demonstrates practical experience with Python-based data processing, semantic search, embedding models, vector databases, and LLM integration.

It also explores the importance of data quality, retrieval relevance, reproducibility, and responsible use when building machine-learning-powered applications.
