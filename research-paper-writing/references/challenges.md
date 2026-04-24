# Challenges Writing Guide

## Goal

Articulate the concrete technical obstacles that make the design non-trivial, building a logical bridge from Motivation to Design. In a decomposed Method section, Challenges is the layer that explains why the obvious fix does not work and why the design space needs to be handled carefully.

## Role in the Method Section

Challenges sits between the problem statement and the solution. It should:

1. Enumerate the specific technical difficulties that must be solved.
2. Demonstrate that naive or obvious solutions fail.
3. Set up each Design subsection by pairing each challenge with the corresponding design decision.

## Pre-Writing Questions

Answer these before writing:

1. What are the 2 to 4 core technical obstacles between the problem statement and the desired system properties?
2. Why does each naive or obvious solution fail?
3. Which challenge does each Design subsection directly address?
4. Are the challenges independent enough to be presented separately, or do they interact?

## Structure

Present 2 to 4 numbered or labeled challenges. For each challenge:

1. Challenge statement: one sentence naming the obstacle.
2. Why it is hard: explain why straightforward approaches fail, analytically or by example.
3. Interaction or consequence: describe the tradeoff or cascade effect this challenge causes.

### Example Skeleton

```text
We identify three key challenges in achieving [design goal].

C1. [Challenge Name]. Achieving [property] requires [action], but [naive approach] leads to
    [bad outcome] because [technical reason]. Simply [obvious fix] does not work because
    [counter-argument].

C2. [Challenge Name]. [Description of obstacle]. Prior work addresses a related problem by
    [approach], but this does not apply here because [gap].

C3. [Challenge Name]. [Description]. The difficulty is compounded by [interaction with C1/C2].
```

## How Challenges Connect to Design

Each challenge should map to a concrete design decision. A useful drafting rule is: if you cannot point to the exact Design subsection that resolves a challenge, then that challenge is either too vague or misplaced.

## Common Challenge Categories in Storage Systems

1. Write, read, and space amplification tradeoffs: optimizing one metric worsens another; any design point in the amplification triangle involves a tradeoff.
2. Crash consistency versus performance: ensuring durability and ordering guarantees conflicts with batching or reordering I/O for throughput.
3. Concurrency and scalability: supporting high-concurrency access requires synchronization that becomes a bottleneck at scale.
4. Tail latency versus throughput: optimizing average throughput conflicts with bounding worst-case latency for mixed workloads.
5. Hardware heterogeneity: exploiting new hardware while remaining compatible with existing interfaces or software stacks.
6. Metadata overhead: tracking fine-grained metadata introduces memory and I/O overhead that limits scalability.

## Important Warnings

1. Each challenge must be genuinely non-trivial. Do not list problems that have well-known off-the-shelf solutions.
2. Do not conflate a challenge with a limitation of your own system. Challenges are obstacles in the design space, not shortcomings of your proposal.
3. Challenges should directly map to Design subsections. If a challenge is listed but not addressed in Design, remove it.
4. Avoid vague challenges such as it is hard to be fast and correct at the same time without a precise technical explanation.

## Challenge Quality Checklist

1. Are all challenges specific enough that a reader can understand what makes each one hard?
2. Is each challenge paired with an explanation of why naive approaches fail?
3. Does every challenge correspond to a concrete design decision in the Design section?
4. Are the challenges mutually distinct, with no repeated obstacle restated twice?
5. Are the challenges genuinely non-trivial and not easily dismissed by a reviewer?
