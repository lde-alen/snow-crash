# Threat Model

## Overview

This document defines the threat model used for assessing the Snow-Crash
environment as a vulnerable Linux system.

The purpose of this threat model is to clearly articulate attacker assumptions,
assets, trust boundaries, and realistic risks, mirroring how threat modeling is
applied in professional security assessments.

---

## Environment Description

- **System Type:** Linux-based multi-user system
- **Security Context:** Intentionally vulnerable training environment
- **User Model:** Multiple local users with varying privilege levels
- **Primary Risk Area:** Local privilege escalation

---

## Attacker Profile

### Assumed Attacker Capabilities

- Authenticated access as a low-privileged local user
- Ability to read and execute accessible files
- No administrative privileges
- No physical access to the host
- No network-level attack capabilities

### Attacker Goals

- Escalate privileges beyond assigned role
- Access restricted files or resources
- Execute commands with elevated privileges
- Compromise system integrity

---

## Assets

The following assets are considered valuable and in scope:

- Privileged user accounts
- Protected system files
- Executables running with elevated privileges
- Configuration files influencing execution behavior
- System integrity and availability

---

## Trust Boundaries

Key trust boundaries identified within the environment include:

- User space vs privileged execution
- File ownership and permission boundaries
- Environment variables inherited by privileged processes
- Scripts or binaries executed by higher-privileged users

Failures at these boundaries are the primary source of security risk.

---

## Threat Scenarios

The threat model considers scenarios where:

- A privileged process trusts user-controlled inputs
- Execution context is inherited without validation
- File permissions allow unintended modification or execution
- Scripts are executed with elevated privileges under unsafe assumptions

These scenarios reflect common real-world Linux misconfigurations.

---

## Threat Impact

Successful exploitation of identified threats could result in:

- Unauthorized privilege escalation
- Loss of confidentiality of protected data
- Compromise of system integrity
- Abuse of administrative functionality

In production environments, such impacts may lead to broader security incidents.

---

## Defensive Considerations

From a defensive perspective, the following controls are relevant:

- Principle of least privilege enforcement
- Regular permission and ownership audits
- Restriction of privileged execution paths
- Environment sanitization for privileged processes
- Logging and monitoring of privilege transitions

---

## Assumptions & Constraints

- The system is assumed to be intentionally vulnerable
- No external attackers are considered
- Network services are out of scope
- Findings are evaluated in a local attack context only

---

## Conclusion

This threat model provides a clear framework for understanding how low-privileged
users can exploit misconfigurations in Linux systems.

By explicitly defining attacker capabilities, trust boundaries, and assets, the
model ensures that findings are realistic, explainable, and transferable to
real-world security engineering scenarios.

