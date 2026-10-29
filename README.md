# GBV_RAG
GBV Understanding RAG System
Topic
Helping users understand whether behaviours they describe may be associated with gender-based violence (GBV), using evidence-based sources.

Intended use
The system is an educational and supportive information tool. It can explain forms of GBV, identify behaviours described by a user, and explain why those behaviours may be concerning. It does not diagnose GBV, determine legal status, label a person a perpetrator, or make decisions for the user.

Source & Licence / Terms
The corpus used contains trusted GBV guidance and, where relevant, Kenyan legal sources. Recommended source types include WHO, UN Women, UNFPA, Kenyan government/GBV guidance, and Kenya Law. Record the source name, provenance, access date, file type and local file size. Verify the current terms before redistributing source documents.

Embedding Model
sentence-transformers/all-MiniLM-L6-v2

LLM
Google Gemini API. The API key is read from a Google Colab Secret named GEMINI_API_KEY and is never written in code.

Vector Database
ChromaDB, persisted to Google Drive.

Execution Instructions
Run the notebook in Google Colab.
Mount Google Drive when prompted.
Use a corpus containing trusted GBV guidance documents. Kenya Law documents may be retained as a legal-information supplement, but they should not be the only source for behaviour-identification questions.
Add GEMINI_API_KEY to Colab Secrets before Task 6.
Run top-to-bottom. The first run builds the corpus and vector database; later runs reload the persisted Chroma collection.
Safety and information disclaimer: This is an educational GBV information system, not a diagnostic, legal, medical, or emergency-response service.
