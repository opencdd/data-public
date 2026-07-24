# OpenCDD — Public Sample Data

Public sample data and tooling for [OpenCDD](https://opencdd.github.io), an
open Common Data Dictionary online resource republishing IEC CDD data with
additional models built on the same schema.

This repo holds the **public, freely redistributable** subset:

- **OceanRunner** sample dictionary (`data/oceanrunner/`) — a small marine-propulsion
  ontology used as a fixture and demo across the OpenCDD ecosystem.
- **CDDAL spec** (`reference-docs/specs/cddal-v1.adoc`) — the CDD Authoring
  Language plain-text format spec.
- **OceanRunner source** (`reference-docs/examples/oceanrunner.cddal`) — the
  CDDAL source the sample JSON is built from.
- Slim **Rakefile** + **Gemfile** for building the sample.

For the full IEC CDD dictionary data, see the sibling **private** repo
[`opencdd/data-private`](https://github.com/opencdd/data-private) (access
restricted — IEC SC3D redistribution terms apply).

## Quick start

```bash
bundle install
bundle exec rake browser:sample     # build data/oceanrunner/database.json from CDDAL
```

You'll need the [`opencdd`](https://github.com/opencdd/opencdd-ruby) Ruby gem
installed. For local development across the opencdd org repos, the Gemfile
uses a path dependency — clone `opencdd-ruby` as a sibling directory:

```
src/opencdd/
├── data-public/      (this repo)
├── data-private/     (private — IEC data, scrapers, full pipeline)
├── opencdd-ruby/     (the gem)
├── opencdd-ts/       (@opencdd/models TypeScript port)
├── editor/           (OpenCDD Editor)
└── opencdd.github.io/  (OpenCDD Browser)
```

## Related projects

| Repo | Purpose |
|------|---------|
| [`opencdd/data-private`](https://github.com/opencdd/data-private) | IEC CDD dictionary data, scrapers, full data pipeline (private) |
| [`opencdd/opencdd-ruby`](https://github.com/opencdd/opencdd-ruby) | Ruby gem implementing the CDD model + Parcel I/O + CDDAL |
| [`opencdd/opencdd-ts`](https://github.com/opencdd/opencdd-ts) | TypeScript value-object layer (`@opencdd/models`) |
| [`opencdd/editor`](https://github.com/opencdd/editor) | OpenCDD Editor (Parcel authoring web app) |
| [`opencdd/opencdd.github.io`](https://github.com/opencdd/opencdd.github.io) | OpenCDD Browser (read-only CDD browser) |

## License

BSD-3-Clause. See [LICENSE](LICENSE).
