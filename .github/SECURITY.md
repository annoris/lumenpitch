# Security Policy

## Supported Versions

The **LumenPitch — AI-Powered Presentation Studio & Multi-LLM Deck Engine** team actively maintains security updates for the latest release branch:

| Version | Branch | Supported |
| :--- | :--- | :---: |
| **1.0.x** | `main` | ✅ Yes |
| **< 1.0.0** | Legacy pre-release | ❌ No |

---

## Security Architecture Overview

- **Self-Hosted Privacy:** All runtime data (`APP_DATA_DIRECTORY`, `USER_CONFIG_PATH`, `DATABASE_URL`) is stored outside the Git working tree.
- **Official Solana Treasury Verification:** The sole official Solana (`SOL` / `USDC-SPL`) payment and sponsorship wallet address associated with this project is:
  ```text
  3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm
  ```
  Always verify this exact address in [`SPONSORS.md`](../SPONSORS.md) and [`.github/FUNDING.yml`](./FUNDING.yml) before signing any transaction.

---

## Reporting a Vulnerability

Please report security vulnerabilities privately via GitHub's **Private Vulnerability Reporting** tab under the repository's **Security** section rather than opening a public issue.
