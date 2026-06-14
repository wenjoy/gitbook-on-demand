# SDK Version Matrix

This page is the version reference for Switchboard docs, examples, and verifier tooling.

- Baseline date: **June 12, 2026**
- Source of truth: [`tooling/sdk-versions.lock.json`](sdk-versions.lock.json)
- The lock file now tracks two different views:
  - `sdk_versions` / `companion_versions`: the **canonical docs pin set** used by current docs and compatibility checks
  - `observed_example_versions`: the **exact versions currently pinned in the checked-in `sb-on-demand-examples` manifests**

## Observed Versions In Current Examples

| Package / Crate | Observed Version(s) | Current Example References | Notes |
| --- | --- | --- | --- |
| `@switchboard-xyz/on-demand` | `^3.10.3` | `common`, `solana/feeds/*`, `solana/prediction-market`, `solana/randomness/coin-flip`, `solana/surge`, `solana/x402`, `sui/feeds/basic`, `sui/surge/basic` | Current TypeScript examples are aligned. |
| `@switchboard-xyz/common` | `^5.8.2` | `common`, `common/twitter-follower-count`, `common/variable-overrides`, `evm/*`, `solana/feeds/*`, `solana/prediction-market`, `solana/randomness/coin-flip`, `solana/surge`, `solana/x402` | Current TypeScript examples are aligned. |
| `@switchboard-xyz/on-demand-solidity` | `^1.1.0` | `evm/price-feeds`, `evm/randomness/*` | Current EVM examples are aligned. |
| `@switchboard-xyz/sui-sdk` | `^0.1.16` | `sui/feeds/basic`, `sui/surge/basic` | Aligned across current Sui examples. |
| `switchboard-on-demand` | `0.13.0` | `common/rust-feed-creation`, `solana/feeds/*`, `solana/prediction-market`, `solana/randomness/coin-flip` | Current Rust examples are aligned. |
| `switchboard-protos` | `0.2.6` | `solana/prediction-market` | Only used by the prediction-market program. |
| `pinocchio` | `0.11.2` | `solana/feeds/advanced` | Companion dependency for the low-CU Pinocchio example. |

## Canonical Docs Pin Set

These are the current docs pins for examples-verified flows.

| Package / Crate | Canonical Pin | Notes |
| --- | --- | --- |
| `@switchboard-xyz/on-demand` | `3.10.3` | Matches the current TypeScript example set. |
| `@switchboard-xyz/common` | `5.8.2` | Matches the current shared EVM and Solana TypeScript examples. |
| `@switchboard-xyz/on-demand-solidity` | `1.1.0` | Current Solidity interface pin. |
| `@switchboard-xyz/sui-sdk` | `0.1.16` | Matches current Sui examples. |
| `@switchboard-xyz/aptos-sdk` | `0.1.5` | Used by the Aptos and Movement docs. |
| `@switchboard-xyz/iota-sdk` | `0.0.3` | Current docs pin. |
| `switchboard-on-demand` | `0.13.0` | Matches current Rust examples. |
| `switchboard-protos` | `0.2.6` | Matches the current prediction-market example. |

## Companion Dependencies

| Dependency | Canonical Pin | Notes |
| --- | --- | --- |
| `@solana/web3.js` | `1.98.0` | Matches current Solana examples. |
| `@mysten/sui` | `1.38.0` | Compatible with current Sui docs/examples import surface. |
| `@aptos-labs/ts-sdk` | `6.1.0` | Aptos + Movement smoke projects. |
| `@iota/iota-sdk` | `1.11.0` | Iota smoke projects. |
| `ethers` | `6.13.1` | Matches the current EVM price-feeds example manifest. |
| `@coral-xyz/anchor` | `0.31.1` | Matches the current Solana example manifests. |
| `pinocchio` | `0.11.2` | Matches the advanced Solana price-feed example. |

## Toolchain Baseline

| Tool | Version |
| --- | --- |
| Node.js | `23.11.0` (verified, `>=24` recommended for `@iota/iota-sdk`) |
| Bun | `1.3.6` |
| Rust | `1.89.0-nightly` |
| Anchor CLI | `0.31.1` |
| Solana CLI | `2.3.11` |
| Foundry (`forge`) | `1.5.0` |
| Aptos CLI | `8.1.0` |
| Sui CLI | `1.73.1` |

## Known Notes

- Current TypeScript example manifests are aligned on `@switchboard-xyz/on-demand@^3.10.3` and `@switchboard-xyz/common@^5.8.2`.
- `@mysten/sui` latest `2.x` still breaks the import surface used in current docs/examples, so `1.38.0` remains pinned.
- Current Solana Rust examples use `switchboard-on-demand = "0.13.0"`. The advanced Pinocchio price-feed example uses `pinocchio = "0.11.2"` and the `AccountView` API.
- `sui/feeds/basic` defaults its checked-in `Move.toml` to testnet. Use the explicit `build:testnet`, `build:mainnet`, `deploy:testnet`, and `deploy:mainnet` scripts when documenting or verifying flows.
