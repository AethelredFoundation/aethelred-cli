<h1 align="center">aethelred-cli</h1>

<p align="center">
  <strong>The official command-line interface for the Aethelred blockchain</strong><br/>
  Submit AI jobs · Verify Digital Seals · Manage validators · Query on-chain state
</p>

<p align="center">
  <a href="https://github.com/aethelred-foundation/aethelred-cli/actions/workflows/repo-security-baseline.yml"><img src="https://img.shields.io/github/actions/workflow/status/aethelred-foundation/aethelred-cli/repo-security-baseline.yml?branch=main&style=flat-square&label=Security" alt="Security"></a>
  <a href="https://github.com/aethelred-foundation/aethelred-cli/actions/workflows/docs-hygiene.yml"><img src="https://img.shields.io/github/actions/workflow/status/aethelred-foundation/aethelred-cli/docs-hygiene.yml?branch=main&style=flat-square&label=Docs+Hygiene" alt="Docs Hygiene"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square" alt="License"></a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Rust-1.85+-DEA584?style=flat-square&logo=rust&logoColor=white" alt="Rust">
  <img src="https://img.shields.io/badge/PQC-Kyber+Dilithium-purple?style=flat-square" alt="PQC">
  <img src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey?style=flat-square" alt="Platform">
  <a href="https://docs.aethelred.io/cli"><img src="https://img.shields.io/badge/docs-CLI-orange?style=flat-square" alt="Docs"></a>
</p>

---

## Install

**macOS / Linux (Homebrew):**
```bash
brew install AethelredFoundation/tap/aethel
```

**Cargo:**
```bash
cargo install aethel
```

**Download binary** from [Releases](https://github.com/AethelredFoundation/aethelred-cli/releases):
```bash
curl -sSL https://install.aethelred.io | bash
```

---

## Quick Start

```bash
# Configure network
aethel config set --network testnet
aethel config set --rpc https://rpc.testnet.aethelred.io

# Create / import a wallet
aethel wallet create --name mykey
aethel wallet import --mnemonic "your twelve word mnemonic..."

# Check balance
aethel bank balance --address aethel1abc...

# Submit an AI compute job
aethel pouw submit-job \
  --model-hash abc123... \
  --input ./my_prompt.json \
  --verification-type hybrid \
  --from mykey

# Query a Digital Seal
aethel seal get --job-id <job-id>

# Verify a seal
aethel seal verify --seal-id <seal-id>
```

---

## Command Reference

| Command | Description |
|---|---|
| `aethel config` | Manage CLI configuration (network, RPC, keyring) |
| `aethel wallet` | Create, import, list, and export wallets |
| `aethel bank` | Token transfers and balance queries |
| `aethel pouw submit-job` | Submit an AI compute job |
| `aethel pouw list-jobs` | List your submitted jobs |
| `aethel pouw rewards` | Query your validator rewards |
| `aethel seal get` | Get a Digital Seal by job ID or seal ID |
| `aethel seal verify` | Verify a Digital Seal's authenticity |
| `aethel seal list` | List recent Digital Seals |
| `aethel model register` | Register an AI model on-chain |
| `aethel model list` | List registered models |
| `aethel validator list` | List active validators |
| `aethel gov propose` | Submit a governance proposal |
| `aethel gov vote` | Vote on a governance proposal |
| `aethel status` | Node health and chain status |
| `aethel version` | Print CLI version |

---

## Tools

This repo also contains:

| Tool | Description |
|---|---|
| `seal-verifier` | Standalone seal verification binary |
| `model-registry` | Model registration CLI tool |

---

## Development

```bash
# Build
cargo build --workspace

# Test
cargo test --workspace

# Lint
cargo clippy -- -D warnings

# Run locally
cargo run --bin aethel -- --help
```

---

## Related

- [AethelredFoundation/aethelred](https://github.com/AethelredFoundation/aethelred) — Core node
- [AethelredFoundation/aethelred-sdk-rs](https://github.com/AethelredFoundation/aethelred-sdk-rs) — Rust SDK (used internally)
- [Docs](https://docs.aethelred.io/cli)
