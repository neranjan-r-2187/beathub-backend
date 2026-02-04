# Design Decisions

## Why did you reference Songs in the Playlist instead of embedding them?

I referenced songs in the `Playlist` by storing references (IDs) rather than embedding full song documents to keep a single source of truth for each `Song` entity. This avoids duplicating potentially large song objects across many playlists, makes updates to song metadata (title, duration, artwork, etc.) automatic for every playlist that includes the song, and improves storage efficiency. Referencing also makes it practical to support large or unbounded playlists, simplifies relationships (many-to-many), and enables efficient population queries when detailed song data is needed.

Embedding is appropriate when the embedded data is small, immutable, or tightly coupled to its parent. For playlists we prefer referencing because songs are first-class, shared resources.

## Why did you reference the Artist in the Song model?

The `Song` model references an `Artist` rather than duplicating artist information so that artist metadata is normalized and maintained in one place. Many songs share the same artist, so using a reference prevents data duplication, reduces inconsistencies, and makes it easy to update artist-level data (name, biography, images) without touching each `Song` document. References also enable efficient queries and population for artist-centric views (e.g., list all songs by an artist) and support richer artist-related features.

## Phase 4: Final Polish

Final polish tasks completed or recommended before production:

- Validate and enforce required fields and types in your Mongoose schemas.
- Add indexes for commonly queried fields (e.g., song IDs, artist IDs, user IDs, playlist owner).
- Ensure the seed script is idempotent or clearly documented (how it resets or seeds data).
- Add error handling and input validation for API endpoints.
- Add basic unit/integration tests for models and critical flows.
- Document running and environment setup (env vars, DB URL, seed instructions).
- Consider pagination and rate-limiting on list endpoints and large population queries.

These steps improve reliability, maintainability, and performance as the app moves toward production.
