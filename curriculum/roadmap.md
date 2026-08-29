# Linux / Arch Engineering Curriculum Audit

Last updated: 2026-08-26

This roadmap contains the first-session curriculum audit and proposed architecture. It is not a lesson. The learner should review this architecture before Module 1 begins.

## A. Executive Summary

This curriculum treats Linux competence as an engineering capability, not a command list. It integrates MIT Missing Semester 2026 as a primary educational spine, adds missing Linux administration and recovery competencies from ArchWiki and official documentation, and uses labs to require evidence before mastery is recorded.

The workload must remain secondary to full-stack development. Recommended baseline: 3 to 5 hours per week, with occasional 6 to 8 hour weeks for major labs or recovery exams.

## 1. Source Inventory

Primary/official sources:

- ArchWiki main page: https://wiki.archlinux.org/
- Arch Installation Guide: https://wiki.archlinux.org/title/Installation_guide
- Arch General Recommendations: https://wiki.archlinux.org/title/General_recommendations
- Arch System Maintenance: https://wiki.archlinux.org/title/System_maintenance
- Arch System Administration category: https://wiki.archlinux.org/title/Category:System_administration
- Arch Linux official site and package documentation: https://archlinux.org/
- Linux kernel documentation: https://docs.kernel.org/
- systemd documentation: https://systemd.io/
- Docker documentation: https://docs.docker.com/
- OWASP for web application security overlap: https://owasp.org/
- Local man pages, info pages, command `--help`, and configuration examples.

High-quality educational sources:

- MIT Missing Semester 2026: https://missing.csail.mit.edu/2026/
- MIT Missing Semester historical lectures: data wrangling, security/cryptography, backups, automation, machine introspection, OS customization, web/browsers, security/privacy.
- The Linux Command Line: https://linuxcommand.org/tlcl.php
- Linux Upskill Challenge: https://github.com/livialima/linuxupskillchallenge
- SadServers scenarios for troubleshooting practice: https://github.com/SadServers/sadservers and https://sadservers.com/scenarios

Secondary/topic-discovery source:

- Mikeroyal Arch Linux Guide: https://github.com/mikeroyal/Arch-Linux-Guide. Use for breadth discovery only, not as final authority.

## Source Verification Note

The initial audit was prepared on 2026-08-26. Current web checks confirmed the MIT Missing Semester 2026 lecture list, the role of ArchWiki General Recommendations as a post-installation index, and the continuing availability of SadServers troubleshooting scenarios. Future instructors should re-check living documentation when a module depends on current commands, package behavior, or installation guidance.

## 2. Source Authority Hierarchy

1. Official documentation, standards, man pages, ArchWiki, Arch Linux official site.
2. MIT Missing Semester and established educational resources.
3. Practice platforms such as SadServers.
4. Community guides and secondary summaries.
5. AI-generated explanations or random web content, only after verification.

## 3. Curriculum Gaps

MIT Missing Semester is excellent for developer tooling but does not fully cover:

- Arch installation and administration;
- pacman/AUR/PKGBUILD competence;
- systemd administration in depth;
- bootloader/initramfs/recovery;
- partitioning, filesystems, fstab, storage failure;
- structured network diagnosis;
- security hardening for a personal Linux system;
- backup restore drills;
- VM-based failure recovery;
- long-term progress tracking and mastery assessment.

These gaps are covered through ArchWiki, official docs, lab work, and failure scenarios.

## 4. Duplicate Topics

The following overlap and should be consolidated instead of repeated:

- shell basics: MIT 2026 shell + The Linux Command Line;
- command-line environment: MIT 2026 + Unix/Linux fundamentals;
- debugging/profiling: MIT 2026 + Linux observability/performance labs;
- packaging/shipping: MIT 2026 + Docker/deployment modules;
- security: MIT historical security + OWASP + Linux security basics;
- automation: MIT historical automation + shell scripting + systemd timers;
- data wrangling: MIT historical data wrangling + command-line tooling.

## 5. Recommended Additional Sources

No large additional source set is necessary now. Add narrowly when a module requires it:

- OpenSSH official documentation for SSH-specific depth.
- GNU Bash manual for advanced shell behavior.
- Filesystem-specific docs for Btrfs/ext4 when storage labs begin.
- QEMU/libvirt or VirtualBox documentation depending on chosen VM tool.

## 6. Competency Dependency Graph

```text
environment safety
  -> shell navigation
  -> files, paths, stdin/stdout/stderr
  -> pipelines, redirection, exit status
  -> text processing and data wrangling

files and users
  -> ownership, permissions, groups
  -> privilege, sudo, secrets
  -> application file safety

processes
  -> jobs, signals, process trees
  -> resource inspection
  -> daemons
  -> systemd services
  -> journald and service troubleshooting

storage basics
  -> block devices, partitions, filesystems
  -> mounts, fstab, disk/inode exhaustion
  -> backups, snapshots, restore
  -> boot and recovery

network fundamentals
  -> interfaces, IP, routing, DNS
  -> TCP/UDP, ports, sockets
  -> SSH, HTTP, firewalls
  -> network troubleshooting

package management
  -> pacman repositories and upgrades
  -> package cache, mirrors, verification
  -> AUR concepts
  -> PKGBUILD and makepkg

developer operations
  -> Node processes, env vars, ports, logs
  -> Docker images/containers/volumes/networks
  -> deployment concepts
  -> system maintenance

all core domains
  -> break-fix labs
  -> integration labs
  -> final Arch practical exam
```

## 7. Proposed Curriculum Phases

Phase 0 - Environment, safety, repository protocol, baseline assessment. Active plan: `curriculum/phases/phase-0.md`.

Phase 1 - Unix/Linux mental model: kernel/userspace, files, processes, streams, users.

Phase 2 - Shell and command-line workflow: navigation, expansion, quoting, redirection, pipelines, exit codes.

Phase 3 - Text processing and documentation use: grep, sed, awk, find, xargs, logs, man pages.

Phase 4 - Filesystems, permissions, and users: hierarchy, ownership, groups, sudo, links, temporary files.

Phase 5 - Processes and observability: ps, pstree, top/htop, signals, jobs, resource evidence.

Phase 6 - Package management on Arch: pacman, repositories, mirrors, upgrades, cache, package trust.

Phase 7 - systemd and logs: units, services, targets, enable/start, dependencies, journald, timers.

Phase 8 - Networking and SSH: interfaces, IP, routing, DNS, ports, sockets, firewall concepts, remote access.

Phase 9 - Storage, backups, and restore: disks, partitions, filesystems, mounts, swap, backup strategy, restore verification.

Phase 10 - Boot and recovery: UEFI, bootloader, kernel, initramfs, systemd boot path, live recovery.

Phase 11 - Security: least privilege, SSH hardening, updates, package trust, secrets, OWASP overlap.

Phase 12 - Automation: defensive Bash, idempotence, scheduled tasks, systemd timers, script review.

Phase 13 - Virtualization lab operations: disposable VMs, snapshots, virtual networking, recovery drills.

Phase 14 - Docker for developers: images, containers, Dockerfile, Compose, volumes, networks, logs, security boundaries.

Phase 15 - Arch administration integration: install reasoning, post-install configuration, maintenance, AUR prerequisites.

Phase 16 - Troubleshooting/break-fix progression: SadServers-style failures and local disposable VM scenarios.

Phase 17 - Final Arch practical examination: fresh VM, objectives only, multiple unknown failures, recovery and explanation.

## 8. Required Lab Environments

Host:

- EndeavourOS daily system.
- Used for safe command-line exercises, documentation reading, development workflow, and repository records.

Docker lab:

- Used for Node, databases, web servers, local infrastructure, container lifecycle, logs, volumes, networking, and Compose.

Disposable Arch VM:

- Used for partitioning, filesystems, boot, initramfs, systemd failure, package recovery, networking breakage, permission disasters, recovery drills.

Optional comparison VM:

- Debian/Ubuntu or another distribution for transfer and contrast after fundamentals are stable.

## 9. VM Strategy

Use a disposable Arch VM for dangerous or system-level labs. Each destructive lab must verify:

- correct target environment;
- snapshot exists when appropriate;
- recovery path is known;
- learner understands simulated damage category;
- host system is not the target.

VM tooling remains unresolved. Choose based on the learner's machine and comfort: GNOME Boxes, VirtualBox, QEMU/KVM with virt-manager, or another suitable tool.

## 10. Docker Strategy

Docker is a related engineering track, not a substitute for VMs. Use Docker for application and infrastructure experiments. Do not use Docker for bootloader, kernel/initramfs, partitioning, or full-system recovery labs.

## 11. Safety Strategy

Before dangerous work:

1. Identify HOST, LAB VM, CONTAINER, or REMOTE SYSTEM.
2. Confirm disposability.
3. Explain simulated damage.
4. Require snapshot or backup when appropriate.
5. Define allowed and prohibited actions.
6. Require evidence and verification.

## 12. Assessment Strategy

Assessment types:

- micro-assessments after individual concepts;
- module assessments after competency groups;
- integration labs combining several subsystems;
- failure recovery exams with incomplete problem statements;
- final practical exam in a fresh disposable Arch VM.

Every assessment records evidence, hint level, outcome, reasoning, safety, verification, and mastery implication.

## 13. Progress-Tracking Architecture

Core files:

- `progress/progress.md` - current phase/module/task and session history.
- `progress/competencies.md` - mastery levels and evidence.
- `progress/weaknesses.md` - recurring weaknesses and remediation.
- `curriculum/phases/` - implementation plan and exit criteria for each phase.
- `learning-log/` - session records.
- `evidence/` - command output, logs, configs, scripts, screenshots, or written reasoning.
- `labs/` - lab definitions and submitted lab reports.
- `assessments/` - formal assessment records.
- `mistakes/` - classified errors.
- `troubleshooting/` - incident and break-fix records.

## 14. Estimated Weekly Workload

Default: 3 to 5 hours per week.

Suggested split:

- 1 hour documentation/concept work;
- 1 to 2 hours guided or independent command-line practice;
- 1 to 2 hours lab/troubleshooting or full-stack integration;
- 15 minutes progress reflection.

Heavy lab weeks may temporarily reach 6 to 8 hours. Avoid sustained overload because full-stack development is the primary career track.

## 15. Relationship To MIT Missing Semester 2026

MIT Missing Semester 2026 is a primary component, especially for shell, command-line environment, development tools, debugging/profiling, Git, packaging/shipping, agentic coding, beyond-code engineering, and code quality.

It is not replaced. It is integrated into a broader Linux administration and recovery curriculum.

## 16. Historical Missing Semester Topics Worth Integrating

Integrate:

- Data Wrangling: essential for logs, text processing, evidence extraction.
- Security and Cryptography: important for SSH, secrets, package trust, web security foundations.
- Backups: essential; include restore drills.
- Automation: important; integrate with Bash and systemd timers.
- Machine Introspection: essential for observability and debugging.
- OS Customization: supplementary; teach only after safety and recovery basics.
- Web and Browsers: supplementary/important for full-stack integration.
- Security and Privacy: important but scoped to practical threat modeling and safe defaults.

Do not teach every historical lecture in full. Use them where they fill gaps or reinforce competencies.

## 17. Arch-Specific Topics

- Arch installation concepts.
- pacman, repositories, mirrors, package cache, package signing.
- rolling release maintenance.
- ArchWiki navigation and interpretation.
- system maintenance.
- AUR concepts only after package/build prerequisites.
- PKGBUILD and makepkg.
- bootloader/initramfs choices in Arch context.
- EndeavourOS vs Arch distinctions.

## 18. Linux-General Topics

- Unix philosophy and system model.
- filesystems, permissions, users, groups.
- processes, signals, jobs.
- systemd concepts that transfer to systemd-based distributions.
- networking fundamentals.
- logs and observability.
- storage and backup principles.
- security and least privilege.
- automation and defensive scripting.
- troubleshooting methodology.

## 19. Troubleshooting Progression

Level 1: explain expected vs actual behavior.

Level 2: collect evidence with guided questions.

Level 3: distinguish likely subsystems.

Level 4: form and test hypotheses independently.

Level 5: repair and verify constrained failures.

Level 6: recover from realistic multi-step failures in disposable VMs.

Level 7: teach the diagnosis and justify the fix to another engineer.

## 20. Final Mastery Criteria

The learner can demonstrate:

- independent Arch installation and post-install configuration in a VM;
- safe system maintenance and package management;
- competent shell and documentation workflow;
- diagnosis of unknown service, network, storage, permission, package, and boot failures;
- repair with minimal blast radius;
- verification after repair;
- backup creation and proven restore;
- appropriate security reasoning;
- clear written RCA and explanation;
- reduced dependence on high-level hints.

No final mastery is granted without direct evidence.
