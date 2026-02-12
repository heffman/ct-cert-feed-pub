# Access

## Public Repository

This repository contains:

- Canonical JSON schemas
- Documentation
- Sample artifacts
- Coverage notes

It does not include:

- Production ingestion infrastructure
- Operational automation
- Live daily snapshots

The public materials exist to allow evaluation of structure, schema stability, and integration feasibility.

---

## Production Data Access

Current daily snapshots are available via authenticated HTTPS delivery.

Delivery characteristics:

- Deterministic daily snapshot
- Gzip-compressed JSONL
- Stable schema versioning
- Per-day summary statistics
- No active scanning or outbound probing
- Derived exclusively from public CT logs

Intended for:

- Security research teams
- Certificate lifecycle analytics
- Cryptographic inventory systems
- Compliance evidence pipelines
- Large-scale passive telemetry analysis

This is bulk data infrastructure — not a monitoring service.

---

## Evaluation

For evaluation access, open an issue labeled `access` with:

- Organization or research affiliation
- Intended use case
- Expected ingestion frequency
- Estimated data retention window

Access decisions are discretionary.

No custom fields.
No custom pipelines.
No feature roadmap commitments.
