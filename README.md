[![Check for new OpenRA release and build docker image](https://github.com/dkruyt/openra/actions/workflows/main.yml/badge.svg)](https://github.com/dkruyt/openra/actions/workflows/main.yml) [![1] ![2]](https://github.com/dkruyt/openra/pkgs/container/openra)

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

## ⚙️ Configuration

You can modify server settings such as the server name, mod, listen port, external port, etc., directly in the Docker Compose file under the `environment` section.

The `environment` section in `docker-compose.yml` allows you to declare environment variables, which are available to your code inside the Docker container. Here is what each of them represents:

- `Name`: This will set the `Name` that the dedicated server reports.
- `Mod`: This is to choose the game modification for your OpenRA dedicated server, the default is `ra` which stands for Red Alert.
- `Map`: Identifier of the map to be hosted by the dedicated server. If blank, a random map will be selected.
- `ListenPort`: It's the port that the server listens on for client connections.
- `AdvertiseOnline`: Defines whether the server should be advertised online. If set to `True`, it will be visible on the public server list.
- `Password`: A password for the server. If set, players would need this password to join the server.
- `RecordReplays`: If set to `True`, the server will record game replays.
- `RequireAuthentication`: Defines if the server will require authentication.
- `ProfileIDBlacklist`: List of blacklisted profile IDs that are not allowed to connect to the server.
- `ProfileIDWhitelist`: List of whitelisted profile IDs that are allowed to connect to the server.
- `EnableSingleplayer`: If set to `False`, single-player mode is disabled on the server.
- `EnableSyncReports`: If set to `True`, synchronisation reports (sync reports) will be enabled.
- `EnableGeoIP`: If set to `True`, Geo IP lookups are enabled.
- `EnableLintChecks`: If set to `True`, lint checks are enabled.
- `ShareAnonymizedIPs`: If set to `True`, shares anonymized IPs publicly.
- `FloodLimitJoinCooldown`: This sets up an anti-flooding mechanism where if a client disconnects, it's allowed to rejoin after a time period specified in milliseconds.
- `SupportDir`: Defines a custom directory for support files. If blank, a default directory is used.

All these variables are optional. If you do not provide a value for an environment variable, the Docker image will use its default value. Please refer to OpenRA documentation for specific details on these variables.

## 👥 Contributing

Feel free to fork this project, submit PRs or issues, or ask any question about the project.

[1]: <https://ghcr-badge.egpl.dev/dkruyt/openra/latest_tag?trim=major&label=latest>
[2]: <https://ghcr-badge.egpl.dev/dkruyt/openra/size>
