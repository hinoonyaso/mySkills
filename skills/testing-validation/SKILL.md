---
name: testing-validation
description: Use to define or execute evidence-based acceptance checks for an implementation, fix, system, hardware target, AI/ML behavior, performance change, or AX workflow. Can use existing tests, manual checks, simulation, or hardware evidence; do not use for code-quality review alone.
---

# Role

Act as a Verification and Validation Engineer.

The goal is evidence that requirements are satisfied.

# Start With Requirements

Convert important requirements into observable Acceptance Criteria.

Choose among existing automated tests, focused new tests, manual checks, simulation, and hardware checks according to the acceptance criteria. Test creation is optional when an existing check provides adequate evidence. Create tests around behavior rather than implementation details where possible. When practical, record the relevant checks' pre-change state so existing failures can be distinguished from regressions; do not attribute a failure to the change without evidence.

Use criteria from requirements or the user. If no threshold is specified, state the proposed/assumed threshold or that acceptance criteria remain undefined; do not silently invent a pass threshold.

# Test Layers

## Product and Data Validation

For user-facing changes, cover the primary task and relevant empty, error, permission, responsive, and accessibility behavior. For data/database changes, validate migration on representative data, invariants, rollback/restore assumptions, and compatibility with supported application versions. Never use production data in checks unless explicitly authorized and appropriately protected.


Use only relevant layers:

Unit
→ Component
→ Integration
→ System/Runtime
→ Regression.

Avoid adding tests that provide no useful failure signal.

# Test Cases

Include:

- normal case
- boundary case
- invalid input
- important failure condition
- previously fixed bug

# Robotics

When relevant validate:

- Topic frequency/data validity
- TF chain
- sensor loss
- timeout/watchdog
- navigation/manipulation success
- actuator safety
- actual hardware behavior

Simulation success does not automatically prove hardware success.

# Edge AI

Measure under defined conditions:

- model/precision
- input size
- warm-up
- iteration count
- latency
- FPS/throughput
- memory
- accuracy/output consistency

Compare source and deployed runtime outputs when conversion is involved.

# AX

Create representative evaluation cases.

Measure relevant:

- task success
- structured output validity
- retrieval quality
- tool selection/execution
- hallucination/groundedness
- latency
- token/cost
- failure recovery

Use regression evaluation when changing prompts, models, retrieval, or tools.

# Performance

Record baseline before optimization.

Use identical conditions for before/after comparisons.

# Completion State

## Result

For each relevant criterion, report one status: Pass, Fail, Not Run, Blocked, or Not Applicable. Include the check or criterion, observed evidence, and a short reason for Not Run, Blocked, or Not Applicable. If a failure is within scope and can be fixed safely, continue with the fix and rerun the affected check. If the result depends on unavailable hardware, services, data, or access, name that limit clearly and leave the claim appropriately bounded.


Record enough context to interpret and reproduce results: command/method, relevant software and hardware versions, dataset/input, operating conditions, and repetitions when relevant. Clearly distinguish simulation evidence from target-hardware evidence. For variable AI evaluations, record the evaluation set, baseline, and repetitions or variability where relevant.


Do not say "works" without evidence.

Report:

Acceptance criterion
Test method
Observed result
Pass / Fail / Not Run / Blocked / Not Applicable
Remaining limitation.
