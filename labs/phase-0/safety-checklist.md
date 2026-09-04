# Phase 0 Safety Checklist

Last updated: 2026-09-04

Complete this before any practical lab beyond harmless host inspection.

## System Boundaries

| Item | Learner Response | Verified |
|---|---|---|
| Primary host operating system | EndeavourOS | Yes (verified via `/etc/*-release`) |
| Host is daily-use system | Yes | Yes |
| Disposable Arch VM exists | virt-manager installed | In progress (VM creation pending) |
| VM snapshot capability exists | Supported by QEMU/KVM | Pending verification in lab |
| Docker is installed and usable | Yes | Yes (hello-world ran successfully) |
| Backup strategy for important host data exists | Unknown | No |

## Safety Rules

- Do not run destructive experiments on the EndeavourOS host.
- Treat commands that modify partitions, boot, services, packages, ownership, permissions, networking, or system directories as high-risk until classified.
- Redact secrets from all evidence.
- Prefer read-only inspection commands on the host during early phases.
- Use a disposable VM for boot, partitioning, filesystem damage, package recovery, systemd breakage, networking breakage, and permission-disaster labs.

## Pre-Lab Gate

Before a dangerous exercise, answer:

```text
TARGET TYPE:
TARGET NAME:
WHY THIS TARGET IS SAFE:
SNAPSHOT OR RECOVERY PATH:
DAMAGE CATEGORY:
COMMANDS OR ACTIONS THAT ARE PROHIBITED:
HOW SUCCESS WILL BE VERIFIED:
```

## Phase 0 Status

Safety gate status: In Progress (Host & Docker confirmed; VM lab setup and host backup verification pending).

