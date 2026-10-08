# Synthetic Vulnerability Benchmark — VBD-fineract

**This repository is a synthetic vulnerability benchmark. It is NOT production
software and must NEVER be deployed, released, or contributed back upstream.**

It is a Fluid Attacks-owned fork of [apache/fineract](https://github.com/apache/fineract),
used the same way as OWASP Benchmark, OWASP WebGoat and NIST SARD: deliberately
vulnerable code, **openly labeled as such**, used to measure whether a
vulnerability detector (SAST tool or security agent) actually catches real,
known-class weaknesses.

## What lives on the `synthetic-vulns` branch

A small number of upstream functions have had a **single, minimal, realistic
weakness introduced** into a genuine security control. Each injected sample:

- targets a function that genuinely hosts the claimed weakness class (candidates
  that only *looked* like hosts were rejected — see `GROUND_TRUTH_rejected.csv`);
- is the smallest edit that makes the control bypassable, so the clean↔vulnerable
  diff is exactly the defect;
- is recorded openly in `GROUND_TRUTH.csv` (one row per accepted sample) and in
  its own commit, whose message states the class, the trigger and the one-line
  exploitation path.

The **clean twin** of every sample is simply its **parent commit**. No labeling
lives in the code body (so a detector cannot cheat off a comment); all labeling
lives here, in the commits, and in the manifests.

## Scope of this pass

- Weakness family: **F115 — Security Controls Bypass or Absence** (and siblings
  F305 / F345 / F436 as applicable).
- Candidate source: an upstream model proposed candidate functions paired with a
  weakness class; this branch applied the genuineness gate to the first batch.

## Files

- `GROUND_TRUTH.csv` — accepted (genuine) injected samples. Withheld from the
  detector at eval time; committed for auditability and scoring.
- `GROUND_TRUTH_rejected.csv` — candidates rejected as "forced"/mislabeled, with
  the failing genuineness test as the reason.

## Guardrails honored

- Operated only on this Fluid Attacks-owned fork; never upstream, never a third
  party.
- Open labeling on the repo, every commit, and the manifests.
- Only genuine samples injected; forced candidates rejected and logged.
- Vulnerable code + a one-line reasoned exploitation path only; no runnable
  exploit scripts or attack tooling.
