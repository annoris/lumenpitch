# Preparing GitHub publication

The delivery is a local repository on `main`, without commits or a remote. Review diagnostics, validation and files before the first commit. Exclude `.env`, credentials, databases, customer documents, generated exports and local runtime data. Use `git status --short` to review files and `git diff --cached` to inspect staged changes.

Create a repository under your own account, add its real URL with `git remote add origin URL`, configure your Git identity, stage reviewed files and create the initial commit. No organization or domain is preconfigured. Preserve LICENSE, NOTICE and third-party notices.

Docker release images use `github.repository`. Configure your own authorized export-runtime download base before building; the export engine is not included. Provider-specific donation, hosting, external synchronization and temporary-publication workflows were removed. Electron signing requires your own certificates and identities. Update checks are disabled without `UPDATE_SERVER_URL` and `UPDATE_DOWNLOAD_URL`.

Do not publish a release as fully functional until you have verified its authorized export engine, real AI-provider generation and target platforms. See `VALIDATION.md` for the remaining dependency audit findings.

`docs/images` contains real product screenshots and the Solana Pay QR code (`docs/images/solana-pay-qr.svg`) linked from the README. Keep screenshots free of credentials, personal browser content and private documents. Runtime accounts and their passwords must never be included in publication archives.

## Solana Pay release gate ($149 USD one-time)

- **Official recipient wallet:** `3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm`
- **Issue template:** `.github/ISSUE_TEMPLATE/claim-release-access.yml` collects the buyer's Solana transaction signature (`txSig`) and payment asset (`SOL` or `USDC-SPL`) with the `release-access-claim` label.
- **Verification workflow:** `.github/workflows/verify-solana-payment.yml` queries Solana Mainnet RPC (`getTransaction`), verifies a finalized payment of at least `$149 USD` in `SOL` or `149 USDC` (`EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`) to `3HvUMCUSSHEdtA35UuD4J7mbgpTxJ7LgT2X7GfdzvBdm`, checks that the on-chain SPL Memo includes `gh:<issue-author-login>`, prevents signature replay across existing issues, and optionally invites the user (`permission: pull`) to the private release repository when `RELEASE_REPO_NAME` (`owner/repo`) and `RELEASE_REPO_PAT` are configured in repository secrets/variables.
