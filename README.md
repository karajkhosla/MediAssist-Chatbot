# MediAssist-Chatbot Project

## Project Overview

This project is a medical chatbot designed to provide users with information and assistance related to health and medicine.  It leverages the power of Generative AI, specifically OpenAI's Large Language Models (LLMs), to understand user queries and provide relevant, accurate, and helpful responses. The chatbot is built using LangChain, a framework for developing applications powered by language models, and its knowledge base is stored in a Pinecone vector database for efficient retrieval.  A user-friendly web interface is created with Flask.

## Features

* **Medical Information Retrieval:** Provides answers to user questions about diseases, treatments, symptoms, and medications.
* **AI-Powered Responses:** Uses OpenAI's LLMs to generate natural and informative responses.
* **Customizable Knowledge Base:** The chatbot's knowledge is derived from a custom medical dataset, "The Gale Encyclopedia of Medicine".
* **Efficient Knowledge Storage and Retrieval:** Employs Pinecone for fast and scalable storage and retrieval of medical information.
* **User-Friendly Interface:** A web application built with Flask provides an intuitive way to interact with the chatbot.
* **Scalable Architecture:** Designed to be deployed on cloud platforms like AWS.

## Technology Stack

* **Large Language Model (LLM):** OpenAI
* **GenAI Framework:** LangChain
* **Vector Database:** Pinecone
* **Web Framework:** Flask (Python)
* **Version Control:** Git
* **Cloud Deployment (Planned):** AWS

## System Architecture

1.  **Data Ingestion:**
    * Medical information is extracted from "The Gale Encyclopedia of Medicine".
    * The extracted data is processed and split into smaller, manageable chunks.

2.  **Embedding Generation:**
    * An embedding model (e.g., OpenAI Embeddings) converts the text chunks into vector embeddings.  These embeddings capture the semantic meaning of the text.

3.  **Knowledge Base Storage:**
    * The vector embeddings are stored in a Pinecone vector database.  This database acts as the chatbot's knowledge base, allowing for efficient similarity search.

4.  **User Interaction:**
    * Users interact with the chatbot through a web interface built with Flask.
    * User queries are sent to the backend.

5.  **Query Processing:**
    * The user's query is converted into a vector embedding using the same embedding model.
    * The Pinecone database is queried to find the most similar embeddings in the knowledge base.  This identifies the most relevant medical information.

6.  **Response Generation:**
    * The relevant information retrieved from Pinecone, along with the original user query, is sent to the OpenAI LLM.
    * The LLM generates a natural language response that answers the user's question, drawing upon the retrieved medical knowledge.

7.  **Response Delivery:**
    * The LLM's response is sent back to the Flask web application and displayed to the user.

## Installation and Setup

### Prerequisites

* Python 3.6 or higher
* pip (Python package installer)
* Git
* OpenAI API key
* Pinecone API key
* AWS Account (if deploying to AWS)

### Steps

1.  **Clone the Repository:**
    ```bash
    git clone <repository_url>
    cd medical-chatbot
    ```

2.  **Create a Virtual Environment (Recommended):**
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Linux/macOS
    venv\Scripts\activate  # On Windows
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: A `requirements.txt` file should be included in the repository.  If not, you'll need to install the following packages individually:  `openai`, `langchain`, `pinecone-client`, `Flask`,  and any other dependencies as needed.)*

4.  **Set up Environment Variables:**
    * Create a `.env` file in the project root.
    * Add your API keys:
        ```
        OPENAI_API_KEY=<your_openai_api_key>
        PINECONE_API_KEY=<your_pinecone_api_key>
        PINECONE_ENVIRONMENT=<your_pinecone_environment>  # e.g., us-east1-aws
        ```

5.  **Set up Pinecone Index:**
     * Create an index in your Pinecone account.  You'll need to specify the index name in your code (e.g., "medical-knowledge-index").  The dimensions of the index should match the output dimension of the embedding model you are using (e.g., 1536 for `text-embedding-ada-002`).

6.  **Populate the Knowledge Base:**
    * Run the script to process the medical data and upload the embeddings to Pinecone.  (The specific script name may vary, e.g., `store_index.py`).
    ```bash
    python store_index.py
    ```

7.  **Run the Flask Application:**
    ```bash
    python app.py
    ```
    * The application will typically be accessible at `http://127.0.0.1:5000/`.

## Usage

1.  Open the web application in your browser.
2.  Enter your medical question or query in the input field.
3.  Click the "Send" button.
4.  The chatbot will display the response, providing relevant medical information.

## Code Structure

*(The actual code structure may vary, but here's a general outline)*

* `app.py`:  Flask application code, handles user input and displays responses.
* `store_index.py` (or similar): Script to process the medical data and upload it to Pinecone.
* `helper.py` (or similar):  Helper functions for data processing, embedding generation, and interacting with Pinecone/OpenAI.
* `templates/`:  Directory containing HTML templates for the Flask application.
* `data/`: Directory containing the medical data source (e.g., the "Gale Encyclopedia of Medicine" data).
* `requirements.txt`:  List of Python dependencies.
* `.env`: File to store environment variables (API keys).

## Planned Enhancements

* **Improved Accuracy:** Fine-tuning the LLM and refining the knowledge base.
* **More Data Sources:** Expanding the knowledge base with additional medical texts and databases.
* **Multi-modal Input:** Allowing users to input images or other media.
* **User Authentication:** Adding user accounts and personalized interactions.
* **Deployment to AWS:** Deploying the application to AWS for scalability and reliability.
* **Continuous Integration/Continuous Deployment (CI/CD):** Automating the deployment process.

## Contributions

Contributions are welcome!  If you find a bug, have a suggestion, or would like to contribute code, please submit an issue or pull request.

## License

[Specify the license for your project, e.g., MIT License]
