# Contributing to FluxaPay

Thank you for contributing! Please follow these guidelines to keep the codebase healthy and the CI green.

---

## Prerequisites

- **Node.js ≥ 20** (managed via `.nvmrc` / `nvm`)
- **Docker** (for running local Postgres)
- **actionlint** — for validating GitHub Actions workflow files locally

---

## Setting up locally

```bash
git clone https://github.com/adams813/fluxapay.git
cd fluxapay
npm install
```

---

## Linting GitHub Actions workflows

We use [actionlint](https://github.com/rhysd/actionlint) to keep workflow files correct.

> **Important:** Do **not** commit the `actionlint` binary to the repository.
> The binary is listed in `.gitignore` (`/actionlint`).
> CI installs it automatically via the pinned [`rhysd/actionlint@v1`](https://github.com/rhysd/actionlint) action.

### Install actionlint locally

**macOS (Homebrew)**

```bash
brew install actionlint
```

**Linux / Windows (manual download)**

```bash
bash <(curl https://raw.githubusercontent.com/rhysd/actionlint/main/scripts/download-actionlint.bash)
# Move the downloaded binary somewhere on your PATH, e.g.:
mv actionlint ~/.local/bin/
```

> After installation you can verify with: `actionlint --version`
> The downloaded binary should **not** be placed in the repository root.

### Run locally

```bash
actionlint
```

This will lint all files under `.github/workflows/`.

---

## Running tests

```bash
# Backend unit tests
cd fluxapay_backend && npm test

# TypeScript SDK tests
cd fluxapay_sdk && npm test
```

---

## Pull Request checklist

- [ ] `npm run lint` passes (or `npm run build` for the SDK)
- [ ] All existing tests pass
- [ ] New behaviour is covered by tests
- [ ] No platform-specific binaries committed to the repository
- [ ] Workflow files pass `actionlint` locally
