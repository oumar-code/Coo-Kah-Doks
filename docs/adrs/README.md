# Architectural Decision Records (ADRs)

## What is an ADR?

An Architectural Decision Record (ADR) is a document that captures an important architectural decision made during the design or operation of the Coo-Cah manufacturing ecosystem. It records:
- The **context** that led to the decision
- The **options** that were considered
- The **decision** that was made and why
- The **consequences** of that decision (positive and negative)

ADRs provide a permanent, traceable record of *why* things are built the way they are — preventing well-intentioned future changes that would unknowingly reverse carefully considered decisions.

---

## ADR Process

### When to Write an ADR

Write an ADR when making decisions that:
- Affect the technology stack of multiple factories or the entire group
- Involve a buy-vs-build choice for major systems (MES, ERP, AI platform, EMS)
- Change a group-wide standard (protocol, data format, sensor type)
- Commit significant capital to a technology path
- Have implications for energy, safety, or compliance

You do **not** need an ADR for:
- Routine configuration decisions within an already-chosen platform
- Choices that affect only a single factory and can be easily reversed
- Cosmetic or UI decisions

### How to Propose an ADR

1. **Open a GitHub issue** using the [ADR Proposal template](../../.github/ISSUE_TEMPLATE/adr-proposal.yml)
2. **Draft the ADR** using the [ADR template](#adr-template) below
3. **Submit a Pull Request** to add the ADR to `docs/adrs/`
4. **Review period:** Minimum 5 business days; all relevant stakeholders must review
5. **Approval:** Group CTO (or delegate) merges the approved ADR

### ADR Status Values

| Status | Meaning |
|--------|---------|
| `PROPOSED` | Under review; not yet approved |
| `ACCEPTED` | Approved and active; architecture follows this decision |
| `DEPRECATED` | Superseded by a newer ADR; no longer followed for new work |
| `SUPERSEDED` | Replaced by a specific newer ADR (referenced in the document) |
| `REJECTED` | Considered but not adopted; kept for historical record |

---

## ADR Template

```markdown
# ADR-NNN: [Short title describing the decision]

**Status:** PROPOSED | ACCEPTED | DEPRECATED | SUPERSEDED | REJECTED  
**Date:** YYYY-MM-DD  
**Deciders:** [Names or roles of decision-makers]  
**Technical Story:** [Link to relevant issue or epic]

---

## Context

[Describe the situation that led to this decision. What problem are we solving?
What constraints do we operate under (technical, financial, regulatory, operational)?]

## Decision Drivers

- [Key driver 1]
- [Key driver 2]
- [Key driver 3]

## Options Considered

### Option 1: [Name]
**Description:** [What this option involves]  
**Pros:** [Advantages]  
**Cons:** [Disadvantages]  
**Cost estimate:** [CapEx/OpEx impact]

### Option 2: [Name]
...

### Option 3: [Name]
...

## Decision

[State the chosen option clearly. Explain the primary reasoning.]

## Consequences

### Positive
- [Positive outcome 1]
- [Positive outcome 2]

### Negative / Trade-offs
- [Negative consequence or trade-off 1]
- [Negative consequence or trade-off 2]

### Risks
- [Risk 1 and mitigation]
- [Risk 2 and mitigation]

## Compliance Notes

[Any regulatory or standards compliance implications of this decision.]

## Review Date

[Date at which this ADR should be reviewed for continued validity, if applicable.]
```

---

## ADR Index

| ADR | Title | Status | Date | Domain |
|-----|-------|--------|------|--------|
| [ADR-001](ADR-001-energy-source-selection.md) | Energy Source Selection for Coo-Cah Factories | ACCEPTED | 2025-01-15 | Energy |
| [ADR-002](ADR-002-mes-platform-selection.md) | MES Platform Selection | ACCEPTED | 2025-02-10 | Manufacturing |
| [ADR-003](ADR-003-digital-twin-platform.md) | Digital Twin Platform Selection | ACCEPTED | 2025-03-05 | Digital Twin |
| [ADR-004](ADR-004-amr-fleet-platform.md) | AMR Fleet Platform Selection | ACCEPTED | 2025-03-18 | Automation |
| [ADR-005](ADR-005-erp-platform.md) | ERP Platform Selection | ACCEPTED | 2025-04-01 | Enterprise IT |
| [ADR-006](ADR-006-ai-platform-architecture.md) | Central AI Platform Architecture | ACCEPTED | 2025-04-15 | AI / Infrastructure |

---

## Governance

- **ADR Owner:** Group CTO (Coo-Cah Rwanda OpCo)
- **Review Cadence:** All accepted ADRs reviewed annually for continued relevance
- **Superseding:** New ADRs explicitly reference and supersede older ADRs they replace
- **Storage:** All ADRs stored in this repository under `docs/adrs/`

---

*Questions about the ADR process: architecture@coocah.com*
