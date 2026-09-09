---
name: skill-mermaid
description: Create, edit, render, and review Mermaid architecture diagrams. Use for Mermaid source files, Mermaid code blocks, architecture visualizations, renderer compatibility, or SVG and PNG diagram exports.
license: MIT
compatibility: Primary rendering and full visual validation require the Mermaid CLI (`mmdc`). GitHub Markdown and VS Code Mermaid Preview are secondary compatibility targets.
---

# Mermaid architecture diagrams

Produce approachable Mermaid diagrams that remain readable across supported renderers.

## Workflow

1. Inspect the surrounding documentation, existing diagrams, and required output location before editing.
2. Choose the simplest Mermaid diagram type that communicates the architecture. Prefer a generic flowchart unless a specialized diagram adds necessary meaning.
3. Give nodes explicit, reader-facing labels and use shapes that convey meaning, such as cylinders for databases and Mermaid's `das` shape for queues when supported.
4. Add Mermaid configuration frontmatter and prefer the hand-drawn look:

   ```mermaid
   ---
   config:
     look: handDrawn
   ---
   flowchart LR
       producer[Producer] --> queue@{ label: "Message Queue", shape: das }
       queue --> consumer[Consumer]
       consumer --> database[(Database)]
   ```

   Use another look when hand-drawn rendering conflicts with an external design system, formal publishing requirements, compact layout, precise alignment, or output clarity.
5. Keep each Mermaid comment on a separate line. Start it with `%%`; never append it to a statement and never put comments in configuration frontmatter.
6. Keep source compatible with renderers in this priority order:

   1. Mermaid CLI (`mmdc`), which defines the intended presentation.
   2. GitHub Markdown's Mermaid renderer.
   3. VS Code Mermaid Preview.

   Optional aesthetics may degrade in secondary renderers, but every supported renderer must parse the source, render it, and communicate the diagram clearly. Avoid or replace syntax that breaks a secondary renderer.
7. Render SVG by default:

   ```sh
   mmdc -i path/to/diagram.mmd -o path/to/diagram.svg
   ```

   Use PNG only when the target environment cannot display or accept SVG. Do not generate both formats without a concrete consumer requirement.
8. Inspect the rendered artifact. Confirm that labels are legible, edges connect the intended nodes, the layout communicates the architecture, and optional styling has not obscured meaning. When the relevant environments are available, also preview the source in GitHub Markdown and VS Code Mermaid Preview.

## Comment syntax

Use:

```mermaid
%% Explain a non-obvious relationship.
producer --> consumer
```

Do not use:

```mermaid
producer --> consumer %% Explain a non-obvious relationship.
```

## Completion checks

- The diagram models the requested architecture without unnecessary detail.
- `look: handDrawn` is present unless a documented constraint justifies another look.
- Comments occupy their own lines and configuration frontmatter contains data only.
- `mmdc` renders the source successfully.
- Secondary renderers can parse and communicate the diagram, even if optional aesthetics differ.
- The primary rendered artifact is SVG unless SVG is unsuitable for its destination.
- The rendered output has been inspected visually, not merely generated.
