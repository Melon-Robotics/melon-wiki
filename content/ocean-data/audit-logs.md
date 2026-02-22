+++
title = 'Audit Logs & Immutability'
description = 'Tamper-evident audit trails and immutable data records for subsea operations'
date = 2024-01-01T00:00:00Z
draft = false
+++

# Audit Logs & Immutability

Audit logs record what happened, when, and by whom — and must be structured so that no one can alter them without that alteration being detectable. In subsea operations, audit logs support incident investigation, regulatory compliance, and data integrity verification.

## Why This Exists

Raw data and derived products are only trustworthy if the chain of custody can be proven. Audit logs provide the evidence trail. Without tamper-evident logs, data can be altered after the fact — intentionally or accidentally — and the alteration cannot be detected. Regulatory bodies and legal proceedings require that evidence of data integrity be demonstrable.

## Who This Is For

- Data managers designing data storage and access systems
- Safety officers investigating incidents
- Regulators reviewing operational records
- Legal and compliance teams responding to disputes or incidents

## What Audit Logs Must Record

A complete audit log entry records:

- **Timestamp** — When the event occurred (UTC, with sub-second precision where relevant)
- **Actor** — Who or what performed the action (user ID, system ID, software version)
- **Action** — What was done (create, read, update, delete, export)
- **Object** — What was acted upon (file path, record ID, dataset name)
- **Source address** — Where the action originated (IP address, terminal ID)
- **Result** — Whether the action succeeded or failed
- **Context** — Any relevant operational context (dive ID, deployment ID)

## Immutability Requirements

### Append-Only Design

Audit logs must be append-only: entries can be added but not modified or deleted. Systems that allow modification or deletion of audit log entries are not audit logs — they are records that can be falsified.

**Implementation options:**
- Write-once storage media
- Cryptographic chaining (each entry includes a hash of the previous entry)
- Append-only log services with access controls preventing modification
- Offsite replication to an independent system

### Cryptographic Chaining

Each log entry can include a cryptographic hash of the previous entry, creating a chain. Altering any entry breaks all subsequent hashes, making tampering detectable:

```
Entry N: { data, hash(Entry N-1) }
Entry N+1: { data, hash(Entry N) }
```

This structure is the basis of blockchain-style data integrity, applied here without the distributed consensus overhead.

### Timestamping

Timestamps must come from a trusted, authoritative source:

- **NTP-synchronised clocks** — Synchronised to a trusted time server
- **GPS time** — For systems deployed at sea where NTP may be unavailable
- **Third-party timestamping** — Cryptographic timestamps from a trusted authority prove data existed at a particular time

## Log Retention and Access

### Retention Periods

Retention requirements vary by jurisdiction and data type:

- **Operational logs** — Typically 2–5 years
- **Incident-related records** — Often retained indefinitely pending investigation closure
- **Environmental data** — May have regulatory-defined retention periods

Organisations must define and enforce retention policies. Automatic deletion before retention periods expire must be prevented.

### Access Controls

Access to audit logs must itself be logged:

- Reading logs is an auditable action
- Administrators who can manage log systems must not be able to delete entries
- Separation of duties: those who generate data should not be the sole custodians of that data's logs

## Operational Context

### Dive Operations

For diving operations, audit logs should capture:

- Gas mix preparation and verification sign-offs
- Dive supervisor authorisation entries
- In-water communication transcripts (or references to recordings)
- Equipment inspection completion records
- Any deviations from the approved dive plan

### ROV/AUV Operations

For autonomous and remotely operated vehicles:

- Mission file versions and upload timestamps
- Parameter changes made during operations
- Sensor data file creation and transfer records
- Operator intervention events

## Integration with Data Provenance

Audit logs and data provenance are related but distinct:

- **Audit logs** — Record system events and user actions
- **Data provenance** — Track the lineage of data products (where data came from and how it was processed)

Both are required for full accountability. See [Data Provenance & Chain-of-Custody](/ocean-data/provenance/) for provenance-specific guidance.

## Related Topics

- [Data Provenance & Chain-of-Custody](/ocean-data/provenance/)
- [Timestamp Integrity](/ocean-data/timestamps/)
- [Raw vs Derived Data](/ocean-data/raw-derived/)
- [Regulatory Landscape Overview](/safety-compliance/regulatory-landscape/)
