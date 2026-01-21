# Snow-Crash – Linux Security Assessment Portfolio

## Overview

This repository documents a controlled security assessment of the **Snow-Crash**
wargame environment from the 42 Network, approached as a simulated vulnerable
Linux system rather than a capture-the-flag challenge.

The objective of this work is to translate hands-on exploitation practice into
professional security analysis, documentation, and defensive understanding.

 **No passwords, flags, exploit commands, or step-by-step solutions are
disclosed in this repository.**

---

## Objectives

- Analyze Linux privilege boundaries and execution contexts
- Identify common system misconfigurations leading to privilege escalation
- Practice ethical vulnerability documentation
- Develop professional security reporting skills aligned with industry standards
- Bridge offensive techniques with defensive remediation strategies

---

## Scope & Assumptions

- **Assessment Type:** Local, authenticated security assessment
- **Attacker Profile:** Low-privileged local user
- **Target Environment:** Linux-based multi-user system
- **Out of Scope:**
  - Network-based attacks
  - Brute-force or credential guessing
  - Disclosure of secrets or exploitation payloads

---

## Methodology

The assessment follows a lightweight penetration testing methodology inspired by
widely adopted industry practices:

- System enumeration and permission analysis
- Identification of trust boundaries
- Privilege escalation risk assessment
- Root cause analysis
- Mitigation and hardening recommendations

Each Snow-Crash level is treated as an independent security finding and
documented using a consistent reporting structure.

---

## Report Structure

```text
.
├── README.md
├── methodology.md
├── threat-model.md
├── levels/
│   ├── level01.md
│   ├── level02.md
│   ├── level03.md
│   └── ...
└── appendix/
    ├── linux-security-primitives.md
    └── references.md

