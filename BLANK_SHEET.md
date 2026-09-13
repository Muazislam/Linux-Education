# Blank Sheet / Scratchpad

This file serves as a temporary working sheet during active sessions.
Feel free to draft commands, test snippets, or take quick notes here.

---

### 🎯 Baseline Diagnostic Task D3: Streams and Redirection

(From baseline-diagnostic.md)

In earlier sessions, you completed D1 (Orientation) and D2 (Files & Paths). To finish the baseline evaluation before Phase 1,
we test the core mental model of Linux I/O streams.
──────

### Your Assignment for Task D3:

Please answer the following conceptual questions and provide terminal commands to demonstrate them:

#### 1. Concept Questions (Explain in your own words)

1. In Linux, what are the three standard data streams that every process opens by default? What numbers (file descriptors) are
   assigned to them?
2. What is the fundamental difference between a pipe (|) and an output redirect (>)?
3. What is the difference between > and >> when sending output to a file? What is the risk of using > accidentally?

#### 2. Practical Demonstration (Safe host test)

In your terminal, demonstrate streams and redirection using a temporary file in /tmp (or your home directory):

• Run a command that writes output to a new file using redirection.
• Run a second command that appends a line to that same file.
• Run a command that produces an error (e.g., trying to read a non-existent file) and redirect only the error message into an
error log file, without printing it to your screen.
• View the contents of your files to prove it worked.
──────
Reply with your explanations and the commands/output you tested. (Remember: I'm looking for your reasoning, not memorized
answers!)

stderr (3) - standard I/O streams
stdin (3) - standard I/O streams
stdin (3p) - standard I/O streams
stdout (3) - standard I/O streams
