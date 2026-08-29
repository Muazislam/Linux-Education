# Phase 0 Safety Checklist

Last updated: 2026-08-26

Complete this before any practical lab beyond harmless host inspection.

## System Boundaries

| Item | Learner Response | Verified |
|---|---|---|
| Primary host operating system | EndeavourOS | Not verified |
| Host is daily-use system | Yes | Not verified |
| Disposable Arch VM exists | Unknown | No |
| VM snapshot capability exists | Unknown | No |
| Docker is installed and usable | Unknown | No |
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

Safety gate status: Not complete.

Reason: disposable VM, snapshot path, Docker state, and backup state are not yet verified.
