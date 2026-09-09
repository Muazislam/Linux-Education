## 🛠️ Recommended Next Tasks (Phase 0)

  Below is a concrete, evidence‑driven workflow you can start right now.
  All commands should be executed on the host system only for read‑only inspection; any
  destructive work must be switched to the disposable VM (Tier 3).

  ### 1️⃣ Choose the Lab Environment (Tier Decision)

  Create a short decision note at decisions/lab-environment.md with one of the three
  options:

    # Lab Environment Decision (Phase 0)
    
    - **Tier 1 – Host System** – *Only safe, read‑only commands.*  
    - **Tier 2 – Docker** – Use containers for isolated services.  
    - **Tier 3 – Disposable Arch VM** – Full‑risk labs (disk, boot, systemd).
    
    **Chosen tier:** Tier 3 – Disposable Arch VM

  │ Why Tier 3?
  │ You plan to practice destructive scenarios (partitioning, boot recovery) that the
  safety
  │ rules explicitly forbid on the host.

  ### 2️⃣ Fill out the Safety Checklist

  Add a file labs/safety-checklist.md (copy the template from labs/template-safety.md if it
  exists) and tick the items that apply to your chosen tier.
  Key points to verify:

  • ✅ Snapshot taken before any destructive lab.
  • ✅ All destructive commands target the VM (virsh, qemu-img, etc.).
  • ✅ Host backups are up‑to‑date.

  ### 3️⃣ Collect Baseline Diagnostic Evidence

  Create a new evidence file: evidence/phase-0/baseline.md.
  Run the following read‑only commands on your EndeavourOS host and paste the output into
  the file under the indicated headings.

   Heading           | Command                          | Purpose
  -------------------|----------------------------------|----------------------------------
   OS Release        | cat /etc/*-release               | Verify distribution and version
   Kernel            | uname -a                         | Full kernel string
   CPU / Memory      | lscpu && free -h                 | Hardware overview
   Disk layout       | lsblk -f                         | List block devices & filesystems
   Filesystem health | df -hT                           | Check mount points & usage
   Systemd status    | systemctl list-units --          | Ensure no failed units
                     | type=service --state=failed      |
   Package integrity | pacman -Qk (or pacman -Qkk)      | Detect missing files
   Network config    | ip addr show && ip route         | Verify interfaces & routing
   Journal snapshot  | journalctl -b -p err --no-pager  | Capture boot‑time errors

  Example snippet to paste:

    ## OS Release

  $ cat /etc/*-release
  ...

    
    (Replace the `...` with the actual output.)
    
    ### 4️⃣ Update Progress Records  
    
    1. Append a new entry to `progress/progress.md` documenting the date, chosen tier, and
  a summary of the collected evidence.  
    2. Mark the Phase 0 milestone as **“In‑Progress – Baseline collected”** (or “Completed”
  once you have all sections).
    
    ### 5️⃣ Verify Completion  
    
    Run a quick checklist script (if you have one in `scripts/check-phase0.sh`) or manually
  confirm that all five items above are present.  
    When satisfied, you can **close Phase 0** by updating:
    
    - `progress/milestones.md` (set Phase 0 status to `DONE`).  
    - `curriculum/phases/phase-0.md` – add a short “exit‑criteria met” note.  
    
    ---  
    
    ## 📢 Next Interaction  
    
    When you have completed the steps above, let me know:
    
    1. **Which tier you chose** (and paste the `lab-environment.md` content).  
    2. **Any issues** you encountered while gathering baseline evidence (e.g., missing
  commands, permission errors).  
    3. **Whether the evidence file** `evidence/phase-0/baseline.md` is ready for review.
    
    Then we can:
    
    - Review the evidence together (Socratic questioning on any surprising output).  
    - Identify any **weaknesses** (`progress/weaknesses.md`) that emerged.  
    - Plan the **first hands‑on lab** for Phase 1 (Unix/Linux mental model).
    
    ---  

    ## ⚡ Helpful Slash Commands  

    - **`/status`** – Summarize the current phase, competencies, and open weaknesses.  
    - **`/learn`** – Start a new concept with Socratic inquiry (e.g., “Explain the Linux
  boot process”).  
    - **`/lab`** – Launch or verify an objective‑based lab (will auto‑check the safety
  tier).  
    - **`/practice`** – Assign a focused terminal exercise (e.g., “list all open sockets”).

    Feel free to use any of these to streamline the workflow, or simply reply with the
  requested artifacts. Happy learning!