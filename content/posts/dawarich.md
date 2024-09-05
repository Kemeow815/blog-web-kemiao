---
title: dawarich
date: 2024-09-05T12:20:43+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1721297013317-e4976cc284d9?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MjU1MDk5MTJ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1721297013317-e4976cc284d9?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MjU1MDk5MTJ8&ixlib=rb-4.0.3
---

# [Freika/dawarich](https://github.com/Freika/dawarich)

# Dawarich


[![Discord](https://dcbadge.limes.pink/api/server/pHsBjpt5J8)](https://discord.gg/pHsBjpt5J8) | [![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/H2H3IDYDD) | [![Patreon](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Dfreika%26type%3Dpatrons&style=for-the-badge)](https://www.patreon.com/freika) | [0x6bAd13667692632f1bF926cA9B421bEe7EaEB8D4](https://etherscan.io/address/0x6bAd13667692632f1bF926cA9B421bEe7EaEB8D4)

[![CircleCI](https://circleci.com/gh/Freika/dawarich.svg?style=svg)](https://app.circleci.com/pipelines/github/Freika/dawarich)

## Screenshots

![Map](screenshots/map.jpeg)

![Stats](screenshots/stats.jpeg)

![Import](screenshots/imports.jpeg)

Dawarich is a self-hosted web application to replace Google Timeline (aka Google Location History). It allows you to import your location history from Google Maps Timeline and Owntracks, view it on a map and see some statistics, such as the number of countries and cities visited, and distance traveled.

You can find changelog [here](CHANGELOG.md).

## Disclaimer

⚠️ The project is under very active development.

⚠️ Expect bugs and breaking changes.

⚠️ Do not delete your original Google Maps
Timeline data after importing it to Dawarich.

⚠️ Export your data from Dawarich using built-in
export functionality before updating to a new version.

⚠️ Try to keep Dawarich up-to-date to have the latest features and bug fixes.

## Usage

To track your location, install the [Owntracks app](https://owntracks.org/booklet/guide/apps/) or [Overland app](https://overland.p3k.app/) on your phone and configure it to send location updates to your Dawarich instance.

### OwnTracks

The url to send the location updates to is `http://<your-dawarich-instance>/api/v1/owntracks/points?api_key=YOUR_API_KEY`.

Currently, the app only supports [HTTP mode](https://owntracks.org/booklet/tech/http/) of OwnTracks.

### Overland

The url to send the location updates to is `http://<your-dawarich-instance>/api/v1/overland/batches?api_key=YOUR_API_KEY`.

Your API key can be found and/or generated in the user settings.

To import your Google Maps Timeline data, download your location history from [Google Takeout](https://takeout.google.com/) and upload it to Dawarich.

## How-to's

- [How to set up reverse proxy](docs/how_to_setup_reverse_proxy.md)
- [How to import Google Takeout to Dawarich](https://dawarich.app/docs/tutorials/import-existing-data#sources-of-data)
- [How to import Google Semantic History to Dawarich](https://dawarich.app/docs/tutorials/import-existing-data#semantic-location-history)
- [How to import Google Maps Timeline Data to Dawarich](https://dawarich.app/docs/tutorials/import-existing-data#recordsjson)
- [How to track your location to Dawarich with Overland](https://dawarich.app/docs/tutorials/track-your-location#overland)
- [How to track your location to Dawarich with OwnTracks](https://dawarich.app/docs/tutorials/track-your-location#owntracks)
- [How to export your data from Dawarich](https://dawarich.app/docs/tutorials/export-your-data)

More guides can be found in the [Docs](https://dawarich.app/docs/intro)

## Features

### Location Tracking

You can track your location using the Owntracks or Overland app.

### Location history

You can view your location history on a map. On the map you can enable/disable the following layers:

- Heatmap
- Points
- Lines between points

### Statistics

You can see the number of countries and cities visited, the distance traveled, and the time spent in each country, splitted by years and months.

### Import

You can import your existing location history from:

- Google Maps Timeline
- OwnTracks
- Strava
- Your own GPX files
- Your photos' EXIF data

## How to start the app locally

`docker-compose up` to start the app. The app will be available at `http://localhost:3000`.

Press `Ctrl+C` to stop the app.

## How to install the app

**[Docker](docs/How_to_install_Dawarich_using_Docker.md)**

**[Synology](docs/How_to_install_Dawarich_on_Synology.md)**

### Default credentials

- **Username**: `user@domain.com`
- **Password**: `password`

Feel free to change them both in the Account section.

## Environment variables

| ENV var name                                                          | Description                                                                                                                |
|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| MIN_MINUTES_SPENT_IN_CITY                                             | minimum minutes between two points to consider them as visited the same city, e.g. `60`                                    |
| TIME_ZONE                                                             | time zone, e.g. `Europe/Berlin`, full list is [here](https://github.com/Freika/dawarich/issues/27#issuecomment-2094721396) |
| APPLICATION_HOSTS                                                     | list of host of the application, e.g. `localhost,dawarich.example.com`                                                        |
| BACKGROUND_PROCESSING_CONCURRENCY (only for dawarich_sidekiq service) | Number of simultaneously processed background jobs, default is 10                                                          |
| REVERSE_GEOCODING_ENABLED | `true` or `false`, this env var allows you to disable reverse geocoding feature entirely                                                          |
| PHOTON_API_HOST | Photon reverse geocoding api host. Useful, if you're running your own Photon instance                                                          |

## Star History

As you could probably guess, I like statistics.

<a href="https://star-history.com/#Freika/dawarich&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=Freika/dawarich&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=Freika/dawarich&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=Freika/dawarich&type=Date" />
 </picture>
</a>
