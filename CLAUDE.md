# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

**`opencdd/data-public`** is the public, freely-redistributable sample-data
repo for [OpenCDD](https://opencdd.github.io). It exists so newcomers can
clone a small, license-clean subset of OpenCDD without needing access to the
IEC CDD data.

For the IEC CDD dictionary data (full ~25K entities across 7 dictionaries,
raw scrapes, reference PDFs), see the sibling **private** repo
[`opencdd/data-private`](https://github.com/opencdd/data-private).

## Contents

- `data/oceanrunner/database.json` — built sample (40 entities, marine propulsion).
- `data/index.json` — single-dict index (oceanrunner only).
- `reference-docs/examples/oceanrunner.cddal` — OceanRunner source in CDDAL.
- `reference-docs/specs/cddal-v1.adoc` — CDD Authoring Language spec (AsciiOIDC).
- `Rakefile` — slim; just `rake browser:sample` and `rake generate_ts`.
- `Gemfile` — path-depends on the sibling `opencdd-ruby` checkout.

## Commands

```bash
bundle exec rake browser:sample     # rebuild data/oceanrunner/database.json from CDDAL
bundle exec rake generate_ts        # regenerate opencdd-ts registry files (rarely needed here)
```

## Sibling repo conventions

Local development assumes all opencdd repos are checked out as siblings under
`src/opencdd/`:

- `data-private/` — full IEC data, scrapers, release pipeline.
- `opencdd-ruby/` — the gem (path dep from `Gemfile`).
- `opencdd-ts/` — TS port of the gem.
- `editor/` — Parcel authoring web app.
- `opencdd.github.io/` — read-only CDD browser.

## License

BSD-3-Clause. IEC CDD data is **not** in this repo — it lives in `data-private`
under separate IEC SC3D redistribution terms.
