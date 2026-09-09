# Prefer SVG over PNG for Rendered Mermaid Diagrams

## Context

Rendered Mermaid diagrams may be exported as vector SVG files or raster PNG files. SVG preserves sharp lines and text at different display sizes and remains inspectable as structured markup. PNG has broader compatibility in environments that cannot display SVG, but its fixed resolution makes it less suitable as the default artifact for diagrams.

We need a clear output-format preference that is independent of which Mermaid rendering tool produces the artifact.

## Decision

We will use SVG as the primary output format for rendered Mermaid diagrams. When an environment cannot use SVG, we may generate PNG output as a fallback.

## Consequences

Positive consequences:

- Diagrams remain sharp when scaled or displayed at different sizes.
- Text and graphical elements remain inspectable in the generated artifact.
- Authors have a consistent default output format regardless of the rendering tool.
- PNG remains available for environments that cannot display SVG.

Negative consequences:

- Some publishing environments reject SVG or apply stricter security controls to it.
- Consumers that require PNG need an additional rendering or conversion step.
- SVG output can vary between rendering tools and versions even though the selected format is the same.
- PNG fallbacks are not scalable and may be less accessible or harder to inspect than SVG or Mermaid source.

## Alternatives Considered

**Use PNG as the primary output format**. PNG is widely supported, but it loses the scalability and inspectability of SVG.

**Generate both SVG and PNG for every diagram**. This maximizes compatibility, but it duplicates generated artifacts and increases maintenance and verification work.

**Require SVG without a fallback**. This keeps the artifact policy simple, but it excludes environments that cannot display or accept SVG.
