# ct-cert-feed (Artifacts & Schema)

Download normalized, deterministic Certificate Transparency (CT) log snapshots as bulk JSON.

This repository publishes the canonical schema and sample artifacts for a daily CT snapshot dataset.

It does NOT contain the ingestion or production pipeline code.

---

## Why This Exists

Building a Certificate Transparency ingestion pipeline is non-trivial.

Common challenges include:

- Fetching CT log entries at scale
- Handling x509 vs precertificate entries correctly
- De-duplicating entries across logs
- Parsing and normalizing SAN DNS names
- Managing schema stability over time
- Replaying CT logs deterministically by date
- Avoiding brittle ad-hoc JSON extraction logic

ct-cert-feed provides a normalized daily snapshot so teams can focus on analysis instead of log scraping.

---

## What This Dataset Provides

A deterministic daily snapshot of certificate lifecycle facts derived from selected public CT logs.

Each record represents one CT entry and includes:

- CT log metadata (log name, index, timestamp)
- Entry timestamp
- Certificate serial number
- Validity window (`not_before`, `not_after`)
- Subject and issuer attributes
- SAN DNS names
- Public key algorithm and key size
- Signature algorithm
- Precertificate metadata (when applicable)

The dataset contains facts only.  
No scoring. No policy judgments. No enrichment.

---

## Snapshot Format

Snapshots are published as:

- `records.jsonl.gz` — newline-delimited JSON (gzip compressed)
- `stats.json` — totals and per-log breakdown

Example structure:

date=2026-01-31/

├── records.jsonl.gz

└── stats.json


This format is designed for:

- Bulk ingestion into Postgres
- Offline cryptographic analysis
- Certificate lifecycle analytics
- Historical CT replay
- Asset inventory correlation

---

## Schema

Canonical definitions:

- `schemas/v1/normalized_record.schema.json`
- `schemas/v1/stats.schema.json`

Schema versioning is strict and monotonic.

Breaking changes require a version increment.

---

## Example Artifacts

See `examples/` for representative snapshot samples:

- Example `records.jsonl`
- Example `stats.json`

These samples are limited in size but reflect production structure.

---

## Coverage

The dataset is derived from a selected set of major public CT logs.

Goals:

- Deterministic structure
- Stable normalization
- Operational simplicity

Non-goals:

- Exhaustive internet coverage
- Real-time monitoring
- Alerting or notification

See `docs/coverage.md`.

---

## Common Use Cases

- Certificate inventory systems
- Security research
- Compliance analytics
- CT historical replay
- Passive asset discovery
- Cryptographic ecosystem research
- Building higher-level CT intelligence systems

---

## Access

Current daily snapshots are available via authenticated HTTP.

If you are evaluating this dataset for:

- Certificate transparency bulk download
- CT log normalization
- Historical CT analysis
- Ingesting CT logs into your own pipeline

Open an issue labeled `access` and describe your intended use case.

---

## Non-Goals

This is NOT:

- A TLS monitoring service
- A vulnerability scanner
- A policy engine
- A compliance enforcement tool
- An active internet scanner

Interpretation belongs downstream.

---

## License

See `LICENSE` for repository terms.

Data artifacts are separately licensable outputs.
