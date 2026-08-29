# Phase 0 Lab Architecture

Last updated: 2026-08-26

## Host

Purpose:

- daily development;
- safe command-line practice;
- documentation reading;
- repository records;
- non-destructive observation.

Rules:

- no deliberate breakage;
- no blind copy-paste of privileged commands;
- no destructive filesystem, package, boot, or networking exercises.

## Docker Lab

Purpose:

- Node, web servers, databases, application infrastructure;
- containers, images, volumes, networks, logs, ports, environment variables;
- full-stack development support.

Not for:

- bootloader labs;
- kernel/initramfs labs;
- partitioning;
- full-system recovery.

## Disposable Arch VM

Purpose:

- Arch installation reasoning;
- systemd failures;
- package recovery;
- boot and initramfs recovery;
- storage and filesystem labs;
- dangerous permission and networking scenarios.

Required before destructive VM labs:

- clear VM name;
- snapshot or rebuild path;
- no valuable data inside;
- learner can identify host vs VM prompt.

## Optional Comparison VM

Purpose:

- compare distribution differences after fundamentals are stable;
- avoid overfitting Linux knowledge to Arch alone.

## Open Phase 0 Questions

- Which VM tool will be used?
- Is Docker already installed?
- Is hardware virtualization enabled?
- How will host backups be handled?
- How much weekly time is realistic?
