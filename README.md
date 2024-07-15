I've been using [Ollama](https://ollama.com) to run LLMs for development with Visual Studio Code and the [Continue](https://www.continue.dev) extension and for some experiments with [LangChain](https://github.com/langchain-ai/langchain).

I've had success installing Ollama using both the [MacOS](https://ollama.com/download/mac) application as well as the [Linux](https://ollama.com/download/linux) installer.

I wanted to expose a user interface for some non-coding usecases and found [Open WebUI](https://docs.openwebui.com).

I'm running this on a [Debian 12](https://www.debian.org/releases/bookworm/) server with a Nvidia 3090 with 24GB of RAM. You will need a similar linux server with a Nvidia GPU and Cuda installed and configured properly.

Install Docker<br/>
https://docs.docker.com/engine/install/

Allow non-root users to manage Docker<br/>
https://docs.docker.com/engine/install/linux-postinstall/

Install the Nvidia Container Runtime<br/>
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

For a more robust installation, I'm storing the `docker-compose.yml` file as well as the Docker volume bindings in `/opt/ollama`. This gives me a more organized filesystem layout for everything. For a less permenant setup, simply cloning this repository and running for any path is fine.

Change into the directory containing the `docker-compose.yml` file and run.
```
docker compose up -d
```

Open WebUI will now be running on port 8080 of the host.

While it's possible to pull models from the WebUI, I prefer doing so via the terminal.
```
docker compose exec -it ollama ollama pull <model>
```
