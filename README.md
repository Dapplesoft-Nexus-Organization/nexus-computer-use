# Nexus Computer-Use & Sandbox Engine

Isolated, snapshot-enabled environments providing safe compute sandboxes for agent actions.

## Sandboxing Tiers
- **E0 (Ephemeral Sandbox):** Isolated Docker/containerd micro-environments for read-only evaluations.
- **E1 (Lab VM):** Full Windows/Linux KVM images featuring snapshot/revert capabilities and interactive screen streaming.
- **Network Guard:** Outbound proxy with strict domain allowlisting preventing data leakage.

## Directory Structure
```text
nexus-computer-use/
├── sandboxes/
│   ├── e0-docker/
│   └── e1-qemu-vm/
├── browser-runner/
└── network-guard/
```
