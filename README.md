I've been using [Ollama](https://ollama.com) for a while now as a backend LLM for coding with [VS Code](https://code.visualstudio.com) and the [Continue](https://www.continue.dev) extension. I've run it via the install process provided for [Linux](https://ollama.com/download/linux) and the [MacOS](https://ollama.com/download/mac) application.

I wanted to expose a user interface for non-coding use and found [Open WebUI](https://docs.openwebui.com). Since Open WebUI is distributed via Docker, I wanted to streamline the Ollama install to be via Docker as well.

I'm running this on a [Debian 12](https://www.debian.org/releases/bookworm/) server with a Nvidia 3090. You will need a similar linux server with a Nvidia GPU and Cuda installed and configured properly.

Install Docker<br/>
https://docs.docker.com/engine/install/

Allow non-root users to manage Docker<br/>
https://docs.docker.com/engine/install/linux-postinstall/

Install the Nvidia Container Runtime<br/>
https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

I'm running this on a server where I've created an `ollama` user that's a part of the `docker` group. I then created a path at `/opt/ollama` where I keep the `docker-compose.yml` file and store files from the Docker volumes.

For a less permenant setup, simply cloning this repository will work as well.

Change into the directory containing the `docker-compose.yml` file and run.
```
docker compose up -d
```

Open WebUI will now be running on port 8080 of the host.

While it's possible to pull models from the WebUI, I prefer doing so via the terminal. It provides better visibility into the download.
```
docker compose exec -it ollama ollama pull <model>
```
