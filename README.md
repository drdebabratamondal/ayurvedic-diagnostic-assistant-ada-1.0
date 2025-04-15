# Ayurvedic Diagnostic Assistant (ADA) with Gemini & RAG

This repository contains a Kaggle notebook implementing an **Ayurvedic Diagnostic Assistant (ADA)**. The project leverages Google's Gemini 2.0 Flash model combined with Retrieval-Augmented Generation (RAG) to analyze patient symptoms based on traditional Ayurvedic principles (Tridosha theory) and provide structured diagnostic suggestions.

## Overview

The ADA aims to bridge traditional Ayurvedic wisdom with modern AI capabilities. It takes patient symptoms described in natural language as input and performs the following:

1.  Analyzes symptoms to identify potential dominant Doshas (Vata, Pitta, Kapha) and imbalances.
2.  Retrieves relevant information from a corpus of Ayurvedic texts using RAG to ground its analysis.
3.  Generates a structured diagnostic report in JSON format, detailing:
    *   Dominant Dosha
    *   Identified Imbalances
    *   Provisional Diagnosis
    *   Supporting Evidence (symptom correlation, potential pulse/tongue indications)
    *   Recommended Treatments (categorized: dietary, herbs, medicines, therapies, lifestyle)
4.  Presents the results in a user-friendly HTML format within an interactive notebook interface.

## Features

*   **Gemini 2.0 Flash Integration:** Utilizes Google's efficient and capable language model.
*   **Retrieval-Augmented Generation (RAG):** Enhances diagnostic accuracy by incorporating knowledge retrieved from specialized Ayurvedic texts.
*   **Structured JSON Output:** Ensures consistent and machine-readable diagnostic reports through few-shot prompting and API configuration.
*   **Vector Database:** Uses `FAISS` and `SentenceTransformer` embeddings (`all-MiniLM-L6-v2`) for efficient semantic search over the Ayurvedic knowledge base.
*   **Interactive UI:** Built with `ipywidgets` for easy symptom input and results visualization within the notebook.
*   **Sample Cases:** Includes predefined examples for Vata, Pitta, and Kapha imbalances for testing and validation.
*   **Kaggle Integration:** Designed to run effectively within the Kaggle notebook environment, utilizing datasets and accelerators.

## Technology Stack

*   **Language:** Python 3
*   **LLM:** Google Gemini 2.0 Flash (via `google-generativeai` SDK)
*   **Core Libraries:**
    *   `langchain`, `langchain-community`, `langchain-huggingface`
    *   `sentence-transformers`
    *   `faiss-cpu`
    *   `numpy`, `pandas`
    *   `ipywidgets`
    *   `tqdm`
*   **Environment:** Kaggle Notebooks

## Dataset

This project uses the **Ayurveda Texts (English)** dataset available on Kaggle:
[https://www.kaggle.com/datasets/rcratos/ayurveda-texts-english](https://www.kaggle.com/datasets/rcratos/ayurveda-texts-english)

Please ensure this dataset is added as input to your Kaggle notebook environment via the "+ Add Data" / "+ Add Input" feature.

## Running the Notebook (on Kaggle)

1.  **Clone/Upload:** Clone this repository or upload the `.ipynb` notebook file to your Kaggle account.
2.  **Add Dataset:** Add the 'Ayurveda Texts (English)' dataset mentioned above as input to the notebook.
3.  **API Key:**
    *   Obtain a Google AI Studio API key for Gemini: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
    *   Add this key as a Kaggle Secret named `GOOGLE_API_KEY`. The notebook is configured to retrieve it using `UserSecretsClient`.
4.  **Accelerator:** For optimal performance (especially during the embedding generation in Step 4), select a GPU accelerator in the notebook settings (e.g., `T4 x2` is recommended and used in the notebook metadata).
5.  **Enable Internet:** Ensure internet access is enabled in the notebook settings to install packages and access the Google API.
6.  **Run Cells:** Execute the notebook cells sequentially from top to bottom.
    *   *Note:* Step 4 involves installing dependencies and building the vector index, which may take some time, especially on the first run (GPU acceleration helps significantly).
    *   *Note:* The code includes `os.environ["TOKENIZERS_PARALLELISM"] = "false"` to prevent common warnings during embedding generation. It also uses `.invoke()` instead of the deprecated `.get_relevant_documents()` for the retriever.
7.  **Interact:** Use the `ipywidgets` interface generated at the end of the notebook (Step 10) to enter symptoms or run sample cases.

## Disclaimer

This Ayurvedic Diagnostic Assistant is an educational demonstration of applying Generative AI techniques. It is **not a substitute for professional medical advice, diagnosis, or treatment.** Always seek the advice of a qualified Ayurvedic practitioner or other qualified health providers with any questions you may have regarding a medical condition. Never disregard professional medical advice or delay in seeking it because of something you have read or generated using this tool.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs, feature requests, or improvements.

## License

`This project is licensed under the MIT License - see the LICENSE.md file for details.`
