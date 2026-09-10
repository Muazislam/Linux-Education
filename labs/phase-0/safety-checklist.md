# Phase 0 Safety Checklist

Last updated: 2026-09-04

Complete this before any practical lab beyond harmless host inspection.

## System Boundaries

| Item                                           | Learner Response                                                                                                             | Verified                            |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| Primary host operating system                  | EndeavourOS                                                                                                                  | Yes (verified via `/etc/*-release`) |
| Host is daily‑use system                       | Yes                                                                                                                          | Yes                                 |
| Disposable Arch VM exists                      | VirtualBox VM **arch‑lab‑01** (Arch 7.2.4‑arch1‑2) boots to a root login prompt                                              | Yes                                 |
| VM snapshot capability exists                  | VirtualBox snapshot **phase‑0‑base** created and successfully restored (`VBoxManage snapshot arch‑lab‑01 take phase‑0‑base`) | Yes                                 |
| Docker is installed and usable                 | Docker engine installed, `docker run hello‑world` succeeded                                                                  | Yes                                 |
| Backup strategy for important host data exists | rsync script copying `$HOME/Documents` (and test data) to USB; first run on 2026‑09‑10                                       | Yes                                 |

## Safety Rules

- Do not run destructive experiments on the EndeavourOS host.
- Treat commands that modify partitions, boot, services, packages, ownership, permissions, networking, or system directories as high‑risk until classified.
- Redact secrets from all evidence.
- Prefer read‑only inspection commands on the host during early phases.
- Use a disposable VM for boot, partitioning, filesystem damage, package recovery, systemd breakage, networking breakage, and permission‑disaster labs.

## Pre‑Lab Gate

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

Safety gate status: **Done** – Host & Docker confirmed; VM lab setup and host backup verified.
