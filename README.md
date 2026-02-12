# ct-cert-feed (Artifacts & Schema)

Daily, normalized TLS certificate lifecycle snapshots derived from selected public Certificate Transparency (CT) logs.

This repository contains:

- The canonical snapshot schema
- Documentation
- Sample artifacts
- Coverage notes
- Access information

It does NOT contain the ingestion or production pipeline code.

---

## What This Dataset Is

A daily, deterministic snapshot of certificate lifecycle facts extracted from public CT logs.

Each snapshot contains one record per CT entry and includes:

- CT log metadata
- Entry timestamp
- Certificate serial number
- Validity window
- Subject and issuer fields
- SAN DNS names
- Public key algorithm and size
- Signature algorithm
- Precertificate metadata (when applicable)

The dataset contains **facts only**.  
It does not assign risk scores or judgments.

---

## Snapshot Format

Snapshots are published as:

- `records.jsonl.gz` (newline-delimited JSON)
- `stats.json` (summary + per-log breakdown)

Example layout:

date=2026-01-31/

├── records.jsonl.gz

└── stats.json


See `schemas/v1/` for canonical definitions.

---

## Schema

Authoritative schemas:

- `schemas/v1/normalized_record.schema.json`
- `schemas/v1/stats.schema.json`

Schema versioning is strict and monotonic.

---

## Coverage

This dataset is derived from a selected set of major public CT logs.

It prioritizes:

- Consistency
- Stability
- Deterministic structure
- Operational simplicity

It does not attempt exhaustive internet coverage.

See `docs/coverage.md`.

---

## Example Artifacts

See `examples/` for:

- Sample `records.jsonl`
- Sample `stats.json`

These are representative but limited in size.

---

## Access

Current daily snapshots are available via authenticated HTTP.

If you are evaluating this dataset for:

- Security research
- Certificate lifecycle analytics
- Compliance tooling
- Passive inventory systems
- Bulk cryptographic research

Open an issue labeled `access` describing your use case.

---

## Non-Goals

This is NOT:

- A TLS monitoring service
- An alerting system
- A vulnerability scanner
- A policy enforcement engine
- An active scanner

Interpretation belongs downstream.

---

## License

See `LICENSE` for repository terms.

Data artifacts are separately licensable outputs.
