# Policy Navigator

This project features an **AI-powered document assistant** developed during a Data Science Fellowship at the **Chicago Education Advocacy Cooperative (ChiEAC)**. It is designed to make complex public policy information, specifically **SNAP** (Supplemental Nutrition Assistance Program) and **Medicaid** more accessible by allowing users to query dense policy documents using natural language. This tool uses **Retrieval-Augmented Generation (RAG)** to provide precise, context-aware answers. Instead of digging through endless PDFs, users can ask natural language questions and get synthesized responses based directly on official documentation.

## Files Included
* **`Explainer_AI.ipynb`**: Main notebook containing the data extraction pipeline, FAISS indexing, and the RAG query system.
* **`Data/`**: Directory containing the source policy documents:
    * `MEDICAID.pdf`: Official Medicaid and CHIP overview.
    * `SNAP.pdf`: Policy basics for the Supplemental Nutrition Assistance Program.
* **`Images/`**: Contains sample screenshots of the application interface on Streamlit.

## Objectives
* **Simplify Policy Access**: Convert dense legal and governmental PDF text into searchable, conversational data.
* **Accuracy & Reliability**: Ensure that the AI only provides answers grounded in the provided source documents (SNAP and Medicaid manuals).
* **Efficiency**: Implement a high-performance vector search to retrieve relevant information in milliseconds.

## Technical Stack & Methods
* **Data Pipeline**: Used `pdfplumber` to extract text and `LangChain`'s `RecursiveCharacterTextSplitter` to create chunks of 500 characters with a 50-character overlap for context retention.
* **Vector Search**: Implemented `SentenceTransformers` (`all-MiniLM-L6-v2`) to generate 384-dimensional embeddings and `FAISS` (Facebook AI Similarity Search) for high-speed similarity retrieval.
* **Generative AI**: Integrated the `google/flan-t5-base` model to synthesize retrieved information into clear, concise responses.
* **Text Cleaning**: Applied custom regex functions to strip out "Policy Basics" headers, page numbers, and redundant whitespace.

## Key Features
* **Semantic Search**: Unlike keyword searches, this system understands the intent behind questions like "Who is eligible for SNAP?"
* **Dual-Mode Retrieval**: 
    * **Summary Mode**: Provides a concise paragraph answer.
    * **Full Context Mode**: Returns the exact text snippets from the policy manual for verification.
* **L2 Normalization**: Ensures that dot product calculations in FAISS function as cosine similarity for more accurate matching.

## How to Run
1. **Clone this repo**: 
   ```bash
   git clone [https://github.com/yourusername/benefit-explainer.git](https://github.com/yourusername/benefit-explainer.git)
2. **Install Dependencies**: 
   ```bash
   pip install faiss-cpu sentence-transformers transformers pdfplumber langchain
3. **Open the notebook**: Launch `Explainer_AI.ipynb` in Jupyter or VS Code.
4. **Execute**: Run all cells to initialize the vector index and begin querying the documents.

## Acknowledgments
A huge thank you to *Dr. Benjamin Drury* for the opportunity to work on tools that drive social impact at *ChiEAC* and in bringing this project to life!
