# 📄 Legal Document Analyzer and Summarizer

This project provides an end-to-end workflow for analyzing legal documents (PDF/DOCX) using Google Gemini via the `google-generativeai` SDK. The system extracts structured legal obligations and court decisions from complex legal texts, producing a machine-readable summary and actionable insights.

## 🧠 GenAI Capabilities Demonstrated

This project showcases the following GenAI capabilities:

- **Structured Output / Controlled Generation:** The Gemini model is prompted to return information in a strict JSON schema, ensuring reliable, machine-readable output for downstream processing.

- **Document Understanding:** The workflow parses and comprehends complex legal documents (PDF and DOCX), segmenting and analyzing them to extract obligations, deadlines, and court decisions.

- **Long Context Window:** Gemini's ability to process and reason over large chunks of legal text enables accurate extraction of information from lengthy court orders and filings.

## 🚀 Getting Started

### Prerequisites

-   Python 3.6+
-   A Google Gemini API key.  You'll need to set this up securely.
-   Kaggle account (if running on Kaggle)

### Installation

1.  Clone the repository:

    ```
    git clone git@github.com:RoystonDAlmeida/legal-document-analyzer-and-summarizer.git
    cd legal-document-analyzer-and-summarizer/
    ```

### Secure API Key Management

> **Note:** This project is designed to use secure API key management.
>
> -   **Never expose your API key** in code or output.
> -   **Do not** hardcode API keys in the notebook.
> -   If using Kaggle, use [Kaggle Secrets](https://www.kaggle.com/docs/secrets).
> -   Otherwise, use environment variables or a secure configuration file.

#### Setting up the Gemini API key (Kaggle):

1.  Go to [Kaggle Secrets](https://www.kaggle.com/docs/secrets).
2.  Add a new secret with the name `GEMINI_API_KEY` and paste your Gemini API key as the value.

### Usage

1.  **Prepare your legal document:**  Place your PDF or DOCX file in the appropriate input directory (or modify the `input_path` variable in the script).
2.  **Run the analysis script:**

    ```
    python your_script_name.py  # Replace with the actual script name
    ```

    or, if using the Jupyter Notebook:

    *   Open the `legal-document-analyzer-and-summarizer.ipynb` notebook.
    *   Run the notebook cells sequentially.

3.  **Review the results:** The analysis results will be saved as a JSON file (e.g., `legal_analysis.json`) in the output directory. The script also prints a preview of the extracted text and the analysis results to the console.

## ⚙️ Core Steps

1.  **Environment Setup and Gemini SDK Initialization:**  The script initializes the Gemini SDK using your API key.
2.  **Document Parsing Functions:** Helper functions extract text from PDF and DOCX files.
3.  **Preprocessing Pipeline:** Text cleaning and segmentation functions prepare the text for analysis.
4.  **Gemini-Powered Analysis:** The core analysis is performed using the Gemini model, extracting obligations, deadlines, and key clauses in JSON format.
5.  **Result Aggregation:** Results from all processed chunks are combined into a unified JSON structure.
6.  **Execution Workflow:**  The complete analysis pipeline is executed, parsing the document, analyzing it with Gemini, and saving the results.

## 🗂️ Input Format

The script accepts legal documents in PDF (.pdf) and DOCX (.docx) formats.

## 📊 Output Format

The analysis results are outputted as a JSON file, containing the following keys:

-   `summary`: A concise summary of the document.
-   `obligations`: A list of extracted legal obligations, with details such as the responsible party, action, deadline, and clause reference.
    ```
    [
      {
        "docket_number": "case identifier, if available",
        "party": "responsible entity",
        "action": "specific requirement",
        "deadline": "YYYY-MM-DD, if applicable",
        "clause_reference": "section identifier, if available",
        "details": "further details"
      }
    ]
    ```
-    `court_decisions`: A list of extracted court decisions.
    ```
    [
         {
           "docket_number": "case identifier",
           "case": "case identifier",
           "decision": "summary of the court's decision",
           "party": "party affected",
           "other_party": "opposing party (if any)",
           "reasoning": "the court's reasoning"
         }
    ]
    ```
-   `justice_opinions`:  A list of extracted justice opinions.
    ```
    [
        {
            "docket_number": "case identifier",
            "justice": "Name of the justice providing the opinion",
            "opinion_summary": "Detailed summary of the justice's opinion on the case",
            "reasoning": "Reasons for the opinion",
            "related_cases": "Any cases related to the opinion",
        }
    ]
    ```

-   `other_notes`: Any other noteworthy legal points or observations.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests with improvements or new features.
