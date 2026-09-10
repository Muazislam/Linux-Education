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
DATE: 2026-09-10 (Amended from 2026-09-04)
CHOSEN VM TOOL: Oracle VirtualBox
VM NAME: arch-lab-01 (Arch Linux 7.2.4-arch1-2, headless/CLI tty1)
SNAPSHOT VERIFIED: Yes (snapshot 'phase-0-base' created, modified root state tested, snapshot reverted and verified)
WHY: Selected to avoid complex host firewall/networking changes required by QEMU/KVM while ensuring isolated, disposable sandbox with instant snapshot restoration for high-blast-radius experiments.
DOCKER STATUS: Installed and verified functional (ran hello-world container).
HOST BACKUP STATUS: Verified via rsync to USB drive (partitioned ext4, tested dry-run with node_modules exclusion, real mirror executed).
WEEKLY TIME BUDGET: ~20 hours/week (flexible based on full-stack web dev load).
RISK CLASSIFICATION: Disposable Arch VM dedicated to Tier 3 full-risk labs (disk partitioning, boot recovery, systemd breakage).
```

## Next Action

Proceed to Phase 0 baseline assessment completion (Tasks D3–D7) or transition to Phase 1 (Unix/Linux Mental Model).
