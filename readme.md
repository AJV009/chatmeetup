# Quick Setup: Chatbot using Flowise and Ollama

This project demonstrates how to quickly set up a chatbot using no-code tools like Flowise and local LLM tools like OLLaMA. It leverages Docker and Docker Compose for easy deployment and management.

## Prerequisites

Before getting started, ensure that you have the following prerequisites installed on your system:

- Docker
- Docker Compose
- Good internet bandwidth (approx. 3GB of files to download)

## Getting Started

To set up the chatbot, follow these steps:

1. Clone this repository to your local machine.

2. Open a terminal and navigate to the project directory.

3. Copy the `.env.sample` file to `.env`:
```bash
cp .env.sample .env
```
You can modify the `.env` file to customize the configuration if needed.

4. Run the following command to start the services defined in the `docker-compose.yml` file:
```bash
docker compose up --build -d
```

5. Once the services are up and running, execute the following commands to pull the required models for OLLaMA:
```bash
docker exec -it ollama-embed ollama pull nomic-embed-text
docker exec -it ollama-generation ollama pull phi3:mini
```

6. To monitor the logs of the services, open separate terminals and run the following commands:
```bash
docker logs -f ollama-embed
docker logs -f ollama-generation
docker logs -f flowise
```

This will display the logs of the respective services in real-time.

## Configuration

The `docker-compose.yml` file contains the configuration for the services used in this project. You can customize the environment variables and ports as per your requirements.

The following services are defined in the `docker-compose.yml` file:

- `flowise`: The Flowise service for the no-code chatbot interface.
- `ollama-embed`: The OLLaMA service for embedding generation.
- `ollama-generation`: The OLLaMA service for text generation.

## Usage

Once the services are up and running, you can access the Flowise interface by opening a web browser and navigating to `http://localhost:${FLOWISE_PORT}`. The `FLOWISE_PORT` is determined by the value specified in the `docker-compose.yml` file.

You can now interact with the chatbot using the Flowise interface and leverage the power of OLLaMA for natural language processing tasks.

## Acknowledgments

- [Flowise](https://flowiseai.com/) - Open source low-code tool for developers to build customized LLM orchestration flow & AI agents
- [OLLaMA](https://ollama.com/) - Get up and running with large language models locally

## License

This project is licensed under the [MIT License](LICENSE).

---

Have fun exploring and building your chatbot with Flowise and OLLaMA!
