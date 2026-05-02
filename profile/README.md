# Typenx

Typenx is a self-hostable anime discovery and library platform built around open addons.

It brings together metadata from AniList, MyAnimeList, Kitsu, and your own media sources so you can browse anime, centralize seasons, manage addons, and build recommendation features without locking the project to one provider.

## Why It Exists

Anime libraries are scattered across tracking sites, metadata providers, and personal media servers. Typenx is an attempt to make that ecosystem feel coherent:

- Self-hosted Rust backend with SQLite, Postgres, MySQL, and MongoDB support.
- React frontend for discovery, account flows, addon management, and library views.
- Addon protocol for catalogs, search, metadata, recommendations, episodes, and optional video sources.
- Official metadata addons for AniList, MyAnimeList, and Kitsu.
- SDKs for TypeScript, Python, and Rust so contributors can build new sources quickly.

## Start Here

- Star and follow the main backend: [typenx-core](https://github.com/typenx/typenx-core)
- Try the frontend: [typenx-web](https://github.com/typenx/typenx-web)
- Build an addon: [TypeScript SDK](https://github.com/typenx/typenx-addon-TS-sdk), [Python SDK](https://github.com/typenx/typenx-addon-python-sdk), or [Rust SDK](https://github.com/typenx/typenx-addon-rust-sdk)

## Official Addons

- [AniList](https://github.com/typenx/typenx-addon-anilist): metadata and recommendations from AniList.
- [MyAnimeList](https://github.com/typenx/typenx-addon-myanimelist): metadata and recommendations from MAL.
- [Kitsu](https://github.com/typenx/typenx-addon-kitsu): metadata and recommendations from Kitsu.
- [Season Centralizer](https://github.com/typenx/typenx-addon-season-centralizer): merges split seasons into one clean show entry.
- [Video Library](https://github.com/typenx/typenx-addon-video-library): exposes user-controlled self-hosted video URLs.

## Help Build Typenx

If you like self-hosted media tools, anime discovery, or addon-first platforms, starring [typenx-core](https://github.com/typenx/typenx-core) helps more contributors find the project.

Useful ways to help:

- Star the repos you want to see grow.
- Open issues for rough edges, setup friction, or addon ideas.
- Build a small addon for a provider you already use.
- Share screenshots, feedback, or deployment notes.

Typenx is early, but the shape is there: a self-hosted anime hub that gets better every time someone plugs in a new source.
