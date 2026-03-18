# Roadmap

## Scope

This roadmap describes the intended infrastructure-focused development path for Local Pseudonymization Core.

The project is not planned as an end-user application. Its purpose is to become a reusable open-source component for local, reversible pseudonymization in AI and LLM workflows.

The roadmap is therefore centered on extraction, hardening, interface design, documentation, and integration readiness.

## Roadmap principles

The roadmap is guided by five principles:

- prioritize a stable and reviewable core over rapid feature expansion
- keep protection decisions explicit and locally controlled
- reduce unnecessary architectural coupling
- improve maintainability, testability, and long-term reuse
- document assumptions, limits, and trust boundaries clearly

## Phase 1: Extract and define the core

### Goal

Establish a clearly scoped infrastructure core that is independent from any specific end-user application.

### Focus areas

- identify and isolate the pseudonymization and re-identification logic
- define architecture boundaries between core, configuration, and interfaces
- clarify project-owned logic versus external dependencies
- document non-goals and trust-sensitive assumptions
- prepare a repository structure that reflects separation of concerns

### Intended result

A well-defined and documented core architecture that can be maintained and extended independently from the original application context.

## Phase 2: Harden the transformation model

### Goal

Turn the extracted logic into a more robust and reusable core component.

### Focus areas

- stabilize placeholder generation and mapping behavior
- improve consistency of reversible pseudonymization flows
- make rule handling more explicit and maintainable
- reduce architectural friction between transformation logic and surrounding application logic
- prepare the core for isolated testing and reliable reuse

### Intended result

A hardened transformation core with clearer internal contracts and better suitability for infrastructure use.

## Phase 3: Define configuration and rule handling

### Goal

Provide a maintainable configuration model for protection rules and controlled reuse in different environments.

### Focus areas

- define how terms, categories, and patterns are represented
- support rule maintainability and clarity for users or organizations
- prepare for versionable configuration structures
- prepare for secure handling of sensitive mappings or configuration-related data
- document how rule-based control differs from automatic privacy detection

### Intended result

A documented configuration model that supports explicit, reviewable, and maintainable protection rules.

## Phase 4: Provide integration interfaces

### Goal

Make the core usable in different technical contexts through standard integration paths.

### Focus areas

- define library integration boundaries
- prepare a CLI for scripted and batch-oriented workflows
- prepare a proxy mode for AI and LLM request flows
- prepare a local API surface for internal services and system integrations
- document interface assumptions and intended usage patterns

### Intended result

A reusable infrastructure component that can be embedded, scripted, proxied, or accessed locally by other systems.

## Phase 5: Strengthen maintenance and resilience

### Goal

Improve the long-term maintainability and resilience of the project.

### Focus areas

- improve separation between core logic and surrounding layers
- support more reliable testing and structured release preparation
- keep critical dependencies limited and well-scoped
- document trust assumptions and security-relevant boundaries
- make the architecture easier to review and extend responsibly

### Intended result

A project structure that is better suited for ongoing maintenance, review, security work, and future contribution.

## Phase 6: Documentation and reference integrations

### Goal

Make the project understandable and adoptable by third parties.

### Focus areas

- document architecture, trust model, and non-goals
- provide reference integration patterns
- describe realistic deployment and usage scenarios
- clarify where the project fits into local or internal AI workflows
- make assumptions and limits easy to inspect

### Intended result

A documented and reusable infrastructure project that other developers and organizations can evaluate and integrate more easily.

## Near-term priorities

The near-term priorities are:

1. define and document the core architecture
2. extract and harden the pseudonymization core
3. define maintainable rule and configuration handling
4. establish integration paths for library, CLI, proxy, and API use
5. document trust assumptions, limits, and integration patterns

## What success looks like

In the near to medium term, success means:

- the project has a clear and reusable core
- pseudonymization and re-identification are no longer tied to a single application structure
- interfaces are documented and integration-oriented
- trust assumptions are explicit and reviewable
- the project is easier to maintain, test, and extend
- third parties can understand where and how to adopt it

## What this roadmap does not prioritize

The roadmap does not prioritize:

- turning the repository into a user-facing product
- rapid expansion into many unrelated features
- opaque or autonomous privacy decisions
- cloud-first deployment assumptions
- growth at the expense of architectural clarity

## Long-term direction

The long-term direction is an auditable, locally operable, and reusable open-source infrastructure component that can serve as a privacy layer in AI and LLM workflows.

The project should become easier to integrate, easier to review, and more sustainable to maintain over time.
