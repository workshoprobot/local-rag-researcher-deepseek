# 🚀 **Local RAG Researcher with DeepSeek R1 & Langgraph**

### 👉 **[Check Out This Guide: Build Your Own Local RAG Researcher with DeepSeek R1!](https://dev.to/kaymen99/build-your-own-local-rag-researcher-with-deepseek-r1-11m) 🚀**

<div align="center">
  <img src="https://github.com/user-attachments/assets/5dc34341-3a2f-461c-b66d-46b134fe5bd9" alt="Demo of Local RAG Researcher with LangGraph & DeepSeek">
</div>

I built a **local adaptive RAG research agent** on top of **LangGraph**, using the **DeepSeek R1 model** running locally with **Ollama**. The researcher agent takes user instructions, generates relevant research queries, and retrieves necessary documents from a local **Chroma database**. Each document is evaluated for **relevance** against the original query. If the retrieved documents are insufficient or irrelevant, the researcher can optionally **search the web** for additional sources. Each query's findings are summarized and sent to a **final writer agent**, which crafts a **comprehensive report** based on a predefined user reporting format.  

# System Flowchart
This is the detailed flow of the system:

1. **Generate Research Queries**: Produces queries based on user instructions.  
2. **Search Queries**: Processes queries in paralle batches (for speed), for each query the `search_and_summarize` subgraph is invoked.  
3. **Search and Summarize Query (Subgraph)**:  
   - Retrieve RAG Documents from ChromaDB.
   - Evaluate Retrieved Documents relevance  
   - Route Research (to summarization or web research)  
   - Perform Web Research (if needed)  
   - Summarize Query Research  
4. **Generate Final Answer**: Combines all summaries into a final report.  

<div align="center">
  <img src="https://github.com/user-attachments/assets/5e06e948-c853-47d1-b25e-e3c5ca96b60d" alt="Langgraph Local Deepseek RAG researcher">
</div>

# Tech Stack
- **[Ollama](https://ollama.com/)**: Runs the DeepSeek R1 model locally.
- **[LangGraph](https://www.langchain.com/langgraph)**: Builds AI agents and defines the researcher's workflow.
- **[ChromaDB](https://docs.trychroma.com/)**: Local vector database for RAG-based retrieval.
- **[Streamlit](https://docs.streamlit.io/)**: Provides a UI for interacting with the researcher.
- **[Tavily](https://tavily.com/)**: For searching the web.

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

Follow the official instructions to [install Ollama](https://ollama.com/download), then pull the DeepSeek R1 model (this project uses the 7b model but you can choose any other [models available](https://ollama.com/library/deepseek-r1)):

```bash
ollama pull deepseek-r1:7b
```

### Step 2: Launch the Streamlit App

Run the following command to start the UI:

```bash
streamlit run app.py
```

### Step 3: Visualize in LangGraph Studio (Optional)

Since the researcher is built with LangGraph, you can use **LangGraph Studio** to inspect the agent's workflow. To do this, run the following commands:  

```bash
pip install -U "langgraph-cli[inmem]"
langgraph dev
```

# Customization
### Modify Report Structures
- Add custom structures inside the `report_structures` folder.
- Select the preferred structure in the UI.

### Using an External LLM Provider  

By default, the researcher runs locally using the **DeepSeek R1 model** on **Ollama**. However, if you prefer to use a cloud-based LLM provider instead (such as **Cloud DeepSeek R1**, **OpenAI GPT-4o**, or **OpenAI o1**), follow these steps:  

1. **Modify the Code**:  
   - Go to `assistant/graph.py`.  
   - Comment the code invoking Ollama model.  
   - Uncomment the section of code that enables external LLM calls.  
   - `invoke_llm` uses **[OpenRouter](https://openrouter.ai)**, which provides access to multiple LLMs. You can choose your preferred model from their [list](https://openrouter.ai/models). 🚀  
   - You can also modify the `invoke_llm` function to use a single LLM provider instead of **OpenRouter** if you want.  

2. **Set Up API Keys**:  
   - Obtain OpenRouter API key from [here](https://openrouter.ai/settings/keys).  
   - Add these keys to your `.env` file in the following format:  

     ```env
     OPENROUTER_API_KEY=your_openai_key
     ```

# **📚 Further Reading & Resources**

* Langchain: Building a fully local "deep researcher" with DeepSeek-R1[see](https://www.youtube.com/watch?v=sGUjmyfof4Q) 

* Langchain: Building a fully local research assistant from scratch with Ollama [see](https://www.youtube.com/watch?v=XGuTzHoqlj8) 

* LangGraph Template: Multi-Agent RAG Research [see](https://www.youtube.com/watch?v=JLDLANs_m_w) 

* LangGraph Adaptative RAG implementation [see](https://github.com/langchain-ai/langgraph/blob/main/examples/rag/langgraph_adaptive_rag_local.ipynb)

# Contributing
Contributions are welcome! Please open an issue or submit a pull request for any changes.

# Contact
If you have any questions or suggestions, feel free to contact me at aymenMir1001@gmail.com.