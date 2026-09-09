---
name: skill-mermaid
description: Create and edit Mermaid architecture diagrams.
---

# Mermaid architecture diagrams

Produce approachable Mermaid diagrams.

## References

- Use [api.mmd](references/api.mmd) as a reference for modeling an API architecture. For example for user consuming an API that interacts with a database or other systems.
- Use [events.mmd](references/events.mmd) as a reference for modeling event-driven architectures. For example for system consisting of producers, message queues, and consumers.

## ADRs

- Use [this ADR](adr/01-prefer-hand-drawn-style-for-mermaid-diagrams.md) when deciding on the visual style for Mermaid diagrams.
- Use [this ADR](adr/02-prioritize-mmdc-rendering-for-mermaid-diagrams.md) when deciding on the preferred rendering tool for Mermaid diagrams.
- Use [this ADR](adr/03-place-mermaid-comments-on-separate-lines.md) when deciding on the comment syntax for Mermaid diagrams.
- Use [this ADR](adr/04-prefer-svg-over-png-for-rendered-mermaid-diagrams.md) when deciding on the default output format for Mermaid diagrams.

