# Motivation Writing Guide

## Goal

Convince readers that the problem this paper solves is real, important, and still unsolved by existing systems. In a paper whose Method is split into motivation, challenges, and design, this section should stop at the problem statement: it should explain why a new design is necessary, but not how to build it.

## Role in the Method Section

Motivation is the problem layer of Method. It should do three things:

1. Show concrete evidence that the current approach falls short.
2. Identify the root cause of the gap, not just the symptom.
3. End with a clear statement that naturally leads into Challenges and Design.

## Pre-Writing Questions

Answer these before writing:

1. What specific workload, access pattern, or failure scenario exposes the limitation?
2. What metric(s) degrade, and by how much? Use real numbers whenever possible.
3. What is the root technical reason for the degradation, not just the visible symptom?
4. Have you shown that the limitation is fundamental to the existing approach, not just a tuning issue?
5. Is the workload or scenario realistic and representative of practice?

## Structure

### Version 1: Measurement-Driven Motivation

Use this when you can run controlled experiments to demonstrate the gap.

1. Describe the target workload or scenario.
2. Show measurements comparing existing systems under that workload.
3. Diagnose the root cause with profiling or analytical breakdown.
4. State the implication: because of root cause X, existing systems cannot achieve goal Y.

Sentence skeleton:

1. To understand the limitations of existing approaches, we profile [system] under [workload].
2. Figure X shows that [metric] degrades by [amount] as [parameter] increases.
3. Profiling reveals that [percentage]% of time or bandwidth is spent on [root cause].
4. This bottleneck is fundamental to [design choice], and cannot be resolved by [simple fix].

### Version 2: Analytical / Design-Space Motivation

Use this when the limitation follows from a design-space argument without measurements.

1. Describe the design invariant of existing systems.
2. Explain analytically why that invariant conflicts with the target goal.
3. Illustrate with a small example or worst-case scenario.
4. Conclude with the gap statement.

Sentence skeleton:

1. Existing systems adopt [design choice] to achieve [property].
2. However, this design inherently causes [cost] because [reason].
3. For example, consider a workload with [characteristic]: [consequence].
4. As a result, existing systems cannot achieve [target goal] without [unacceptable tradeoff].

## From Motivation to Challenges

The final paragraph of Motivation should hand off to Challenges. A clean handoff usually does two things:

1. Restates the problem in technical terms, not rhetorical terms.
2. Signals that the gap is not solved by one simple fix, so the design space needs to be decomposed.

## Important Warnings

1. Do not let Motivation become a vague claim such as existing systems are slow. Quantify or reason precisely.
2. Do not attack strawmen. Use strong, recent, representative systems as the baseline.
3. Ensure the identified root cause is exactly what the Design section addresses later.
4. Do not propose solutions here. Motivation ends at the problem statement.

## Motivation Quality Checklist

1. Is there concrete evidence, numerical or analytical, that the gap is real?
2. Is the root cause of the limitation clearly identified and technically justified?
3. Is the baseline system or approach fair and representative?
4. Does Motivation end with a clear problem statement that directly motivates Challenges and Design?
5. Is the workload or scenario realistic for practical deployments?
