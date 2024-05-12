---
title: glance
date: 2024-05-12T12:18:53+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1713007272846-14202cbba86c?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTU0ODczOTl8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1713007272846-14202cbba86c?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTU0ODczOTl8&ixlib=rb-4.0.3
---

# [glanceapp/glance](https://github.com/glanceapp/glance)

<p align="center"><em>What if you could see everything at a...</em></p>
<h1 align="center">Glance</h1>
<p align="center"><a href="#installation">Install</a> • <a href="docs/configuration.md">Configuration</a> • <a href="docs/themes.md">Themes</a></p>

![example homepage](docs/images/readme-main-image.png)

### Features
#### Various widgets
* RSS feeds
* Subreddit posts
* Weather
* Bookmarks
* Latest YouTube videos from specific channels
* Calendar
* Stocks
* iframe
* Twitch channels & top games
* GitHub releases
* Site monitor

#### Themeable
![multiple color schemes example](docs/images/themes-example.png)

#### Optimized for mobile devices
![mobile device previews](docs/images/mobile-preview.png)

#### Fast and lightweight
* Minimal JS, no bloated frameworks
* Very few dependencies
* Single, easily distributed <15mb binary and just as small docker container
* All requests are parallelized, uncached pages usually load within ~1s (depending on internet speed and number of widgets)

### Configuration
Checkout the [configuration docs](docs/configuration.md) to learn more. A [preconfigured page](docs/configuration.md#preconfigured-page) is also available to get you started quickly.

### Installation
> [!CAUTION]
>
> The project is under active development, expect things to break every once in a while.

#### Manual
Checkout the [releases page](https://github.com/glanceapp/glance/releases) for available binaries. You can place the binary inside `/opt/glance/` and have it start with your server via a [systemd service](https://linuxhandbook.com/create-systemd-services/). To specify a different path for the config file use the `--config` option:

```
/opt/glance/glance --config /etc/glance.yml
```

#### Docker
> [!IMPORTANT]
>
> Make sure you have a valid `glance.yml` file before running the container.

```console
docker run -d -p 8080:8080 \
  -v ./glance.yml:/app/glance.yml \
  -v /etc/timezone:/etc/timezone:ro \
  -v /etc/localtime:/etc/localtime:ro \
  glanceapp/glance
```

Or if you prefer docker compose:

```yaml
services:
  glance:
    image: glanceapp/glance
    volumes:
      - ./glance.yml:/app/glance.yml
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 8080:8080
    restart: unless-stopped
```

### Building from source

Requirements: [Go](https://go.dev/dl/) >= v1.22

To build:

```
go build .
```

To run:

```
go run .
```
