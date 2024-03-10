[![Check for new OpenRA release and build docker image](https://github.com/dkruyt/openra/actions/workflows/main.yml/badge.svg)](https://github.com/dkruyt/openra/actions/workflows/main.yml) [![1] ![2]](https://github.com/dkruyt/openra/pkgs/container/openra)

https://ghcr-badge.egpl.dev/dkruyt/openra/size

https://ghcr-badge.egpl.dev/dkruyt/openra/latest_tag?trim=major&label=latest


# 🎮 OpenRA Dedicated Server Docker Image

This repository contains the Dockerfile and associated resources needed to build a Docker image for OpenRA, a real-time strategy game engine.

The Dockerfile builds from mono, is optimized for multi-architecture builds, and includes all tools and libraries necessary to run an OpenRA Dedicated Server instance.

## 🔄 GitHub Actions

We use GitHub Actions as our CI/CD system to automatically build and push the Docker images when a new version of OpenRA is released.

A scheduled workflow checks the OpenRA GitHub repository every day at midnight for new releases. If a new release is detected, it triggers a build and push workflow to create a new Docker image for that OpenRA version and push it to GitHub Container Registry (GHCR).

You can also manually trigger the workflow to build a Docker image for a specific OpenRA version by using the workflow dispatch event.

## 🏃 Running the Docker image

To start the OpenRA server, you can use Docker or Docker Compose.

__Docker:__

```sh
docker run -d -p 1234:1234 -v ./openra_data:/home/openra/.openra ghcr.io/dkruyt/openra:latest
```

Replace `tag` with the version you want to use.

__Docker Compose:__

Modify the Docker Compose file (docker-compose.yml) to suit your needs and start the service:

```sh
docker-compose up -d
```

It will start an OpenRA server with the environment variables specified in the Docker Compose file.

## ⚙️ Configuration

You can modify server settings such as the server name, mod, listen port, external port, etc., directly in the Docker Compose file under the `environment` section.

Refer the Docker Compose file and OpenRA documentation for more details on what each environment variable does.

## 👥 Contributing

Feel free to fork this project, submit PRs or issues, or ask any question about the project.

[1]: <https://ghcr-badge.egpl.dev/dkruyt/openra/latest_tag?trim=major&label=latest>
[2]: <https://ghcr-badge.egpl.dev/dkruyt/openra/size>
