# Schema Overview

Snapshots consist of:

- records.jsonl.gz
- stats.json

## Record Model

Each record represents one CT entry.

Core fields:

- record_id
- snapshot_date
- log_name
- log_index
- ct_timestamp_ms
- entry_type (x509 | precert)

For x509 entries:
- cert_sha256
- serial_number_hex
- not_before
- not_after
- subject fields
- issuer fields
- SAN DNS names
- public key algorithm + size
- signature algorithm

For precert entries:
- issuer_key_hash_hex
- tbs_sha256

All timestamps are ISO-8601 UTC.

All normalization is deterministic.

See JSON Schema definitions under `schemas/v1/`.
