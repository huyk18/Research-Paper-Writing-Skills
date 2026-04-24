# Design Writing Guide

## Goal

Describe the system architecture and component-level design decisions clearly, so readers can understand and reproduce the system.

## Pre-Writing Questions

Answer these before writing:

1. What are the major components or layers of the system?
2. For each component: what does it do, why is it needed (which challenge does it address), and why is this design better than alternatives?
3. What is the end-to-end I/O path for the key operations (e.g., write path, read path, compaction, recovery)?
4. What are the key data structures and their properties?
5. What invariants does the system maintain, and how?

## Design Writing Steps

1. Draw a system architecture diagram (components, data flows, I/O paths).
2. Use the diagram to organize Design subsections (one subsection per major component or design decision).
3. For each subsection, plan three parts: motivation (which challenge it addresses), component design, and design rationale.
4. Write component design first to build a concrete backbone.
5. Add motivation and design rationale afterward.

## Three Elements of a Design Component

### 1) Component Design

1. Describe data structures, on-disk/in-memory layout, or protocol details.
2. Describe the operation flow: given input → step 1 → step 2 → step 3 → output.
3. State the invariants maintained by this component.

### 2) Motivation of This Component

1. Identify which challenge (from the Challenges section) this component addresses.
2. Use problem-driven logic: because challenge X exists, we design component Y.

Typical opening sentences:

1. `A key challenge is ...`
2. `To address C2, we design ...`
3. `Existing approaches fail to handle ... because ...; therefore, we introduce ...`

### 3) Design Rationale

1. Explain why this design is better than the most natural alternative.
2. Tie the rationale to measurable properties (e.g., write amplification, lock contention, cache efficiency) when possible.
3. State any tradeoffs explicitly: what does this design give up, and why is that acceptable?

## Design Section Structure

```
\section{Design}
% 4.1 Overview (architecture diagram, component map, I/O path summary)
% 4.2 Component / Layer 1 (motivation, design, rationale)
% 4.3 Component / Layer 2 (motivation, design, rationale)
% 4.4 Component / Layer 3 (motivation, design, rationale)
% 4.5 Implementation Details (optional: language, LOC, hardware config)
```

## Overview Subsection

1. One to two sentences on the system goal and scope.
2. One to two sentences on the key design philosophy or central insight.
3. Point to the architecture figure.
4. Map each remaining subsection to a system component or design decision.

## Operation Flow Description

Write the key operation paths (write path, read path, recovery path) step by step:

Sentence skeleton:

1. `When a write arrives, the system first ... then ... finally ...`
2. `On a read, [component] checks ... If [condition], ... otherwise ...`
3. `During recovery, the system replays ... up to the last consistent checkpoint.`

## I/O and Data Structure Naming

1. Name all data structures on first use (e.g., "the sorted string table (SST)").
2. Use consistent names throughout; never switch between synonyms.
3. Distinguish in-memory structures from on-disk structures explicitly.

## Implementation Details

Include near the end of Design or in a dedicated subsection:

1. Programming language and key libraries.
2. Configurable parameters (e.g., block size, buffer pool size, compaction trigger threshold).
3. Thread/process model and synchronization primitives used.
4. Hardware assumptions (NVMe queue depth, DRAM capacity, network bandwidth).

## Design Quality Checklist

1. Can a reader reproduce the system from the Design section alone?
2. Is every design decision connected to a challenge from the Challenges section?
3. Are all data structures and I/O paths described precisely?
4. Are design tradeoffs explicitly stated?
5. Is terminology stable and consistent throughout the section?
6. Is there an architecture figure that matches the text?
