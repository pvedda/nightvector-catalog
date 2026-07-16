# Catalog Notices: catalog-v2

## Released Artifact

- File: `nightvector-athyg-full.sqlite`
- Catalog schema version: `4`
- SHA-256: `46582bf96e1cec7bc50855114b7e0ab3943cdf48fd994011129ed6d29ff17913`
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

NightVector converts the AT-HYG split CSV sources and OpenNGC database CSV into a merged SQLite database. The transformation validates source rows, skips invalid or duplicate records, normalizes fields, imports stellar color indexes, creates stable catalog identifiers, adds source attribution and astrometry metadata, and builds search indexes. The generated database is a derivative work licensed under CC BY-SA 4.0.

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

The app source repository's `ci_scripts/ci_post_clone.sh` downloads this exact release asset, verifies its SHA-256 checksum, and validates its internal catalog metadata before every Release archive. This complete catalog uses schema 4 and contains 2,429,896 populated stellar color indexes.
