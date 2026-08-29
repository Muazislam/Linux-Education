# Phase 0 Lab Environment Decision

Last updated: 2026-08-26

## Decision Status

Not decided.

## Context

The learner uses EndeavourOS as the primary host. Dangerous Linux labs must not target the host. The curriculum requires a disposable Arch VM for system-level break/fix work and Docker for application/infrastructure experiments.

## Options

| Option | Best For | Tradeoffs |
|---|---|---|
| GNOME Boxes | Simple VM workflow | Less advanced control |
| VirtualBox | Familiar cross-platform VM management | Separate kernel modules and guest tooling |
| virt-manager/QEMU/KVM | Strong Linux-native virtualization | Slightly more setup complexity |
| Other | Existing learner preference | Must still support snapshots or easy rebuilds |

## Decision Record

```text
DATE:
CHOSEN VM TOOL:
WHY:
DOCKER STATUS:
HOST BACKUP STATUS:
WEEKLY TIME BUDGET:
OPEN QUESTIONS:
```

## Next Action

Choose VM tool and verify whether Docker is available.
