# Catalog Notices: catalog-v1

## Released Artifact

- File: `nightvector-athyg-full.sqlite`
- Catalog schema version: `3`
- SHA-256: `bf2e93aff476dfc99cbb3e2b56ad52d8cc010390cbe9971f1a61624734a8b5a3`
- Catalog objects: 2,565,053
- AT-HYG stars: 2,552,164
- OpenNGC objects: 12,889

## Sources And Attribution

### AT-HYG

- Dataset: [AT-HYG](https://codeberg.org/astronexus/athyg)
- Source repository: `https://codeberg.org/astronexus/athyg.git`
- Source commit: `f068ebdc446afe625614604d3b46dc593458caa3`
- License: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

### OpenNGC

- Dataset: [OpenNGC](https://github.com/mattiaverga/OpenNGC)
- Source repository: `https://github.com/mattiaverga/OpenNGC.git`
- Source commit: `36cb178a0f69dba8bfc03a99c10512831edf1c6b`
- License: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

## Transformations

NightVector converts the AT-HYG split CSV sources and OpenNGC database CSV into a merged SQLite database. The transformation validates source rows, skips invalid or duplicate records, normalizes fields, creates stable catalog identifiers, adds source attribution and astrometry metadata, and builds search indexes. The generated database is a derivative work licensed under CC BY-SA 4.0.

## Reproduction

From the NightVector source repository, use the pinned source commits above and run:

```sh
Scripts/build-athyg-catalog.py \
  --input .catalog-cache/athyg/data/athyg_v33-1.csv.gz \
  --input .catalog-cache/athyg/data/athyg_v33-2.csv.gz \
  --openngc .catalog-cache/openngc/database_files/NGC.csv \
  --output DerivedCatalogs/nightvector-athyg-full.sqlite
Scripts/validate-catalog.py DerivedCatalogs/nightvector-athyg-full.sqlite
```

The app source repository's `ci_scripts/ci_post_clone.sh` downloads this exact release asset, verifies its SHA-256 checksum, and validates its internal catalog metadata before every Release archive. The app currently accepts production catalog schema versions 3 and 4; this release intentionally remains schema 3 because no complete schema-v4 production artifact has been published yet.
