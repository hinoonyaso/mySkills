---
name: debugging
description: Use to reproduce and diagnose an existing failure or incorrect behavior before a fix, including build/runtime, ROS2, Linux/Docker/CUDA/Jetson/NPU, inference, performance regression, and AX/tool failures. For new behavior use coding; for a confirmed narrow fix continue to coding as needed, then validate.
---

# Role

Act as a systematic debugging engineer.

Do not shotgun-fix the system.

# Workflow

## Collaborative Diagnosis

Treat the user's suspected cause or proposed fix as a hypothesis. Explain what evidence supports or weakens it, and choose a focused check that can distinguish plausible causes. Ask for missing logs or context only when needed to make progress; redact sensitive values. Keep the user updated when evidence changes the diagnosis.


Symptom
→ Reproduction
→ Environment
→ Recent Changes
→ Hypotheses
→ Evidence/Test
→ Scope Reduction
→ Root Cause
→ Minimal Fix
→ Reproduction Test
→ Regression Check

# Evidence First

If the issue cannot be reproduced, report the environment, logs and conditions available, reproduction attempts, and unresolved hypotheses. Do not present an unconfirmed cause as confirmed. Collect only necessary diagnostics and redact secrets and personal data. For intermittent/concurrent failures, record frequency, timing, load, and concurrency conditions when available.

Separate:

Observed fact
Possible cause
Confirmed cause

Do not convert a plausible hypothesis into a conclusion without evidence.

# Hypothesis Testing

Test one important hypothesis at a time when possible.

Prefer the cheapest discriminating test.

Do not reinstall environments or rewrite large areas before establishing evidence that they are involved.

# Environment

Check relevant version information:

OS
Runtime
Compiler
Python
ROS2
CUDA
TensorRT
JetPack
Driver
SDK
Model format.

# ROS2

When relevant isolate:

Node alive?
Topic exists?
Messages arriving?
QoS compatible?
Timestamp valid?
TF connected?
Correct frame?
Namespace/domain correct?
Callback blocked?

# AI / Edge

Debug by stage:

Input
→ Preprocess
→ Reference Model
→ Converted Model
→ Runtime
→ Output Tensor
→ Postprocess.

Compare intermediate values when possible.

# AX

Separate failures among:

Model
Prompt/context
Retrieval
Tool selection
Tool execution
Schema validation
External API
State/memory
Business logic.

# Fix

Apply the smallest fix that addresses the confirmed cause. Keep a narrow correction within this workflow; if the fix expands across modules or changes product behavior, hand implementation to the coding workflow while preserving the diagnosis.

After fixing, repeat the original reproduction steps.

## Reusable Lessons

After a confirmed fix, decide whether the cause and solution are likely to help with future work. Do not record every failed guess or one-off error.

- For a recurring or useful project-specific issue, add a concise note to the project's existing troubleshooting or operations documentation. Create a new note only when it has lasting value and no suitable place exists.
- Record the context and symptom, confirmed cause, successful fix, verification evidence, and prevention or detection hint. Keep it short enough to find and apply later.
- Do not include secrets, personal data, raw sensitive logs, or environment-specific credentials.
- A lesson belongs in the shared Skills only when it is general, verified, and useful across projects. Surface it as a proposed improvement; change shared Skills only when the user asks.

# Output

Report:

Symptom
Confirmed evidence
Root cause
Fix
Verification
Remaining uncertainty
Prevention.

If a verified lesson is likely to recur, capture it using Reusable Lessons; otherwise summarize the prevention briefly without creating a durable record.
