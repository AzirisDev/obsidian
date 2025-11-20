At first we need to install docker and docker-compose.
Run `docker-compose up --build` in module directory where docker files are located.
#### Model
We have yaml file:
```
name: phi-3.5-mini-instruct
parameters:
	model: bartowski/phi-3.5-mini-instruct.gguf
	type: phi-3.5-mini-instruct
	format: gguf
backend: llama-cpp
context_size: 8192
gpu_layers: 0
threads: 4 # Adjust based on your CPU cores. Assume 1 thread per core
batch_size: 64 # You might want to experiment with values 32, 64 or 128
f16: true
download_files:
	- filename: bartowski/phi-3.5-mini-instruct.gguf
	uri: https://huggingface.co/bartowski/Phi-3.5-mini-instruct-GGUF/resolve/main/Phi-3.5-mini-instruct-Q6_K.gguf
```

This is light version of LLM that can be run just using CPU. 

#### Module 1 - retrieving simple answer with generator

**DockerFile** - this we need to make our python app image
```
FROM python:3.12-slim  // Base python image

WORKDIR /app           // open image's directory

COPY requirements.txt .         // creates local copy inside my container
RUN pip install -r requirements.txt // -r go through file and download everything

COPY client.py .           // creates local copy inside my container

CMD ["python", "client.py"]     // run python file
```

Here we have Docker-Compose yaml file - we need this to orchestrate the containers AKA services:
```
services:
	localai:
		image: localai/localai:v2.25.0-ffmpeg-core
		ports:
			- 8080:8080
		environment:
			- LOG_LEVEL=INFO
			- MODELS_PATH=/models
		volumes:
			- ../models:/models:cached
		healthcheck:
			test: ["CMD", "curl", "-f", "http://localhost:8080/v1/models"]
			interval: 600s
			timeout: 5s
			retries: 5
			# Allows for initial model downloads
			# In a production environment, you likely want to pre-cache the AI model
			start_period: 100000s
			start_interval: 5s
	
	client:
		build:
			context: .
			dockerfile: Dockerfile
		environment:
			- LLM_API_BASE=http://localai:8080/v1
		depends_on:
			localai:
				condition: service_healthy
		restart: "no"
```
Then we have `client.py` file to run ai retrieving python app.

#### Module 2 - Embeddings and AI search
Embeddings is a numeric representation of data: turn the word/token `apple` into something like `[0.32, 0.57, 0.67]`. Token is unit of abstract data gathered from human data, usually it is 3/4 of a word.

We created API server which get texts and makes out of it embeddings. It is small python application. Also, we use `qdrant` service. `Qdrant` open-source vector storage and search tool.

For `client` server we will have main logic of the module. We have predefined concepts with descriptions. That data we will turn into embeddings and store into `qdrant`. After that perform test search.

Links:

202511112226

