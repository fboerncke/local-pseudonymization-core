# Architecture

## Purpose

Local Pseudonymization Core is designed as a reusable infrastructure component for protecting sensitive text before it is sent to AI or LLM systems.

The architecture is intended to separate the core transformation logic from user-facing applications and from specific AI providers. This makes the project easier to maintain, test, integrate, and review.

## Architectural goals

The architecture is guided by the following goals:

- clear separation between core logic, configuration, and interfaces
- local operation without requiring cloud-based privacy services
- explicit, reviewable protection rules instead of opaque automatic decisions
- support for multiple integration paths such as library, CLI, proxy, and API
- maintainability, testability, and long-term reuse in other systems

## Core principles

### 1. Separation of concerns

The project is structured so that pseudonymization logic, configuration handling, and system integration are not tightly coupled.

This separation is important because the same core should be usable in different contexts, including:
- command-line workflows
- local AI gateways
- internal services
- other applications embedding the library

### 2. Local control

Sensitive text transformation should happen locally or inside an organization's controlled environment.

The architecture is intended to avoid unnecessary trust assumptions in external providers and to keep protection decisions, rule definitions, and re-identification logic under local control.

### 3. Explicit protection rules

The system does not attempt to autonomously decide what is private in every context.

Instead, the architecture is based on explicit and maintainable rules defined by users or organizations. Optional NLP-based assistance may be added later, but it should remain assistive rather than authoritative.

### 4. Reversible pseudonymization

The core is designed around reversible pseudonymization rather than one-way anonymization.

This means that:
- protected terms are replaced before AI processing
- the transformed text is sent onward
- the returned result is processed locally
- protected values are restored in context afterwards

This reversible flow is central to the usefulness of the system in real-world workflows.

## Planned high-level components

### Core engine

The core engine is responsible for:
- applying rule-based pseudonymization
- generating stable placeholders
- tracking replacement mappings needed for re-identification
- restoring protected values in the returned output

This is the central component of the project and should remain independent from UI concerns and provider-specific logic.

### Rule and configuration layer

This layer is responsible for:
- storing and loading protection rules
- representing categories, terms, and patterns to be protected
- supporting maintainable configuration formats
- enabling controlled reuse of rules across workflows or organizations

Over time, this layer may also support encrypted or versioned rule configurations.

### Interface layer

The project is intended to support several integration modes:

- **Library**: direct embedding into other software
- **CLI**: scripted use, local automation, and batch-oriented workflows
- **Proxy**: interception layer for AI or LLM requests
- **API**: local service interface for internal tools and system integrations

These interfaces should depend on the core, but the core should not depend on them.

### Documentation and reference integrations

A separate documentation layer is intended to describe:
- architecture decisions
- trust assumptions
- integration patterns
- limitations and non-goals

Reference integrations can help demonstrate how the core can be used in realistic environments without turning the project itself into an end-user product.

## Conceptual flow

```text
Sensitive text
    ↓
Rule-based local pseudonymization
    ↓
Transformed text sent to AI / LLM endpoint
    ↓
AI response
    ↓
Local re-identification
    ↓
Restored result
```

## Dependency strategy

The project is intended to keep critical external dependencies limited and well-scoped.

Dependencies may be used for:
- pattern matching and text processing
- optional NLP assistance
- cryptographic functions for protected configuration handling
- document parsing or exchange formats

The core transformation logic, rule handling, and re-identification flow should remain project-owned and reviewable.

## Trust boundaries

The architecture treats the following as trust-sensitive boundaries:

- the moment original sensitive text enters the system
- the transformation from original values to placeholders
- the storage of rules and mappings
- the forwarding of transformed text to external AI systems
- the restoration of protected values in returned output

For this reason, the architecture aims to make data flow assumptions explicit and to keep sensitive operations local whenever possible.

## Non-goals

The architecture is not intended to provide:

- a cloud privacy gateway
- an end-user chat application
- autonomous determination of what should be considered private
- a guarantee of perfect anonymization in every context

The project is designed as a reusable infrastructure layer, not as a complete application product.

## Long-term direction

The long-term direction is a modular, well-documented, and auditable component that can be embedded into other tools and operated in local or internal environments.

A successful architecture for this project should make the system:

- easier to maintain
- safer to extend
- clearer to review
- simpler to integrate
- more resilient over time
