# Pirated-MovieSites-MediaExtractor

Supports extracting Media Sources (direct video source with no ads) from various pirated movie sites such as (Bilutv, KhoaiTV, etc.). Caching system is implemented to avoid IP bans, so the code is basically production ready.
```bash
npm install
npm run start
```

# Implementation Summary

1. Implement media source extracting schema for each sites. (source: `site/*.js`)
2. Caching system:
    + `cache/*.js` contains multiple implementations of CacheManager extending from `cache/base.js`. 
    + CacheManager is utilized in retrieving metadata from `streaming_services` (Hydrax, Google Drive, Google Photos, Youtube, ...) and pirated sites metadata (Phimmoi's API, Bilutv's API)
    + Muti-layer cache:
        + Since we need to retrieve site's metadata (through SiteAPI) before getting the necessary information to call Streaming Service's API, a multi-layer cache is implemented to handle cases when one of them goes down, or both go down. (IP bans)


