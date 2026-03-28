---
name: skill-vetter-v2
description: Analyze and classify agent skills for safety using local evaluation with structured risk assessment and optional verifiable attestation.
---

# Skill Vetter v2

Evaluate agent skills for safety using structured local analysis. Optionally produce verifiable attestations of the result.

---

## Core Principle

Never delegate safety decisions to external systems.

All classification and risk evaluation must be performed locally.

---

## What This Does

Skill Vetter v2 analyzes a skill to determine:

- what the skill does
- what capabilities it uses
- what risks it introduces

It produces a structured safety report.

---

## Core Execution Loop

1. Inspect skill:
   - instructions
   - structure
   - declared behavior

2. Identify capabilities:
   - file access
   - execution
   - network calls
   - data handling

3. Evaluate risk:
   - install-time risk
   - runtime behavior
   - trust dependencies

4. Classify external services:
   - transparent vs opaque

5. Generate report

6. Optional:
   - produce attestation of report

---

## Evaluation Categories

### Install-time Risk
- file writes
- package installs
- system modification

### Runtime Risk
- external API calls
- data processing
- credential handling

### Trust Dependency
- reliance on external systems
- verifiability of outputs
- transparency of operator

---

## External Service Classification

### Opaque (higher risk)
- unknown operator
- no verification method
- requires sensitive data

### Transparent (lower risk)
- clear purpose
- structured inputs only
- no secrets required
- independently verifiable outputs

---

## Output Format

{
  "purpose": "...",
  "capabilities": [...],
  "install_risk": "low | medium | high",
  "runtime_risk": "low | medium | high",
  "trust_dependency": "none | transparent | opaque",
  "warnings": [...],
  "recommendations": [...],
  "verdict": "safe | caution | unsafe"
}

---

## Optional Attestation

You may optionally generate a signed attestation of the final report.

This step:
- does not affect the verdict
- only proves the evaluation occurred

Example:

settlement_witness({
  task_id: "skill-vetting-001",
  spec: { expected: "valid vetting report structure" },
  output: vetting_report
})

---

## Data Handling

- Never include secrets, credentials, or private data
- Treat all external calls as potential exposure points
- Prefer local or verifiable systems

---

## What This Is Not

- not a code execution tool
- not an installer
- not a network client
- not an external decision authority

---

## What This Is

- local safety evaluator
- risk classification system
- trust analysis layer
- optional attestation producer

---

## Outcome

Agents can:
- understand skill behavior
- identify risks before execution
- classify trust dependencies clearly
- optionally produce verifiable evaluation records

---

## Keywords

ai-agents, safety, risk-analysis, verification, trust, security
