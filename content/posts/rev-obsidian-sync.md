---
title: rev-obsidian-sync
date: 2023-08-29T12:15:24+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1692528131001-5897bedce1b8?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTMyODI0NjV8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1692528131001-5897bedce1b8?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2OTMyODI0NjV8&ixlib=rb-4.0.3
---

# [acheong08/rev-obsidian-sync](https://github.com/acheong08/rev-obsidian-sync)

# Rev Obsidian Sync

Reverse engineered obsidian sync server (NOT OFFICIAL)

> [!WARNING]
> The main branch is the development branch. For stable usage, use the latest release.

> [!NOTE]
> If you have the time and energy, feel free to help out with PRs or suggestions.

## Features

- End to end encryption
- Live sync (across devices)
- File history/recovery/snapshots
- Works natively on IOS/Android/Linux/MacOS/Windows... (via the plugin)
- Vault sharing

### Experimental

These features are not in the latest release but in the main branch. They might not be fully tested and are probably unstable.

- Obsidian publish

## To do

- Fix bugs
- Publish


## Setup
- `git clone https://github.com/acheong08/obsidian-sync`
- `cd obsidian-sync`
- `export HOST=<YOUR DOMAIN NAME>` - Not necessary when running on localhost
- `go run cmd/obsidian-sync/main.go`
- Use nginx or cloudflare to proxy & handle TLS/SSL

~~**HTTPS _should_ be required. I use `certbot` or Cloudflare**. By default, the sync uses `wss` unless you're operating on `localhost` or `127.0.0.1` which breaks if you don't have TLS/SSL~~

HTTPS is not required.

When you're done, configure the [plugin](#sync-override-plugin)

<details>
<summary>
	
### Nginx configuration
</summary>

```nginx
map $http_upgrade $connection_upgrade {
        default upgrade;
        '' close;
}
server {
	listen 80 default_server;
	listen [::]:80 default_server;
	location / {
		proxy_http_version 1.1;
            	proxy_set_header Upgrade $http_upgrade;
            	proxy_set_header Connection $connection_upgrade;
           	proxy_set_header Host $host;
		proxy_pass http://127.0.0.1:3000/;
	}
	server_name _;
}
```

</details>

## Adding a new user

`go run cmd/signup/main.go`

## Sync override plugin

Tested on

- IOS
- Linux (Flatpak)

### Usage

> While we have no qualms with reverse engineering as a playground for experimentation, Obsidian Sync is a service we intend to keep first-party only for the foreseeable future. - https://github.com/obsidianmd/obsidian-releases/pull/2353

This plugin will not be part of the official community plugins list.

- Install https://github.com/acheong08/rev-obsidian-sync-plugin
- Go to settings
- Set API endpoint
	- e.g. `https://obsidian.yourdomain.com`
 	- For development: `http://127.0.0.1:3000` 

Known bugs:

- ~~Cannot restart plugin (for whatever reason you might want to do that...) - Restart the app if you want to reload this particular plugin~~

Report all bugs in this repository.
