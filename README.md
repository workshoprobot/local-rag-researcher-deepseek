# 🚀 **Local RAG Researcher with DeepSeek R1 & Langgraph**

### 👉 **[Check Out This Guide: Build Your Own Local RAG Researcher with DeepSeek R1!](https://dev.to/kaymen99/build-your-own-local-rag-researcher-with-deepseek-r1-11m) 🚀**

![rag-researcher-deepseek](https://github.com/user-attachments/assets/5dc34341-3a2f-461c-b66d-46b134fe5bd9)

# System Flowchart
This is the detailed flow of the system:

1. **Generate Research Queries**: Produces queries based on user instructions.  
2. **Search Queries**: Processes queries in batches and invokes the subgraph for each query.  
3. **Search and Summarize Query Subgraph**:  
   - Retrieve RAG Documents  
   - Evaluate Retrieved Documents relevance  
   - Route Research (to summarization or web research)  
   - Perform Web Research (if needed)  
   - Summarize Query Research  
4. **Generate Final Answer**: Combines all summaries into a final report.  

![Langgraph Local Deepseek RAG researcher](https://github.com/user-attachments/assets/5e06e948-c853-47d1-b25e-e3c5ca96b60d)

# Tech Stack
- **Ollama**: Runs the DeepSeek R1 model locally.
- **LangGraph**: Builds AI agents and defines the researcher's workflow.
- **ChromaDB**: Local vector database for RAG-based retrieval.
- **Streamlit**: Provides a UI for interacting with the researcher.

# How to Run
## Prerequisites
Ensure you have the following installed:
- Python 3.9+
- Ollama
- Tavily API key for web searchs
- Necessary Python libraries (listed in `requirements.txt`)

## Setup
### Clone the Repository
```bash
git clone https://github.com/kaymen99/local-rag-researcher-deepseek
cd local-rag-researcher-deepseek
```

### Create and Activate a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### Install Required Packages
```bash
pip install -r requirements.txt
```

### Set Up Environment Variables
Create a `.env` file in the root directory and add necessary credentials:

```ini
# Tavily API key for SearchTool (optional)
TAVILY_API_KEY="your-api-key"
```

# Running the Application
### Step 1: Install and Run Ollama
Follow the official instructions to install Ollama, then pull the DeepSeek R1 model (this project uses the 7b model but you can choose any other model available):
```bash
ollama pull deepseek-r1:7b
```

### Step 2: Launch the Streamlit App

Run the following command to start the UI:
```bash
streamlit run app.py
```

### Step 3: Visualize in LangGraph Studio (Optional)
To inspect the agent's workflow:
```bash
pip install -U "langgraph-cli[inmem]"
langgraph dev
```

# Customization
### Modify Report Structures
- Add custom structures inside the `report_structures` folder.
- Select the preferred structure in the UI.

### Swap LLM Providers
To use an external LLM provider:
1. Uncomment the relevant code in `assistant/graph.py`.
2. Add the necessary API keys to your `.env` file.

# Contributing
Contributions are welcome! Please open an issue or submit a pull request for any changes.

# Contact
If you have any questions or suggestions, feel free to contact me at aymenMir1001@gmail.com.