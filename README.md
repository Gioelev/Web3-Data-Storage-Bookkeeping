
# Allocator Bookeeping repository for <Web3-Data-Storage>
Web3-Data-Storage

## Allocator JSON Link
_put here a link to your allocator json from https://github.com/filecoin-project/Allocator-Registry/tree/main/Allocators_ recC3QfThf5mSgnB9

## Client Dilligence
1. Multi-Layered Identity Verification
For All Clients:
Tiered KYC:
Individuals: Government ID + liveness check (via Onfido/Jumio) for >1 TiB requests
Organizations: Business registration docs + domain-verified email (e.g., WHOIS match)
Web3 Reputation:
Minimum 6-month history on ENS, Gitcoin, or Filecoin network
Sybil score from tools like TrustaLabs or Gitcoin Passport (threshold: ≥20/100)

Enterprise Clients:
Notarized Data Affidavits:
CEO/CTO-signed declaration of data ownership
Cross-checked against incorporation documents
Infrastructure Proofs:
Historical cloud storage invoices (AWS/GCP last 3 months)
Source code repos showing dataset generation pipelines

2. Sybil Attack Mitigation
Deterministic Rules:
Auto-reject if:
IP geolocation ≠ KYC country
Wallet interacted with known Sybil clusters
GitHub account <1 year old for open-source data

3. Data Authenticity Validation
Technical Verification:
Pre-Storage:
SHA-256 checksums of raw datasets submitted pre-upload
Data schema validation against claimed type (e.g., Parquet for tabular data)
Post-Storage:
Random sampling (5% of deals) via Filecoin Proof-of-Replication challenges
Differential checks: Compare client's original checksum vs. on-chain storage receipts

Enterprise Specific:
Chain of Custody:
TLS-notarized transfer logs from origin servers
Video proof of data extraction from source systems

Audit & Governance Compliance
Evidence Documentation
GitHub issue
Dispute Resolution
14-Day Challenge Period:
Any community member can flag suspicious allocations
Require client to provide additional proofs within 72 hours


## Description of Data Diligence
1. Data Compliance Verification
Legal and Regional Review:
Automated Legal Screening Tools:
Integrate Rescale Legal API to scan data content and flag potential violations (e.g., GDPR/CCPA-sensitive data).
Use IPFS Legal Oracles to verify that storage locations match client declarations (e.g., EU data cannot be stored in non-GDPR-compliant nodes).
Ownership Proof Chain:
Enterprise Clients: Provide data asset registration certificates or blockchain notarization (e.g., recording data asset history via IPLD).
Individual Clients: Require legally binding data provenance declarations, notarized on-chain via EthSign.

High-Risk Data Handling:
Maintain a prohibited data list (e.g., HIPAA-regulated medical data requires additional encryption proof).
Dynamically update compliance rules (daily sync with DataGuidance for global legal changes).

2. Data Authenticity Verification
Enterprise Data Special Measures:
Require TLSNotary-certified data transfer logs.
Implement SQL Integrity Proofs for database content (via zkSQL validation credentials).

3. Audit Evidence Retention
On-Chain Verifiable Records:
Data Fingerprint Notarization:
All checksums recorded in Filecoin VM smart contract.
Process Certificates:
Computation proofs via Bacalhau (e.g., data cleaning logs).
zk-STARK proofs for sampling audits (tamper-proof verification).


## Short description of pathway for clients
Any data related to web3 can be stored in Filecoin.

## Contact info
emails:gioelev@sanshantech.cn

## Detailed Allocator policies, procedures, and requirements.

## Risk mitigation strategies 
_What is the processes for protecting your organization, reputation, and pathway from abuse. For example, what Operational Security (OpSec) standards, user agreements, alerts, or throttling mechanisms will you employ?_ 

## Dispute Resolutions 
To protect our organization, reputation, and pathway from abuse, Fivestar implements the following, enhanced by Enterprise-Data-Pathway practices:

Operational Security (OpSec): KYC/KYB data and client records are stored with encryption and access controls. Non-disclosure agreements protect client privacy during virtual meetings. Regular internal audits prevent data breaches.
User Agreements: Clients sign agreements ensuring compliance with Filecoin Plus policies, geographic requirements, and data ownership responsibilities.
Rate Limiting: DataCap capped at 1 PiB per round (or 5 PiB for trusted users), with phased distribution (5%–50%) and a 25% SP allocation limit per round to prevent overuse.
Alerts and Monitoring: DataCapStats.io and AC Bot monitor deal-making, distribution, and retrieval compliance weekly. CID Checker Bot flags anomalies for manual review.
Throttling Mechanisms: Automated checks limit request frequency and volume to prevent Sybil attacks or spam.
Non-Compliance Handling: Clients providing fake or misleading information face immediate application closure and potential blacklisting of GitHub IDs/miner IDs. Clients have up to 3 weeks to rectify non-compliance; failure leads to termination of future DataCap allocations.

## Compliance Audit Check
Client Compliance: KYC via Gitcoin Passport and KYB via Synaps.io or virtual meetings verify client identity and data ownership.
Storage Provider Compliance: AC Bot and DataCapStats.io verify 5 replicas, 3–4 geographic regions, 25% SP allocation limit, and SP KYB (if non-vetted SPs are used). Retrieval standards are checked via manual/automated verification.
Regular Audits: Internal audits of allocation records, storage deals, and compliance documentation are conducted, with records available for Fil+ Governance Team review.
Monitoring Tools: Weekly AC Bot checks, DataCapStats.io, and CID Checker Bot ensure ongoing compliance. Non-compliant applications are automatically closed if thresholds are not met.
