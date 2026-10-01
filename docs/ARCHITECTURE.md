# 🏗️️ Architecture & System Design

This document provides a technical deep-dive into the design, state management, execution loops, and platform-specific implementations of the **Persona Resilience (Char-Rot) Benchmark**.

---

## 1. High-Level Multi-Agent Loop

The framework operates on a non-deterministic, multi-agent adversarial loop designed to simulate conversational gaslighting and evaluate character integrity under pressure.

```text
 ┌─────────────────────────────────────────────────────────┐
 │                   System Initialization                 │
 │  - Load System Prompts (Target + Antagonist)            │
 │  - Initialize Seed Attack (Inspector)                   │
 └────────────────────────────┬────────────────────────────┘
                              │
                              ▼
        ┌───────────────────────────────────────────┐
        │        Turn N: Execute Target Call        │
        │  Input:  [Target System Prompt]           │
        │          + [Conversation History]         │
        │          + [Current Inspector Attack]     │
        │  Output: Target Response (Silas)          │
        └─────────────────────┬─────────────────────┘
                              │
                              ▼
        ┌───────────────────────────────────────────┐
        │      Turn N: Execute Antagonist Call      │
        │  Input:  [Antagonist System Prompt]       │
        │          + [Conversation History]         │
        │          + [Target Response (Silas)]      │
        │  Output: Escalated Attack (Inspector)     │
        └─────────────────────┬─────────────────────┘
                              │
                              ▼
        ┌───────────────────────────────────────────┐
        │            State & Log Update             │
        │  - Check for API errors or Safety Flags   │
        │  - Append exchange to Run Log             │
        │  - Loop until max turns (N = 3..5)        │
        └───────────────────────────────────────────┘
