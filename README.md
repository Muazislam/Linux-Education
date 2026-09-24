# Linux / Arch Engineering Learning Repository

![Linux](https://img.shields.io/badge/OS-Linux-informational?style=flat-square)
![Arch](https://img.shields.io/badge/Distro-Arch%20Linux-1793D1?style=flat-square)
![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?style=flat-square)
![Docker](https://img.shields.io/badge/Container-Docker-2496ED?style=flat-square)
![QEMU/KVM](https://img.shields.io/badge/Virtualization-QEMU%2FKVM-FF6600?style=flat-square)
![Status](https://img.shields.io/badge/Status-Phase%201%20Ready-brightgreen?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

> A persistent, evidence-backed, long-term learning system and engineering portfolio for Linux, Unix, systems administration, troubleshooting, and Arch Linux.

---

## Table of contents

- [Linux / Arch Engineering Learning Repository](#linux--arch-engineering-learning-repository)
  - [Table of contents](#table-of-contents)
  - [Overview](#overview)
  - [Author \& Learner Profile](#author--learner-profile)
  - [Core Philosophy](#core-philosophy)
    - [Instructional Progression](#instructional-progression)
    - [Hint Independence Scale (H0–H7)](#hint-independence-scale-h0h7)
    - [Mastery Scale (L0–L7)](#mastery-scale-l0l7)
    - [Error Classification](#error-classification)
  - [Lab Architecture \& Safety Gate](#lab-architecture--safety-gate)
  - [Curriculum Roadmap (Phases 0–17)](#curriculum-roadmap-phases-017)
  - [Primary Reference Sources](#primary-reference-sources)
  - [Sample Evidence \& Terminal Practice](#sample-evidence--terminal-practice)
  - [Repository Structure](#repository-structure)
  - [How to Use / AI Instructor Workflow](#how-to-use--ai-instructor-workflow)
  - [Current Status \& Active Milestone](#current-status--active-milestone)
  - [Feedback \& Discussions](#feedback--discussions)
  - [License](#license)

---

## Overview

This repository is a structured, long-term learning system for building real systems-engineering competence — not a collection of notes copied from tutorials.

It functions as part curriculum, part lab notebook, and part engineering portfolio. Every phase produces persistent artifacts — logs, command outputs, diagnostic evidence, architectural decisions, and error post-mortems — proving that skills are built through hands-on verification.

---

## Author & Learner Profile

- **Engineer:** Muaz Islam ([@muazislambabar](https://github.com/muazislambabar))
- **Primary Focus:** Full-Stack Web Development (React, Node.js, Express, Databases, Cloud/APIs).
- **Linux Track:** Secondary, serious systems-engineering track dedicated to building deep Linux and Arch Linux proficiency (from command-line mastery and shell scripting to kernel/boot recovery, Docker infrastructure, systemd administration, and independent Arch Linux maintenance).
- **Time Commitment:** ~20 hours/week dedicated to Linux practice and labs.

---

## Core Philosophy

- **Competence over memorization.** The goal is the ability to reason about a broken system from first principles, not reciting command flags from memory.
- **"Don't administer by coincidence."** (Adapted from _The Pragmatic Programmer_'s "Don't Program by Coincidence" rule). If a command or fix works without an understanding of _why_, it is not complete.
- **No topic is "complete" from reading alone.** Every milestone requires demonstrated terminal evidence, root-cause analysis, and verification.
- **Socratic instruction by default.** The instructor (human mentor or AI) guides through targeted inquiry rather than handing over direct answers.

### Instructional Progression

```text
CONCEPT → EXPLANATION → GUIDED PRACTICE → INDEPENDENT EXERCISE → LAB
   → FAILURE SCENARIO → TROUBLESHOOTING → RECOVERY → ASSESSMENT → MASTERY
```

### Hint Independence Scale (H0–H7)

Tracks how much assistance was required to solve a problem, logged over time to ensure decreasing hint dependence and increasing engineering autonomy.

| Level  | Name                     | Definition                                                                                          |
| :----- | :----------------------- | :-------------------------------------------------------------------------------------------------- |
| **H0** | **Independent**          | Solved with zero assistance; learner proceeds independently.                                        |
| **H1** | **Clarifying Question**  | Socratic question prompting the learner to re-read output or clarify objectives.                    |
| **H2** | **Conceptual Hint**      | High-level conceptual explanation without naming commands.                                          |
| **H3** | **Subsystem Hint**       | Identifies the involved subsystem (e.g., storage, networking, permissions, systemd).                |
| **H4** | **Diagnostic Direction** | Recommends an investigation strategy or inspection path (e.g., check `dmesg`, `journalctl`, `man`). |
| **H5** | **Tool Category**        | Points to the command or utility family (e.g., `ip`, `ss`, `systemctl`, `chmod`).                   |
| **H6** | **Procedural Guidance**  | Provides sequential steps or syntax structure without giving the full answer.                       |
| **H7** | **Explicit Solution**    | Direct command or solution provided (triggers follow-up remediation).                               |

### Mastery Scale (L0–L7)

| Level  | Meaning                  | Evidence Requirement                                            |
| :----- | :----------------------- | :-------------------------------------------------------------- |
| **L0** | Unfamiliar               | No prior knowledge or unverified claim.                         |
| **L1** | Can recognize            | Identifies terminology and syntax when seen.                    |
| **L2** | Can explain              | Explains how the subsystem works in plain language.             |
| **L3** | Guided performance       | Executes correctly with documentation or hints.                 |
| **L4** | Independent performance  | Executes and verifies without hints.                            |
| **L5** | Can troubleshoot         | Diagnoses unexpected failures in the subsystem.                 |
| **L6** | Can recover from failure | Restores system state after catastrophic failure or corruption. |
| **L7** | Can teach / mentor       | Teaches and defends architectural choices to another engineer.  |

### Error Classification

Every error is analyzed and categorized to identify recurring anti-patterns:

`Command` · `Conceptual` · `Diagnostic` · `Reasoning` · `Safety` · `Documentation` · `Verification` · `Procedural` · `Architectural`

---

## Lab Architecture & Safety Gate

Destructive, break-fix learning requires a well-defined blast radius. The environment is split into three tiers of increasing risk tolerance:

```text
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│       HOST SYSTEM       │      │   DOCKER ENVIRONMENT    │      │   DISPOSABLE ARCH VM    │
│      (EndeavourOS)      │ ───► │      (containers)       │ ───► │   (virt-manager / KVM)  │
│                         │      │                         │      │                         │
│  Daily driver.          │      │  App infra, backend     │      │  Destructive            │
│  Safe CLI navigation,   │      │  processes, DBs,        │      │  experiments:           │
│  man/info research,     │      │  reverse proxies,       │      │  partitioning, FS       │
│  non-destructive        │      │  container lifecycle,   │      │  corruption, systemd    │
│  inspection only.       │      │  volumes, networking.   │      │  failure, bootloader/   │
│                         │      │                         │      │  initramfs breakage,    │
│                         │      │                         │      │  live recovery drills.  │
└─────────────────────────┘      └─────────────────────────┘      └─────────────────────────┘
        LOW RISK                       CONTAINED RISK                 FULL DESTRUCTIVE RISK
```

| Tier       | Environment                                                | Target & Scope                                                                                                                                         |
| :--------- | :--------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tier 1** | **Host System** (EndeavourOS)                              | Daily driver; safe CLI navigation, documentation research (`man`, `info`, `--help`), and read-only inspection.                                         |
| **Tier 2** | **Docker Environment**                                     | Application infrastructure, backend services (Node.js, Postgres, Redis, Nginx), container lifecycles, and isolated bridge networks.                    |
| **Tier 3** | **Disposable Arch Linux VM** (`virt-manager` / QEMU / KVM) | Destructive break-fix labs — disk partitioning, filesystem corruption, systemd unit breakage, kernel/initramfs recovery, and emergency chroot repairs. |

> [!IMPORTANT]
> **Host Safety Rule:** If an operation carries a non-zero risk of breaking boot, networking, partitions, or system files, it is strictly forbidden on the host and must run in a disposable VM with a verified snapshot.

---

## Curriculum Roadmap (Phases 0–17)

| Phase  | Title                           | Focus & Core Competencies                                                                                  |
| :----: | :------------------------------ | :--------------------------------------------------------------------------------------------------------- |
| **0**  | **Environment & Baseline**      | Lab safety boundaries, evidence formats, baseline diagnostic assessment.                                   |
| **1**  | **Unix/Linux Mental Model**     | Kernel vs userspace, filesystem hierarchy standard, processes, streams, user space.                        |
| **2**  | **Shell & CLI Workflow**        | Command expansion, quoting rules, streams, redirection, pipelines, exit codes (`$?`).                      |
| **3**  | **Text Processing & Wrangling** | `grep`, `sed`, `awk`, `find`, `xargs`, log parsing, regex, local man pages.                                |
| **4**  | **Filesystems & Permissions**   | POSIX permissions, ownership (`chown`/`chmod`), `umask`, SUID/SGID, sticky bit, `sudo`.                    |
| **5**  | **Processes & Observability**   | Process trees, `ps`, `top`/`htop`, signals (`SIGTERM`, `SIGKILL`), background jobs, `/proc`.               |
| **6**  | **Arch Package Management**     | `pacman`, official mirrors, cache management, package signing, AUR, PKGBUILD, `makepkg`.                   |
| **7**  | **systemd & Services**          | Unit files, service lifecycle, targets, systemd timers, journald structured logging.                       |
| **8**  | **Networking & Remote Access**  | IP routing, DNS resolution, TCP/UDP sockets (`ss`/`ip`), SSH keys & hardening, firewalling.                |
| **9**  | **Storage & Backups**           | Block devices (`lsblk`), partitioning (`fdisk`/`parted`), ext4/Btrfs, `/etc/fstab`, backup/restore drills. |
| **10** | **Boot & System Recovery**      | UEFI, bootloader (`systemd-boot`/GRUB), initramfs (`mkinitcpio`), kernel parameters, live USB `chroot`.    |
| **11** | **Security & Hardening**        | Least privilege, file integrity, SSH hardening, network exposure, audit tools, OWASP overlap.              |
| **12** | **Defensive Automation**        | Robust Bash scripting (`set -euo pipefail`), idempotence, validation, scheduled jobs.                      |
| **13** | **Virtualization Lab Ops**      | QEMU/KVM with `virt-manager`, snapshots, bridge networking, reproducible testbeds.                         |
| **14** | **Docker for Full-Stack**       | Multi-stage Dockerfiles, Compose, bind mounts vs volumes, container networking, debugging.                 |
| **15** | **Arch Administration**         | Clean Arch install from scratch in VM, post-install setup, maintenance procedures.                         |
| **16** | **Break-Fix Troubleshooting**   | SadServers-style incident scenarios, mystery failure diagnosis, root-cause analysis (RCA).                 |
| **17** | **Capstone Practical Exam**     | Fresh unconfigured VM, multi-point cascading failure injection, recovery, and technical defense.           |

---

## Primary Reference Sources

This curriculum is grounded in primary, authoritative documentation over secondary tutorials:

- **Arch Linux:**
  - [ArchWiki Main Page](https://wiki.archlinux.org/)
  - [Arch Installation Guide](https://wiki.archlinux.org/title/Installation_guide)
  - [General Recommendations](https://wiki.archlinux.org/title/General_recommendations)
  - [System Maintenance](https://wiki.archlinux.org/title/System_maintenance)
  - [Arch System Administration Category](https://wiki.archlinux.org/title/Category:System_administration)
- **Linux Core & Kernel:**
  - [Linux Kernel Official Documentation](https://docs.kernel.org/)
  - [systemd System and Service Manager](https://systemd.io/)
  - [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/)
- **Developer & Educational Resources:**
  - [MIT Missing Semester of Your CS Education (2026)](https://missing.csail.mit.edu/2026/)
  - [The Linux Command Line by William Shotts (TLCL)](https://linuxcommand.org/tlcl.php)
  - [SadServers — Linux Troubleshooting Scenarios](https://sadservers.com/)
  - [Docker Documentation](https://docs.docker.com/)

---

## Sample Evidence & Terminal Practice

Real evidence submitted during Phase 0 baseline assessment demonstrating command inspection and understanding:

```bash
# Investigating operating system distribution release safely
$ cat /etc/*-release
DISTRIB_ID="EndeavourOS"
DISTRIB_RELEASE="rolling"
PRETTY_NAME="EndeavourOS"
ID="endeavouros"
ID_LIKE="arch"

# Disambiguating kernel build timestamp vs exact kernel release version via `man uname`
$ uname -v
#1 SMP PREEMPT_DYNAMIC Fri, 28 Aug 2026 03:36:07 +0000

$ uname -r
7.1.11-arch1-1
```

_Lesson Logged:_ Shell arguments are whitespace-sensitive (e.g. `cat /etc/* -release` treats `-release` as an invalid option flag `-r`, whereas `cat /etc/*-release` properly expands file globs).

---

## Repository Structure

```text
.
├── instructor/        # System bootstrap, AI behavioral contract, chat interface, state tracking
├── curriculum/        # Master roadmap (roadmap.md), competency map, and phase plans
├── modules/           # In-depth module plans and lesson exercises
├── progress/          # Competency matrix (competencies.md), milestone tracker, hint logs
├── labs/              # Objective-based lab definitions, safety checklists, lab architecture
├── assessments/       # Baseline diagnostic, module exams, and practical scorecards
├── evidence/          # Raw command outputs, terminal logs, reasoning proof
├── learning-log/      # Daily/weekly study logs and session retrospectives
├── mistakes/          # Classified error logs (ERROR_LOG.md) and root-cause analyses
├── troubleshooting/   # Incident post-mortems (INCIDENT_TEMPLATE.md) and diagnostic patterns
├── knowledge/         # Mental models, concept deep-dives, documentation research summaries
├── decisions/         # Durable engineering and architectural decision records
├── remediation/       # Targeted drill plans for observed weaknesses
├── retrospectives/    # Weekly and periodic meta-learning reflections
└── scripts/           # Helper scripts and automation tooling
```

---

## How to Use / AI Instructor Workflow

1. **Bootstrap:** The AI instructor reads `INSTRUCTOR_PROTOCOL.md` and `instructor/BOOTSTRAP.md` to load the behavioral contract, then checks `instructor/CURRENT_STATE.md`.
2. **Orient:** Cross-reference `progress/progress.md`, `progress/competencies.md`, and the active phase in `curriculum/phases/`.
3. **Interact:** The learner drives sessions naturally or using optional shorthand commands:
   - `/status` — Summarize active phase, competencies, and open weaknesses.
   - `/learn` — Start a new concept with Socratic inquiry.
   - `/practice` — Assign a hands-on terminal exercise with constraints.
   - `/lab` — Start or verify an objective-based lab.
   - `/troubleshoot` — Enter an incident break-fix scenario.
   - `/quiz` — Test diagnostic and conceptual reasoning.
4. **Log & Verify:** All work is recorded in `evidence/`, `learning-log/`, and `progress/`. No progress is marked without verified output.

---

## Current Status & Active Milestone

- **Current Phase:** Phase 0 — Environment Setup, Safety & Baseline Diagnostic
- **Active VM Tool:** `virt-manager` / QEMU / KVM (Installed on EndeavourOS host)
- **Docker Lab:** Installed and verified functional (`hello-world` test passed)
- **Baseline Diagnostic Progress:** Task D1 (Orientation) completed; Tasks D2–D7 in progress.
- **Weekly Commitment:** ~20 hours/week.

---

## Feedback & Discussions

This is a personal, evidence-backed learning repository and engineering portfolio. 
- **Contributions:** Pull requests directly altering the learning records are not accepted, as this repository tracks individual learning progression.
- **Feedback & Reuse:** If you have suggestions or want to adapt this repository architecture/templates for your own learning journey, you are free to fork it, and feedback/discussions are warmly welcomed via [GitHub Issues](https://github.com/muazislambabar)!

---

## License

This repository and its curriculum templates are licensed under the [MIT License](LICENSE). See the [LICENSE](LICENSE) file for full details and copyright information.

---

_Last updated: 2026-09-06_
