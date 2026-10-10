# Nexus Computer Use: Master Knowledge Base & Agent Guidelines (`AGENTS.md`)

This document serves as the master reference, binding architectural blueprint, and mandatory instruction set for any AI assistant (Antigravity, Gemini, Cursor, Copilot) and developer working on `nexus-computer-use`.

---

## 1. Universal AI Git & Commit Policy (STRICT - MUST FOLLOW)

### A. Never Commit (`git commit` is FORBIDDEN for AI)
- The AI assistant **MUST NEVER** execute `git commit`.
- All code changes, Dockerfiles, VM definitions, and newly created files must remain **locally uncommitted** in the git working tree.
- The user will personally inspect the diffs, verify all changes in GitHub Desktop / Git CLI, and execute `git commit` manually.

### B. Never Push (`git push` is FORBIDDEN for AI)
- The AI assistant **MUST NEVER** execute `git push` to `origin` or any remote repository.
- Never publish branches or code online to GitHub. All modifications must stay strictly in the local workspace.

### C. Git Branching & Naming Standards
- **Feature Branch Prefix**: MUST use the full prefix **`feature/`** (lowercase), followed by kebab-case (e.g., `feature/e0-docker-sandbox`, `feature/vm-gateway`).
  - **STRICTLY PROHIBITED**: Never use shorthand prefixes like `feat/`. Always use `feature/`.
- **Bugfix Branch Prefix**: Use `fix/<issue-name>` or `feature/<issue-name>`.
- **Base Branch**: Every feature or fix branch MUST branch directly off **`dev`** (never from `main`).
- **Workflow**: Branch off `dev` -> Perform work -> Leave changes uncommitted for user review -> User manually commits -> User pushes to `origin/feature/<branch-name>` -> PR targets `dev`.

### D. Mandatory Self-Updating Documentation Policy (Zero-Forgotten Rule)
- Whenever sandbox configurations, Dockerfiles, or runners are modified, immediately update `AGENTS.md` and `GEMINI.md`.

### E. Mandatory Prohibition on Automated Browser Testing (STRICT ZERO BROWSER TEST RULE)
- **Automated Browser Testing Strictly Forbidden**: Even though this repository builds the browser runtime for the platform, the AI assistant **MUST NEVER** automatically launch browser subagents, headless browsers, or browser-based test sessions (`browser_subagent`, Puppeteer, Playwright).
- **Code-Level Verification Only**: All verification must be performed strictly at the **code level** (Dockerfile linting, unit tests, static analysis).

---

## 2. Directory Structure

```text
nexus-computer-use/
├── sandboxes/
│   ├── e0-docker/              # Ephemeral Docker execution container
│   │   ├── Dockerfile
│   │   └── entrypoint.sh
│   └── e1-vm/                  # QEMU / KVM virtual machine environment
│       ├── cloud-init/
│       └── scripts/
├── runners/
│   ├── browser/                # Secure sandboxed Playwright runner
│   └── desktop/                # X11 / Wayland VNC capture stream
└── gateway/                    # Network egress security filtering
```

---

## 3. Principles Transferred from eShop & SRV

1. **Security & Sandbox Isolation**:
   - Sandboxes must be completely isolated from production host networks. Egress traffic must be filtered to prevent unauthorized outbound connections.
2. **Zero Plaintext Secrets**:
   - Sandboxes must receive short-lived credentials dynamically; no static secrets or tokens embedded in container images.
3. **Immutability & Ephemeral Teardown**:
   - Sandbox environments must be ephemeral and cleanly torn down after each execution, leaving zero residual state.

---

*Authorized by Dapplesoft Architecture & Nexus Governance Council*
