# Prefer Hand-Drawn Style for Mermaid Diagrams

## Context

Mermaid diagrams in this project are primarily used to communicate architecture. A sketch-like appearance is commonly associated with early design work and makes diagrams feel approachable, discussion-oriented, and easy to revise. This helps readers focus on architectural relationships and ideas rather than mistaking visual polish for a finalized design.

Mermaid supports this appearance through the `handDrawn` look.

## Decision

We will prefer Mermaid's hand-drawn style for architecture diagrams by setting `look: handDrawn` in the diagram configuration.

We may use a different style when a diagram has requirements that the hand-drawn look does not satisfy, such as strict visual consistency with an external design system or clearer rendering for a particular output format.

## Consequences

Positive consequences:

- Architecture diagrams have an informal, sketch-like appearance that encourages discussion and iteration.
- Readers can more readily distinguish conceptual architecture diagrams from polished user-interface designs or exact implementation specifications.
- Diagrams use a consistent visual language that is well suited to communicating architecture.

Negative consequences:

- Hand-drawn rendering may be less suitable for formal publications, compact diagrams, or contexts requiring precise visual alignment.
- Rendering can vary across Mermaid versions and tools, so exported diagrams may need visual verification.

## Alternatives Considered

**Use Mermaid's default style**. This requires less configuration and provides a conventional appearance, but it does not convey the same sketch-like, discussion-oriented character.

**Require hand-drawn style for every diagram**. This maximizes consistency, but it prevents authors from choosing a clearer style when publishing constraints or diagram complexity make hand-drawn rendering unsuitable.
