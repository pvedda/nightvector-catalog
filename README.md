# NightVector Catalog Releases

This repository publishes versioned NightVector production catalog databases. It is separate from the NightVector iOS application source repository.

Each GitHub Release contains:

- `nightvector-athyg-full.sqlite`: the merged SQLite catalog shipped with NightVector.
- `nightvector-athyg-full.sqlite.sha256`: the SHA-256 checksum for the database.
- `CATALOG-NOTICES.md`: attribution, licensing, source versions, and build provenance.

Download a specific tagged release rather than a mutable `latest` asset. NightVector Xcode Cloud builds verify both the release checksum and the catalog's internal production metadata before embedding it in a Release archive.

## License

The released catalog data is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). See `LICENSE-CATALOG.md` and `CATALOG-NOTICES.md` for required attribution and source details.

NightVector application code is separate from this catalog data and is not licensed by this repository.

## Reproducibility

The catalog is produced from the pinned AT-HYG and OpenNGC source revisions recorded in each release's notices using the NightVector catalog build pipeline. The build validates SQLite integrity, schema, metadata, source accounting, and production row counts before publication.
