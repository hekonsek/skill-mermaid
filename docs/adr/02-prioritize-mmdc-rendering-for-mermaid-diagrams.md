# Prioritize mmdc Rendering for Mermaid Diagrams

## Context

Mermaid diagrams can be rendered by several tools, but those tools do not support every Mermaid feature or visual enhancement consistently. A diagram may render with hand-drawn styling, extra icons, or other aesthetics in one tool while another tool ignores or cannot display those enhancements.

We need a clear renderer priority so authors know which output defines the intended presentation and how much compatibility to preserve for other viewing environments.

## Decision

We will use the `mmdc` command as the primary renderer for Mermaid diagrams.

We will support renderers in this order:

1. `mmdc`.
2. GitHub Markdown's Mermaid renderer.
3. The VS Code Mermaid Preview plugin.

We will create diagrams that can be parsed, rendered, and read in each renderer, in priority order. The primary renderer defines the intended presentation. Lower-priority renderers do not need to reproduce optional aesthetics such as hand-drawn styling, extra icons, or similar visual enhancements, provided that the diagram remains parseable, renders successfully, and communicates its content clearly.

## Consequences

Positive consequences:

- `mmdc` provides a consistent primary rendering that can be visually verified.
- The explicit renderer order gives authors a predictable target when Mermaid implementations behave differently.
- Diagrams remain accessible in common repository and editor workflows even when those environments omit nonessential aesthetics.

Negative consequences:

- Authors may need to avoid Mermaid syntax or features that prevent a diagram from rendering in GitHub Markdown or the Code Mermaid Preview plugin.
- The same diagram may look different across renderers because lower-priority renderers are not required to preserve all aesthetics.
- Verifying compatibility across multiple renderers adds maintenance effort.
- Using `mmdc` requires maintaining its runtime and browser dependencies.

## Alternatives Considered

**Treat every renderer as equally authoritative**. This would maximize visual consistency across tools, but the least capable renderer would constrain every diagram and prevent useful enhancements in the primary output.

**Support only `mmdc`**. This would simplify rendering and validation, but diagrams would be less useful when read directly on GitHub or previewed in the editor.

**Use GitHub Markdown as the primary renderer**. This would optimize diagrams for repository browsing, but it provides less control over rendering behavior and does not support every enhancement available through `mmdc`.
