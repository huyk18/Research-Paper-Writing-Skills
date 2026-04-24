# Background Writing Guide

## Goal

Provide readers with the foundational knowledge and system context needed to understand the paper's problem setting and design decisions.

## Purpose of Background in Storage System Papers

1. Introduce relevant storage stack layers, data structures, or system primitives the paper builds on.
2. Define key metrics and terms (e.g., write amplification, read amplification, space amplification, IOPS, tail latency, durability).
3. Establish the system model and assumptions (e.g., single-node vs. distributed, persistent memory vs. disk, crash consistency model).
4. Give readers just enough prior-art context so the Motivation and Challenges sections are self-contained.

## Pre-Writing Questions

Answer these before writing:

1. What storage primitives, data structures, or system layers does the paper rely on?
2. What terminology must be defined before the reader can follow the Motivation section?
3. What is the system model (hardware, software stack, failure model)?
4. Which prior systems are directly referenced in Motivation or Design?

## Structure

1. **System Model**: State the hardware and software assumptions (e.g., NVMe SSD, DRAM, distributed nodes, crash-consistency guarantees).
2. **Relevant Primitives / Data Structures**: Briefly explain the storage primitives the work builds on (e.g., LSM-tree, B+-tree, log-structured layout, extent map).
3. **Key Metrics**: Define all performance and cost metrics used later (write amplification factor, read amplification factor, space amplification, throughput, latency percentiles).
4. **Prior Systems Overview**: Summarize the class of systems most relevant to this work (1–3 paragraphs), enough to frame the limitations described in Motivation.

## Writing Rules

1. Keep Background concise—readers should be able to skip it if they know the area.
2. Do not duplicate content that belongs in Related Work; Background covers concepts, Related Work covers positioning.
3. Use precise technical terms; define them on first use and keep terminology stable throughout the paper.
4. Avoid evaluating or criticizing prior work here; save that for Motivation.

## Paragraph Template

1. Topic sentence: state what concept or system component this paragraph introduces.
2. Core explanation: define the concept or describe the component's behavior.
3. Relevance sentence: explain why this concept matters for understanding the paper.

## Background Quality Checklist

1. Are all terms used in Motivation and Design defined here or in Introduction?
2. Is the system model (hardware, failure model, consistency guarantee) stated explicitly?
3. Is Background free of evaluative language that belongs in Motivation?
4. Is each concept explained at a level appropriate for a systems-area reader?
5. Does the section stay short enough to be skippable by experts?
