

# Automated Document Processing and Markdown Generation

A comprehensive solution for extracting, processing, and standardizing data from documents(PDF files) and web sources using both open-source and enterprise tools. The application leverages FastAPI for backend processing and Streamlit for an intuitive user interface, deployed on Google Cloud Run.

## Workflow Diagram

Below is the workflow diagram for the AI Application:

![AI Application Workflow](https://github.com/khavnekar-y/AI-Information-Extractor/blob/main/ai_application_workflow%20(2).png)

### Diagram Description:
1. **User**: The end-user interacts with the application via the Streamlit frontend.
2. **Streamlit App**: The frontend built using Streamlit.
3. **FastAPI Backend**: The backend server that handles data processing.
4. **Data Extraction**:
   - **PyMuPDF / camelot**: For extracting data from PDF files using Open Source tools.
   - **Azure Document Intelligence and Adobe API Extract API**: For extracting data from PDF files using Enterprise tools.
   - **BeautifulSoup**: For web scraping using Open Source Tools.
   - **APIFY**: For web scraping using Enterprise Tools.
5. **Standardization Tools**:
   - **Docling**: A custom tool for standardizing conversions from pdfs to markdowns.
   - **MarkItDown**: Another custom tool for further data standardization.
6. **AWS S3 Bucket**: Used for storing processed data.
7. **Google Cloud Run**: Used for Deploying FastAPI applications
8. **Streamlit In-builtDeployment**: Used for Deploying Streamlit application for UI/UX. 

## Components

1. **User**: The end-user interacts with the application via the Streamlit frontend.
2. **Streamlit Frontend**: A custom frontend built using Streamlit for user interaction.
3. **FastAPI Backend**: A backend server built using FastAPI to handle data processing and communication with other services.
4. **Data Extraction**:
   - **PyPDF2 / pdfplumber**: For extracting data from PDF files.
   - **BeautifulSoup/Scrapy**: For web scraping.
   - **Microsoft Document Intelligence**: For enterprise-level document processing.
5. **Standardization Tools**:
   - **Docling**: A custom tool for standardizing extracted data.
   - **MarkItDown**: Another custom tool for further data standardization.
6. **AWS S3 Bucket**: Used for storing processed data.

---
## Project Structure
```bash
├── .devcontainer/ # Development container configuration
├── .streamlit/ # Streamlit configuration files
├── api/ # FastAPI backend services
├── frontend/ # Streamlit frontend application
├── notebooks/ # Development and testing notebooks
├── .dockerignore # Docker ignore rules
├── .gitignore # Git ignore rules
├── Azure_Document_Intelligence.py # Azure AI document processing for  enterprise pdf extraction
├── Cloud_Run.md # Cloud deployment instructions
├── Dockerfile # Main application Dockerfile
├── EnterpriseWebScrap.py # Enterprise web scraping module
├── OSWebScrap.py # Open-source web scraping module
├── README.md # Project documentation
├── ai_application_workflow.png # Architecture diagram
├── docker-compose.yml # Multi-container Docker setup
├── docklingextraction.py # Markdown Generator for pdf
├── open_source_parsing.py # pymupdf and camelot for open source pdf extraction
└── requirements.txt # Python dependencies
```

## Workflow Steps

1. The **User** uploads data via the **Streamlit Frontend**.
2. The **Frontend** sends the data to the **FastAPI Backend**.
3. The **Backend** processes the data using one or more of the following:
   - **PyPDF2 / pdfplumber** for PDF extraction.
   - **BeautifulSoup / Scrapy** for web scraping.
   - **Microsoft Document Intelligence** for enterprise document processing.
   - **Apify** for enterprise web processing of documents.
4. The extracted data is standardized using **Docling** and **MarkItDown**.
5. The processed data is stored in an **AWS S3 Bucket**.
6. The **Frontend** retrieves the processed data from the **S3 Bucket** and displays it to the **User**.

---

## Prerequisites

- Python 3.7+
- [Diagrams](https://diagrams.mingrammer.com/) library for generating the workflow diagram.
- AWS account with S3 bucket access.
- Streamlit and FastAPI installed for frontend and backend development.
- Install [Google Cloud SDK](https://cloud.google.com/sdk/docs/install)
- Install [Docker](https://docs.docker.com/get-docker/) 

---
## Installation

Clone the repository:

   ```bash
   git clone https://github.com/your-username/BigData_InClass_Proj1.git
   cd BIGDATA_INCLASS_PROJ1
   ```
   Create a .env file and add the required credentials:

   ```bash
   AWS_ACCESS_KEY_ID=your_aws_access_key
   AWS_SECRET_ACCESS_KEY=your_aws_secret_key
   AWS_REGION=your_aws_region
   AZURE_DOCUMENT_INTELLIGENCE_KEY=your_azure_key
   AZURE_FORM_RECOGNIZER_KEY=your_azure_form_intelligence
   APIFY_TOKEN=your_apify_token
   ADOBE_API_ID=your_adobe_api_key
   ADOBE_API_Secret= adobe_api_secret 
   ```
   
   Build and run the application using Docker Compose:
   ```bash
   docker-compose build --no-cache
   docker-compose up -d
   ```
   
   
3. Ensure you have the custom icons (`microsoft.png`, `docling.png`, `markitdown.png`, `streamlit.png`) in the `./icons/` directory.

4. Generate the workflow diagram:
   ```bash
   python generate_diagram.py
   ```

---

## Usage

1. Run the FastAPI backend:
   ```bash
   cd api
   python -m venv venv
   pip install -r requirements.txt
   venv/Scripts/activate
   uvicorn backend:app --reload
   ```
2.Open your browser and navigate to `http://localhost:8080` to interact with the application for Backend.

3. Run the Streamlit frontend:
   ```bash
   cd frontend
   python -m venv venv
   pip install -r requirements.txt
   venv/Scripts/activate
   streamlit run frontend.py
   ```
4.Open your browser and navigate to `http://localhost:8501` to interact with the application for Streamlit app.Run the streamlit after running the fastapi localhost 


---
**Deployed Application:**
- FastAPI Backend: https://fastapi-streamlit-974490277552.us-central1.run.app/
- Streamlit Frontend: https://streamlit-app-974490277552.us-central1.run.app/

More details on the cloud deployment process will be explained in the CloudRun.md in the root folder


## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

### Notes:
- Replace `yourusername` in the repository URL with your actual GitHub username.
- Ensure the `generate_diagram.py` script is created to generate the workflow diagram.
- Update the `LICENSE` file if you choose a different license.

Let me know if you need further assistance!
