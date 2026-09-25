# Ghost Data Cleaner & SQL Importer

A simple tool to clean, normalize, and export your Ghost CMS content for import into other systems like **Directus**, **Neon (PostgreSQL)**, or any SQL database.

**Repository:** [mvvk-space/Ghost-CMS-JSON-Cleaner](https://github.com/mvvk-space/Ghost-CMS-JSON-Cleaner)

## What it does

1. **Cleans**: Takes a raw `ghost.json` export and strips out the noise.
2. **Normalizes**: Formats dates, booleans, and extracts useful relationships (tags, authors) into a flat, usable structure.
3. **Exports**: Generates a generic `cleaned_data.json` ready for use.
4. **Generates SQL**: Optionally converts that JSON into standard SQL `INSERT` statements.

## Quick start

```bash
git clone https://github.com/mvvk-space/Ghost-CMS-JSON-Cleaner.git
cd Ghost-CMS-JSON-Cleaner
npm install
cp .env.example .env   # edit with your DATABASE_URL if using Neon/Postgres
```

1. Export your content from Ghost Admin → Settings → Export, saved as `ghost.json`.
2. Run `node clean.js` → generates `cleaned_data.json`.

## Supported destinations

- **Neon / PostgreSQL** — `node neon/import.js` (direct import) or `node neon/json-to-sql.js` (generate SQL)
- **Directus** — see [directus/README.md](./directus/README.md)
- **Anything else** — `cleaned_data.json` is an array of objects with standard fields (`title`, `slug`, `html`, `tags`, …) ready for any CMS, static site generator, or database.