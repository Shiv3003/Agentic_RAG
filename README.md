## Agentic RAG APP with FastAPI, Ollama and Vue.js UI 


The fantastic LangGraph's Agentic RAG  moves beyond simple retrieval to intelligent, goal-oriented problem-solving, making it powerful for complex, real-world applications. Agentic RAG improves answer quality and reliability by planning multi-step reasoning, issuing adaptive retrievals, using tools (search, code, SQL) for grounding, and running self-critique loops to verify claims and reduce hallucinations. 


Following the LangGraph official [documentation](https://docs.langchain.com/oss/python/langgraph/agentic-rag), I created a production oriented agentic LangGraph RAG APP using FastAPI,  Qdrant vector database and Ollama Docker containers, with a  Vue.js UI — all bundled in a single‑click docker-compose.yml.


## Features

- **API key–free**: No API keys required at any level.
- **Real-time documents**: Methods for real-time adding and deleting documents into Qdrant vector store.
- **Easy to run**: All you need is Docker installed on your system.
- **Customize**: Choose your LLM and embedding models; run on CPU or GPU.
- **Easy to modify and scale**: A simple platform that demonstrates how to build production-oriented systems with LangGraph and the Ollama library
- **Embedded frontend**: No frontend service in docker-compose; a simple and fun Vue.js SPA  embedded in FastAPI in just one line of code.



## The single-click launcher 

Download this repo into your local PC. First, un/comment the deployment type based on your device : CPU or GPU [docker-compose.yml](docker-compose.yml)

```sh
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: 1
              capabilities: [gpu]
    # deploy:
    #   resources:
    #     limits:
    #       cpus: '12.00'
    #       memory: 12G  

```

then save and run :


```sh
docker compose up --build
```

This command builds, pulls containers, including Ollama's ``qwen2.5:1.5b``, and launches all the services. See the logs until this line appears :
```sh
llm_service  | INFO:     Application startup complete.
llm_service  | INFO:     Uvicorn running on http://0.0.0.0:8001 (Press CTRL+C to quit)
```
then open this URL in your browser:

```sh
http://localhost:80
```

Now the UI would be visible.

The Qdrant database would be empty at this moment and needs to be populated, by pasting the URL into the ``URL Input: Add data into Qdrant`` box and click ``Submit URLs`` : 
