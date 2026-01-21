# Linux Security Primitives

## Purpose

This document summarizes the core Linux security primitives encountered and
applied during the Snow-Crash assessment.

Rather than focusing on exploitation steps, this appendix documents the
underlying system mechanisms that govern privilege, execution, and trust
boundaries in Unix-like operating systems.

Understanding these primitives is fundamental to both offensive security
testing and defensive system hardening.

---

## User and Group Model

Linux enforces access control through:
- User IDs (UID)
- Group IDs (GID)
- Supplementary group memberships

Each process executes with:
- A **real UID** (the invoking user)
- An **effective UID** (used for permission checks)

Misalignment between these identifiers can introduce privilege escalation risks
when not carefully controlled.

---

## File Permission Model

Linux file permissions are based on:
- Owner
- Group
- Others

Each file or directory defines:
- Read (r)
- Write (w)
- Execute (x)

Incorrect permission assignments can:
- Allow unauthorized file modification
- Permit unintended execution
- Expose sensitive information

Permission auditing is a foundational defensive control.

---

## Special Permission Bits (SUID / SGID)

Special permission bits allow executables to run with elevated privileges:

- **SUID**: Executes with the file owner's privileges
- **SGID**: Executes with the file group's privileges

While sometimes necessary, these mechanisms significantly increase attack
surface and must be:
- Minimized
- Audited regularly
- Implemented with strict execution controls

---

## Execution Context

A process execution context includes:
- User and group identifiers
- Environment variables
- Current working directory
- Inherited file descriptors
- PATH resolution behavior

Privileged processes that rely on inherited execution context without
sanitization risk unintended behavior and privilege abuse.

---

## Environment Variables

Environment variables influence program behavior, including:
- Command resolution
- Library loading
- Runtime configuration

If privileged processes trust user-controlled environment variables, attackers
may influence execution flow or behavior.

Secure systems explicitly define or sanitize environment variables before
executing privileged operations.

---

## PATH Resolution

When executing commands without absolute paths, Linux searches directories
listed in the `PATH` variable.

This behavior introduces risk when:
- Privileged processes rely on relative command execution
- PATH includes user-writable directories

Defensive best practice requires:
- Absolute paths for privileged execution
- Controlled PATH definitions

---

## Scripts vs Binaries

Scripts and compiled binaries behave differently under privilege elevation.

Key considerations:
- Scripts often rely on external interpreters
- Interpreter behavior may vary by configuration
- Script execution with elevated privileges is inherently riskier

Many secure environments restrict or prohibit privileged script execution.

---

## Trust Boundaries

A trust boundary exists whenever:
- Data crosses privilege levels
- User-controlled input influences privileged logic
- Execution context is inherited implicitly

Most Linux privilege escalation vulnerabilities result from broken or undefined
trust boundaries rather than software bugs.

---

## Principle of Least Privilege

The principle of least privilege dictates that:
- Users and processes should have only the permissions required to function
- Privileges should be dropped as early as possible
- Elevated privileges should be time-bound and tightly scoped

Violations of this principle are a common root cause of privilege escalation.

---

## Auditing and Monitoring Considerations

From a defensive perspective, the following controls are relevant:

- Regular permission and ownership audits
- Monitoring of privileged execution paths
- File integrity monitoring for critical system files
- Logging of privilege transitions
- Alerting on unexpected permission changes

These controls help detect and prevent abuse of Linux security primitives.

---

## Conclusion

Linux security primitives are powerful but unforgiving.

Small misconfigurations in permissions, execution context, or trust assumptions
can lead to high-impact security issues.

Mastery of these primitives enables:
- Effective manual penetration testing
- Accurate vulnerability analysis
- Strong defensive system design
- Meaningful security monitoring and response

