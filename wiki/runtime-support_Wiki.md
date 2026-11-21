# SigmaOS-runtime-support Wiki

## Overview
Shared runtime primitives extracted from SigmaOS-system: config, error, crypto entropy, klib shims, service lifecycle, orchestrator. Part of the SigmaOS multi-repository component fleet; implementation
was extracted from the SigmaOS-system monolith and hardened where required
(`OnceLock<Mutex<T>>` singletons, serialized global-state tests).

## Modules
- `config`
- `crypto`
- `error`
- `klib`
- `orchestrator`
- `service`

## Principles
- Single Responsibility / one component per repo
- Fail-fast initialization and defensive programming
- Race-free, deadlock-free singleton access
- Deterministic, isolated tests (`cargo test`)
- Stable API via `COMPONENT.toml` contract (`provides`/`depends_on`)

## Usage
```bash
cargo test          # run component tests
cargo build --release
```

## Integration
Registered in the connector registry (`COMPONENTS.toml`) and reachable via
`scripts/sigma_hub.sh` fleet operations (`list`, `status`, `test`, `sync`).
