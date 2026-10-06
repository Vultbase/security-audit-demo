# Vultbase security audit demo

Minimal protocol repo to validate the [Vultbase GitHub Action](https://github.com/Vultbase/vultbase-action) end-to-end.

## Setup

1. Create an API key: [vultbase.com](https://www.vultbase.com) → **Settings** → **API Keys** → **New Key** (`vb_live_…`).
2. Add a **repository secret** on this repo (not on the action repo): **`VULTBASE_API_KEY`**.

## What to expect

- `contracts/VaultV1.sol` is intentionally vulnerable (reentrancy).
- The audit step may **fail** (red) when critical/high findings exceed `fail-on: critical` — that is normal.
- The job **succeeds** only if Vultbase returns a `job-id` and **at least one finding** (`Verify vulnerabilities were detected`).

## Run manually

**Actions** → **Vultbase Security Audit** → **Run workflow**.

## Consumer template

Copy this repo or use the same layout: `contracts/`, `.vultbase.yml`, and `.github/workflows/vultbase-security-audit.yml` with `uses: Vultbase/vultbase-action@v1`.
