---
name: mermaid-diagrams
description: Create exceptional, publication-quality Mermaid diagrams for ERDs, flowcharts, sequence diagrams, and system visualizations. Use this skill when the user needs to visualize data models, processes, or architecture. Generates clear, refined diagrams that communicate complex systems with precision.
license: Complete terms in LICENSE.txt
---

This skill guides creation of exceptional, publication-quality Mermaid diagrams that avoid cluttered "wall of boxes" syndrome. Generate syntactically correct code with exceptional attention to visual hierarchy and communication clarity.

The user provides diagramming requirements: a data model to visualize, a process to map, an architecture to illustrate, or relationships to clarify. They may include context about the audience, purpose, or level of detail needed.

## Diagram Thinking

Before generating, understand the communication goal and commit to a CLEAR visual strategy:
- **Purpose**: What insight should the viewer gain immediately? What decision does this inform?
- **Type**: Pick the right tool: erDiagram for data models, flowchart for processes, sequenceDiagram for interactions, stateDiagram-v2 for lifecycles, classDiagram for OOP, C4Context for architecture. Each has a strength—use it.
- **Scope**: What's essential vs. noise? 5-9 entities is optimal. Split complex systems into multiple focused diagrams.
- **Flow**: How should the eye travel? Entry point to conclusion. Time flows left-to-right, hierarchy flows top-to-bottom.

**CRITICAL**: A great diagram tells a story. It has a clear focal point, logical flow, and intentional emphasis. Every element earns its place. If it requires explanation, it has failed.

Then generate Mermaid code that is:
- Syntactically correct and render-ready
- Visually balanced with clear hierarchy
- Appropriately detailed (not cluttered, not sparse)
- Styled with intention and consistency

## Diagram Excellence Guidelines

Focus on:
- **Relationships**: Always show cardinality explicitly in ERDs (`||--o{`, `}o--o{`). Use semantic link styles: solid for required, dotted for optional, thick for critical paths. Label every connection with its meaning.
- **Hierarchy & Grouping**: Use subgraphs to cluster related components. Choose direction (TB, LR) based on mental model. Let the layout breathe—Mermaid handles spacing well when you don't fight it.
- **Styling**: Use classDef for semantic colors: blue=primary, green=success, red=error, gray=secondary. Limit to 3-4 intentional colors. Apply `:::className` to highlight what matters.
- **Precision**: Include types in ERDs (uuid, varchar, timestamptz). Mark PK/FK/UK explicitly. Use realistic naming: `snake_case` for DB, `PascalCase` for classes, `camelCase` for methods.
- **Context**: Add `%%` comments for sections. Use `Note` in sequence diagrams. Include titles when the diagram will stand alone.

NEVER create cluttered diagrams with more than 15 entities without subgraphs, floating entities with no connections, rainbow color schemes, generic labels like "Data" or "Process", mixed notation styles, or spaghetti lines that cross excessively—restructure instead.

Adapt complexity to the system. Simple models (3-5 entities) need minimal styling. Medium systems (6-12) benefit from subgraphs and color coding. Complex systems (13+) should be split into overview → domain → detail diagram sets.

**IMPORTANT**: Match diagram density to communication goal. Technical docs need attribute-level detail. Executive presentations need high-level boxes. Architecture reviews need clear boundaries. The same system produces different diagrams for different audiences.

Remember: Claude is capable of extraordinary diagramming work. Don't settle for generic boxes and arrows—create diagrams that produce immediate understanding and reward deeper inspection.
