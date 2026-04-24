# Motivation Writing Guide

## Goal

Convince readers that the problem this paper solves is real, important, and unsolved by existing systems.

## Purpose of Motivation in Storage System Papers

1. Show concrete evidence—measurements, profiles, or analytical arguments—that existing systems fall short.
2. Identify the root cause of the performance or correctness gap, not just the symptom.
3. Create reader buy-in: after reading Motivation, readers should understand *why* a new design is necessary.

## Pre-Writing Questions

Answer these before writing:

1. What specific workload, access pattern, or failure scenario exposes the limitation?
2. What metric(s) degrade, and by how much? (Use real numbers whenever possible.)
3. What is the root technical reason for the degradation—not just "it is slow" but why the existing design causes this?
4. Have you shown that the limitation is fundamental to the existing approach, not just a tuning issue?
5. Is the workload or scenario realistic and representative of practice?

## Structure

### Version 1: Measurement-Driven Motivation

Use when you can run controlled experiments to demonstrate the gap.

1. Describe the target workload or scenario.
2. Show measurements (figure or table) comparing existing systems under that workload.
3. Diagnose the root cause with profiling or analytical breakdown.
4. State the implication: because of root cause X, existing systems cannot achieve goal Y.

Sentence skeleton:

1. `To understand the limitations of existing approaches, we profile [system] under [workload].`
2. `Figure X shows that [metric] degrades by [amount] as [parameter] increases.`
3. `Profiling reveals that [percentage]% of time/bandwidth is spent on [root cause].`
4. `This bottleneck is fundamental to [design choice], and cannot be resolved by [simple fix].`

### Version 2: Analytical / Design-Space Motivation

Use when the limitation follows from a design-space argument without needing measurements.

1. Describe the design invariant of existing systems.
2. Explain analytically why that invariant conflicts with the target goal.
3. Illustrate with a small example or worst-case scenario.
4. Conclude with the gap statement.

Sentence skeleton:

1. `Existing systems adopt [design choice] to achieve [property].`
2. `However, this design inherently causes [cost] because [reason].`
3. `For example, consider a workload with [characteristic]: [consequence].`
4. `As a result, existing systems cannot achieve [target goal] without [unacceptable tradeoff].`

## Important Warnings

1. Do not let Motivation be a vague claim ("existing systems are slow"). Quantify or reason precisely.
2. Do not attack strawmen—use strong, recent, representative systems as the baseline.
3. Ensure the identified root cause is exactly what the Design section addresses.
4. Do not propose solutions here; Motivation ends at the problem statement.

## Motivation Quality Checklist

1. Is there concrete evidence (numbers or analytical argument) that the gap is real?
2. Is the root cause of the limitation clearly identified and technically justified?
3. Is the baseline system or approach fair and representative?
4. Does Motivation end with a clear problem statement that directly motivates the Design?
5. Is the workload or scenario realistic for practical storage deployments?
