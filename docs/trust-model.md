# Trust Model

## Purpose

Local Pseudonymization Core is intended for scenarios in which sensitive text must be protected before being sent to AI or LLM systems.

This document describes the trust assumptions behind the project and clarifies which parts of the workflow are meant to remain under local control.

## Core trust assumption

The project is based on a simple principle:

**Protection decisions should remain under the control of users and organizations handling the data.**

The system is not designed to autonomously decide what is private in every context. Instead, it is designed to apply explicit, reviewable protection rules and to make sensitive data flows easier to understand, control, and audit.

## Why a trust model is needed

Software that promises privacy or security can create false confidence if its assumptions are not clear.

In this problem space, trust is affected by questions such as:

- where sensitive text is processed
- who defines what should be protected
- whether transformation logic can be reviewed
- whether external providers must be trusted
- whether restored output can be traced back to explicit rules and mappings

For that reason, the trust model is a central part of the project rather than an afterthought.

## Trust boundaries

The project treats the following points in the workflow as trust-sensitive boundaries:

1. **Sensitive input enters the system**  
   Original text may contain personal data, confidential terms, internal identifiers, or other protected information.

2. **Rules define what should be protected**  
   Protection is based on explicit categories, terms, patterns, or organizational rules.

3. **Local pseudonymization transforms the text**  
   Sensitive values are replaced with placeholders before any downstream AI request.

4. **Transformed text leaves the protected boundary**  
   Only the pseudonymized text should be forwarded to an external AI or LLM endpoint.

5. **Returned output is processed locally**  
   Re-identification happens inside the local or controlled environment.

6. **Protected values are restored in context**  
   The final output is reconstructed based on local rules and mappings.

## Main trust assumptions

### 1. Local processing is preferred

The architecture assumes that sensitive transformations should happen locally or inside an organization's controlled environment whenever possible.

The goal is to reduce reliance on external privacy gateways or opaque service providers for the protection step itself.

### 2. Protection rules are explicit

The project assumes that what should be protected is context-dependent.

A name may be acceptable in one context and sensitive in another. An address, case number, project name, or internal term may require protection depending on organizational practice or legal obligations.

For that reason, the trust model is based on explicit rules rather than hidden automatic judgments.

### 3. Open source supports justified trust

Open source does not guarantee security by itself.

However, in this context it provides important conditions for justified trust:

- reviewability of protection logic
- visibility of data flow assumptions
- independent auditing
- scrutiny of security claims
- shared improvement of trust-sensitive code

This is especially important for software that claims to reduce privacy and confidentiality risks.

### 4. External AI providers are not trusted with original sensitive text

The project assumes that external AI or LLM services should not receive original sensitive values if those values can be protected locally first.

This does not eliminate all risk, but it reduces unnecessary exposure and narrows the trust placed in external systems.

### 5. Assistance is not authority

Optional NLP-based assistance may help identify candidate terms or categories for protection in the future.

But such assistance should remain advisory. Final protection decisions should remain explicit and under user or organizational control.

## What the project is intended to trust

The project is intended to place trust in:

- locally controlled execution environments
- explicit, maintainable protection rules
- reviewable transformation logic
- documented interfaces and assumptions
- auditable open-source code

## What the project is intended not to trust blindly

The project is intended to avoid blind trust in:

- opaque vendor privacy claims
- proprietary transformation logic
- cloud services acting as privacy intermediaries
- automatic systems deciding on their own what is sensitive
- undocumented data flow behavior

## Residual risks

This project is not a guarantee of perfect privacy or perfect anonymization.

Residual risks may still exist, for example:

- incomplete or incorrect protection rules
- context leakage through surrounding text
- errors in rule configuration
- inappropriate assumptions about downstream model behavior
- operational mistakes in local deployment or integration

For that reason, the project should be understood as a controllable and reviewable privacy layer, not as a complete elimination of risk.

## Security-relevant implications

The trust model implies several architectural priorities:

- keep transformation steps local whenever possible
- make rules maintainable and inspectable
- document assumptions and non-goals clearly
- separate core logic from provider-specific integrations
- avoid unnecessary critical dependencies
- support testing and review of trust-sensitive behavior

## Non-goals

The trust model does not assume that the project can provide:

- fully automatic determination of what is private
- universal anonymization for every domain and language
- elimination of all confidentiality risks
- trustworthiness through branding or vendor assurances alone

## Long-term objective

The long-term objective is to support a form of privacy-preserving AI integration in which trust is earned through:

- local control
- explicit rules
- open review
- understandable data flow boundaries
- auditable infrastructure

In that sense, Local Pseudonymization Core aims to reduce unnecessary trust assumptions and replace them with transparent, reviewable mechanisms.
