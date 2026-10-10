# Nexus Computer Use: Gemini & AI Model Guidelines (`GEMINI.md`)

This document is aligned 1:1 with `AGENTS.md`.

## Mandatory Rules Summary
1. **Never Commit / Never Push:** Forbidden for AI. All changes remain locally uncommitted for human review.
2. **Branching:** Branch off `dev` using `feature/<name>`. Never use `feat/`.
3. **Zero Browser Testing:** Forbidden for AI to run browser test agents. Static analysis and unit tests only.
4. **Strict Isolation:** Sandbox egress must be strictly filtered.
5. **Always Update Documentation:** Synchronize `AGENTS.md` and `GEMINI.md` immediately upon code changes.
