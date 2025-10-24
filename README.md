# Truth Unveiled

Truth Unveiled is a decentralized DAO project that stores verifiable artifacts on IPFS, uses Decentralized Identifiers (DIDs) for participant identity and reputation, coordinates governance/execution via Janction, and distributes incentives with a Kickback Rewards system.

This repository holds the code and documentation for the Truth Unveiled DAO — tooling, smart-contract interfaces, off-chain services, and docs to run, verify, and reward contributions.

## Quick overview

- Storage: Immutable content and artifacts are stored on IPFS (content-addressed).
- Identity: Participants use DIDs to authenticate and sign proposals/claims.
- Governance & Execution: Janction coordinates proposal lifecycle and on-chain actions (governance engine).
- Incentives: Kickback Rewards allocates rewards to contributors based on verifiable contributions and community voting.

## Who is this for

- DAO members who want to publish verifiable artifacts (reports, datasets, claims).
- Developers building integrations for IPFS, DID, and Janction.
- Contributors who want transparent, tokenized rewards based on measurable work.

## Table of contents

- [Getting started](#getting-started)
- [Architecture](#architecture)
- [How it works](#how-it-works)
- [Development commands](#development-commands)
- [Contributing](#contributing)
- [Roadmap](#roadmap)
- [License](#license)
- [Contact](#contact)

## Getting started

Prerequisites
- Git
- Node.js >= 18 and npm (if JavaScript/Node components)
- IPFS CLI (js-ipfs or go-ipfs) for local testing
- Docker (optional, for local services)
- A wallet / DID tool (e.g., did:key tooling, or wallet that supports DIDs)

Quick setup (example for local dev)
```bash
git clone https://github.com/cryptomx1/truth-unveiled.git
cd truth-unveiled

# install dependencies (adjust for your stack)
npm install

# start local dev server (placeholder - adjust to your project)
npm run dev
```

Publishing an artifact to IPFS (example)
```bash
# add file to local ipfs node
ipfs add ./artifacts/report.pdf
# ipfs add will return a CID (content identifier). Pin it if you want:
ipfs pin add <CID>
```

Register a DID (example using did:key; replace with your DID provider)
```bash
# generate a new keypair and derive a did:key
# (example tools vary; this is a conceptual step)
npx did-toolkit create --method key --output did.json
cat did.json
```

## Architecture

- frontend/ — web UI for proposal creation, artifact upload, and rewards dashboard
- backend/ — APIs that coordinate DID-based authentication, Janction calls, and reward calculation
- contracts/ — smart-contract interfaces (ABI + deployment scripts)
- infra/ — docker-compose or k8s manifests for local chains, IPFS, and indexing nodes
- docs/ — protocol specs, governance rules, and contributor guides

(Adjust these directories as needed for your project structure.)

## How it works (high-level)

1. A contributor uploads an artifact (data, report, media) to IPFS and receives a CID.
2. The contributor creates a signed claim referencing the CID tied to their DID.
3. A governance proposal is created (via Janction) referencing the CID and the claim.
4. DAO members vote. If approved, on-chain or off-chain actions execute via Janction.
5. Kickback Rewards are issued to the contributor and/or voters according to the reward rules.

## Development commands (examples)

Run tests:
```bash
npm test
# or
pnpm test
```

Run linters:
```bash
npm run lint
```

Build:
```bash
npm run build
```

Deploy (placeholder):
```bash
# scripts/deploy.sh should encapsulate network/contract specifics
./scripts/deploy.sh --network testnet
```

## Security & best practices

- Always pin critical artifacts on at least one trusted IPFS pinning service.
- Use DIDs with secure key management (hardware or secure keystores).
- Review governance contract upgrades via multi-sigs or time-locks.
- Audit reward calculation logic to avoid manipulation or edge-case exploits.

## Contributing

We welcome contributors. Suggested next docs to add:
- CONTRIBUTING.md — repo workflow, tests, PR process
- CODE_OF_CONDUCT.md
- SECURITY.md — disclosure process for vulnerabilities

If you plan to contribute code:
1. Fork the repo
2. Create a feature branch
3. Open a pull request describing the change and tests

## Roadmap

Planned items (example):
- v0.1: Core IPFS upload + DID signing + Janction integration
- v0.2: On-chain reward distribution + admin dashboard
- v0.3: Community reputation scoring + advanced Kickback rules

## License

This project uses the MIT License. See LICENSE for details.

## Contact

Owner: cryptomx1 — https://github.com/cryptomx1

For governance questions, open an Issue or discussion in this repo.
