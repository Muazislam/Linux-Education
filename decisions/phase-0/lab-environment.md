# Phase 0 Lab Environment Decision

Last updated: 2026-09-04

## Decision Status

Decided.

## Context

The learner uses EndeavourOS as the primary host. Dangerous Linux labs must not target the host. The curriculum requires a disposable Arch VM for system-level break/fix work and Docker for application/infrastructure experiments.

## Options

| Option                | Best For                              | Tradeoffs                                     |
| --------------------- | ------------------------------------- | --------------------------------------------- |
| GNOME Boxes           | Simple VM workflow                    | Less advanced control                         |
| VirtualBox            | Familiar cross-platform VM management | Separate kernel modules and guest tooling     |
| virt-manager/QEMU/KVM | Strong Linux-native virtualization    | Slightly more setup complexity                |
| Other                 | Existing learner preference           | Must still support snapshots or easy rebuilds |

## Decision Record

```text
DATE: 2026-09-04
CHOSEN VM TOOL: virt-manager / QEMU / KVM
WHY: Linux-native, high performance, robust snapshot support, installed on host.
DOCKER STATUS: Installed and verified functional (ran hello-world container).
HOST BACKUP STATUS: Pending verification before destructive labs.
WEEKLY TIME BUDGET: ~20 hours/week (flexible based on full-stack web dev load).
OPEN QUESTIONS: Snapshot configuration and virtual networking setup in virt-manager.
Risk lab-environment: Disposable Arch VM**  Full‑risk labs (disk, boot, systemd).
```

## Next Action

Complete Phase 0 baseline diagnostic and verify disposable Arch VM setup.
