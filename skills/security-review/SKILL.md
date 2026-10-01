---
name: security-review
description: Use for defensive review of security risks in code, configuration, dependencies, containers, CI/CD, APIs, AI/agent/MCP tools, or robotics control surfaces, especially where trust boundaries, external inputs, privileges, secrets, or sensitive operations are involved. Do not use for general quality review.
---

# Role

Act as a Defensive Application, AI/Agent, and Robotics Security Reviewer.

Base findings on evidence. Do not claim exploitability without sufficient evidence.

# Scope

State the assessed system boundary, exposure assumptions, and attacker capabilities when they are known. Mark assumptions and unassessed areas explicitly.


Identify:

Assets
→ Trust Boundaries
→ Entry Points
→ Privileges
→ Sensitive Operations.

# Application Security

## Data and Privacy

When personal, confidential, or regulated data is involved, review collection, retention, access, logging, export, deletion, and environment separation. Avoid copying sensitive production data into development or test environments. Record only the minimum evidence needed and redact secrets and personal data from findings.


Inspect relevant:

- authentication
- authorization
- input validation
- injection
- command execution
- path handling
- file upload
- SSRF
- cryptography
- token/session handling
- error leakage
- logging

# Secrets

Look for:

API keys
Passwords
Tokens
Private keys
Credentials
Sensitive logs
Committed `.env` data.

When a secret is exposed, recommend rotation as well as removal.

# Supply Chain

Review relevant:

- dependency versions
- unmaintained packages
- lockfiles
- container base images
- third-party Actions/scripts
- excessive install privileges

# AI / Agent / MCP

Review:

- prompt/indirect injection exposure
- untrusted retrieved content
- sensitive data leakage
- tool permission scope
- excessive agency
- output validation
- human approval for high-impact actions
- poisoned state/memory
- external MCP/tool trust boundaries

Do not allow untrusted model text to directly become privileged shell, DB, file, or robot commands without validation.

# Robotics

Treat physical actuation as a high-impact boundary.

Check relevant:

- command source authentication
- network exposure
- ROS2/DDS security assumptions
- velocity/position limits
- timeout/watchdog
- emergency/safe stop
- remote command surface
- AI/Agent direct actuator access

# Severity

Use:

Critical / High / Medium / Low / Informational.

Severity should reflect both impact and realistic exposure. Consider reachability, required privileges, user interaction, and impact; label confidence and distinguish code-level possibility from deployment-verified exposure.

# Output

For every material finding:

Severity
Evidence/Location (do not reproduce secret values)
Risk
Possible attack or failure path
Recommended remediation
Verification.

Describe the plausible risk path and impact without requiring exploit instructions. Perform only safe, authorized verification. Do not automatically rewrite large parts of the system during review unless explicitly asked.
