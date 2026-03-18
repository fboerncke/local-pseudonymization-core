# Local Pseudonymization Core

Open infrastructure for local, reversible pseudonymization in AI and LLM workflows.

## Overview

Local Pseudonymization Core is an open-source infrastructure component for protecting sensitive text data before it is sent to AI systems.

It pseudonymizes configured terms, categories, and patterns locally, forwards the transformed text to an LLM or AI endpoint, and restores the protected content afterwards in the returned result.

The project is designed as a reusable building block rather than an end-user application. Its goal is to provide a transparent, locally controlled privacy layer that can be integrated into existing software, internal workflows, and self-hosted AI environments.

## Why this exists

Many organizations want to use AI systems in contexts that involve confidential or personal text data. In practice, they often face three unsatisfactory options:

- avoid AI completely
- use manual redaction and copy-paste workarounds
- depend on proprietary or cloud-based privacy gateways

What is missing in the open-source ecosystem is a reusable, locally operated component for reversible pseudonymization that can sit between sensitive text workflows and AI endpoints.

Local Pseudonymization Core is intended to fill that gap.

## Conceptual flow

```text
Sensitive text
    ↓
Local rule-based pseudonymization
    ↓
Transformed text sent to AI / LLM endpoint
    ↓
AI response
    ↓
Local re-identification
    ↓
Restored result
```

## What the project does

Local Pseudonymization Core is intended to provide:

- a local core for rule-based pseudonymization and re-identification
- explicit and maintainable protection rules defined by users or organizations
- integration interfaces for use as a library, CLI, proxy, or API
- support for local and internal deployment scenarios
- transparent and auditable handling of sensitive text transformations

## What makes this different

This project is based on a simple principle:

**The system should not autonomously decide what is private.**

What should be protected depends on context, organization, workflow, and individual judgment. One user may want their name to remain visible, but not their address. Another organization may need to protect case IDs, project names, or internal terminology.

For that reason, Local Pseudonymization Core does not aim to be a “magic privacy AI”.
Instead, it focuses on:

- explicit and maintainable rules
- local control over protection decisions
- optional assistance, but no hidden automatic trust assumptions
- reproducible and reviewable behavior

## Intended use cases

Local Pseudonymization Core is intended for integration into systems such as:

- internal AI gateways
- local LLM workflows
- editorial systems
- legal and administrative software
- healthcare-related documentation workflows
- NGO and public-sector text processing pipelines
- custom applications that need local privacy protection before AI usage

## Intended users

The primary users of this project are:

- developers integrating privacy-preserving AI workflows
- administrators and technical teams operating local AI infrastructure
- organizations working with sensitive text data
- maintainers of tools that want to add local pseudonymization as an infrastructure layer

## Relationship to Private Prompts

Local Pseudonymization Core builds on experience and technical groundwork developed in the Private Prompts prototype.

The prototype explored local pseudonymization from an end-user application perspective.
This repository focuses on the extracted infrastructure core: a reusable, documented, and integrable component intended for use beyond a single application.

In other words:

- **Private Prompts prototype** = application-oriented precursor
- **Local Pseudonymization Core** = reusable infrastructure component

## Architecture goals

The project is being structured around a clear separation of concerns:

- pseudonymization and re-identification core logic
- rule and configuration handling
- local storage and secure configuration handling
- integration interfaces
- documentation and reference integration patterns

The long-term goal is a component that is:

- locally operable
- auditable
- modular
- testable
- integrable into other systems
- maintainable over time

## Non-goals

This project is **not** intended to be:

- a cloud privacy gateway
- a proprietary trust service
- an end-user chat application
- an autonomous AI that decides on its own what is private
- a promise of perfect anonymization in all contexts

## Security and trust model

Local Pseudonymization Core is based on the idea that software dealing with sensitive text transformations must be transparent and reviewable.

Open source does not automatically create security.
But it does create the conditions for:

- auditability
- independent review
- transparent data flow assumptions
- verifiable protection logic
- long-term digital sovereignty

Sensitive decisions should remain under the control of users and organizations, not inside opaque vendor systems.

## Planned interfaces

The project is intended to support multiple integration paths:

- **Library** for embedding in other applications
- **CLI** for scripted and batch usage
- **Proxy** for AI/LLM workflow interception
- **API** for integration into local or internal services

## Planned deliverables

The initial development phase is focused on:

1. extracting and hardening the pseudonymization core
2. defining maintainable rule and configuration handling
3. providing standard integration interfaces
4. documenting architecture, assumptions, and limits
5. preparing the project for reliable testing, maintenance, and reuse

## Current status

This repository represents the infrastructure-focused continuation of earlier prototype work.

The project is currently in the phase of defining scope, architecture boundaries, and reusable interfaces for an open-source core that can support real-world integrations.

## Contributing

Contributions, feedback, testing, integration ideas, and issue reports are welcome.

The core implementation is being developed with a strong focus on architectural consistency, security assumptions, and maintainability. For that reason, contribution paths will be introduced carefully and documented clearly as the project structure stabilizes.

## License

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

The AGPL is intended to ensure that improvements to the software remain available to the public, including when the software is used as part of network-accessible services.

## Contact

Project lead: Frank Börncke  
Website: https://boerncke.de
