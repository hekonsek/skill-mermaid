# Place Mermaid Comments on Separate Lines

## Context

Mermaid renderers do not interpret comments consistently. Inline comments may be parsed successfully by `mmdc`, while GitHub Markdown and the Code Mermaid Preview plugin can fail to parse or render the same diagram.

Comments within Mermaid configuration frontmatter are also not interpreted reliably by the Code Mermaid Preview plugin. Because this project supports all three renderers, comment placement must follow the syntax accepted by the least tolerant supported renderer.

## Decision

We will place each Mermaid comment on its own line. A comment will begin with Mermaid's `%%` comment marker at the start of a new line and will not follow a diagram statement on the same line.

We will not place comments anywhere within Mermaid configuration frontmatter. Configuration must contain only configuration data.

For example, we will use:

```mermaid
%% Explain a non-obvious relationship.
producer --> consumer
```

We will not use:

```mermaid
producer --> consumer %% Explain a non-obvious relationship.
```

## Consequences

Positive consequences:

- Mermaid sources parse more consistently in `mmdc`, GitHub Markdown, and the Code Mermaid Preview plugin.
- Comments remain readable without interfering with diagram statements or configuration parsing.
- Authors have a simple, renderer-independent rule for comment placement.

Negative consequences:

- Comments consume additional vertical space and cannot annotate a statement on the same line.
- Configuration choices that need explanation must be documented outside the configuration frontmatter.
- Existing diagrams with inline or configuration comments may require revision.

## Alternatives Considered

**Allow inline comments when `mmdc` is the primary renderer**. This permits more compact source, but it can break parsing or rendering in GitHub Markdown and the Code Mermaid Preview plugin.

**Allow comments within Mermaid configuration frontmatter**. This keeps configuration explanations close to the relevant setting, but the Code Mermaid Preview plugin does not interpret such comments reliably.

**Avoid Mermaid comments entirely**. This maximizes compatibility, but it prevents authors from recording non-obvious modeling choices next to the diagram source.
