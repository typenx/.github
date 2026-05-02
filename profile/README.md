# Typenx

A self-hostable anime hub that ties tracking, metadata, recommendations, and your own media library together — and lets anyone plug in a new source.

If you watch anime, the tooling is fractured by design. AniList holds your tracking. MyAnimeList holds your scores from years ago. Kitsu mirrors the same data with a different schema. Your Plex or Jellyfin server holds the actual files. Your watch history lives in a fourth place. Recommendations come from whichever site happened to scrape you last.

Typenx is the layer that ties them together, runs on your own hardware, and stays open.

## What it is

A Rust backend, a React frontend, and an addon protocol. Every source — official or hobby, public or private — is a remote HTTP service that speaks the same schema. Typenx Core orchestrates them: it imports your AniList and MyAnimeList lists, asks metadata addons for catalogs and search, asks media addons for stream URLs, and runs its own recommendation model on top.

You host it. You own the database. You can read every line of the recommender. New sources are a few hundred lines of TypeScript, Python, or Rust away.

## Repos

**Core**

- [typenx-core](https://github.com/typenx/typenx-core) — the Rust backend (Axum, multi-database storage, addon orchestration, recommendations).
- [typenx-web](https://github.com/typenx/typenx-web) — the React frontend (discovery, library, account, addon management).

**Official metadata addons**

- [typenx-addon-anilist](https://github.com/typenx/typenx-addon-anilist) — AniList catalogs, search, and metadata.
- [typenx-addon-myanimelist](https://github.com/typenx/typenx-addon-myanimelist) — MyAnimeList catalogs, search, and metadata.
- [typenx-addon-kitsu](https://github.com/typenx/typenx-addon-kitsu) — Kitsu catalogs, search, and metadata.

**Utility addons**

- [typenx-addon-season-centralizer](https://github.com/typenx/typenx-addon-season-centralizer) — collapses split-season releases (`Attack on Titan`, `Attack on Titan Season 2`, `Attack on Titan: The Final Season`) into one show with merged episode numbering.

**Personal-media addons**

- [typenx-addon-plex](https://github.com/typenx/typenx-addon-plex) — expose a Plex server as a Typenx video source.
- [typenx-addon-jellyfin](https://github.com/typenx/typenx-addon-jellyfin) — expose a Jellyfin server as a Typenx video source.
- [typenx-addon-video-library](https://github.com/typenx/typenx-addon-video-library) — point Typenx at a JSON manifest of URLs you already control.

**SDKs for addon authors**

- [typenx-addon-TS-sdk](https://github.com/typenx/typenx-addon-TS-sdk)
- [typenx-addon-python-sdk](https://github.com/typenx/typenx-addon-python-sdk)
- [typenx-addon-rust-sdk](https://github.com/typenx/typenx-addon-rust-sdk)

## What makes it interesting

**An addon protocol that doesn't compromise.** Addons are remote HTTP services with a typed schema, not bundled plugins. Same shape whether they're official, run on your own laptop, or shared between a handful of friends. Manifests declare the resources they provide — `catalog`, `search`, `anime_meta`, `recommendations`, `video_sources` — and Typenx routes calls accordingly.

**A recommender you can actually inspect.** Typenx's recommender is an explainable hybrid model that builds a taste profile from your AniList and MyAnimeList list scores, watch progress, dropped/paused/completed states, and addon metadata (genres, tags, studios, source, era). It runs locally, returns reason snippets when asked, and ships with a training script that fits an implicit-feedback matrix-factorization model on your own database.

**Storage you choose.** SQLite for a homelab, Postgres for a real server, MySQL if you already run one, MongoDB if that's your stack. Same repository boundary, same code paths, one environment variable away.

**Tracking and watching, finally connected.** Sync your AniList list once, then resolve "where can I watch episode 7" against Plex, Jellyfin, or whatever video addon you've registered. The split between metadata and playback is intentional, so any source can drop out without breaking the rest of your library.

## Where to start

If you want to run Typenx, start at [typenx-core](https://github.com/typenx/typenx-core). The quick start is `cargo run -p typenx-server` plus a script that brings up the official addons next to it.

If you want to build something on top, pick an SDK and read the addon protocol — your service runs anywhere and shows up in any Typenx instance that points at it.

If you want to follow development, watch the org. Issues, design notes, and active work all live inside the individual repos.
