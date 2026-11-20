# Support & Solana Sponsorship

Thank you for using and supporting **LumenPitch** ([`https://github.com/annoris/lumenpitch`](https://github.com/annoris/lumenpitch)) — the local-first, open-source AI presentation and visual document engine.

## Solana Sponsorship & Release Access

You can support ongoing development or unlock verified release access via **Solana Mainnet** (`SOL` or `USDC-SPL`).

### Official Solana Wallet Address

```text
3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm
```

- **Network:** Solana Mainnet (`mainnet-beta`)
- **Accepted Assets:**
  - **SOL** (Native Solana)
  - **USDC-SPL** (USD Coin on Solana — Mint: `EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`)
- **Block Explorer:** [View on Solscan](https://solscan.io/account/3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm)
- **QR Code:** See [`docs/images/solana-pay-qr.svg`](https://github.com/annoris/lumenpitch/blob/main/docs/images/solana-pay-qr.svg)

---

## Claiming Release Access ($149 USD One-Time)

If you are purchasing the **$149 USD** one-time release access pass:

1. Send **$149 USD equivalent in SOL** or **149 USDC-SPL** on **Solana Mainnet** to:
   ```text
   3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm
   ```
2. Include your GitHub username in the on-chain SPL Memo field in the exact format:
   ```text
   gh:<your-github-username>
   ```
3. Open a [**Claim Release Access ($149 Solana Pay)**](https://github.com/annoris/lumenpitch/issues/new?template=claim-release-access.yml) issue on GitHub and paste your Base58 transaction signature (`txSig`).
4. Our automated GitHub Actions workflow ([`.github/workflows/verify-solana-payment.yml`](https://github.com/annoris/lumenpitch/blob/main/.github/workflows/verify-solana-payment.yml)) will verify the transaction directly against Solana Mainnet RPC and unlock your access. You can also enter your transaction signature directly inside the in-app **Solana License & Release Gate** modal.

---

## Technical Support & Issue Reporting

- **Architecture & Setup:** Read [`docs/ARCHITECTURE.md`](https://github.com/annoris/lumenpitch/blob/main/docs/ARCHITECTURE.md) and [`docs/PROJECT_STRUCTURE.md`](https://github.com/annoris/lumenpitch/blob/main/docs/PROJECT_STRUCTURE.md).
- **Diagnostics:** Run `node scripts/project-health.mjs` to inspect local workspace health without accessing credentials or external services.
- **Bug Reports:** Use the [Bug Report](https://github.com/annoris/lumenpitch/issues/new?template=bug_report.yml) template and never include API keys, `.env` files, private databases, or confidential documents.
- **Feature Requests:** Use the [Feature Request](https://github.com/annoris/lumenpitch/issues/new?template=feature_request.yml) template.
