---
name: project-feature-explainer
description: "Generates structured feature explanations with summaries, code walkthroughs, usage examples with sample inputs/outputs, and Mermaid sequence/workflow diagrams. Uses references/explanation-template.md for output structure and references/checklist.md for verification. Use when the user asks how a feature works, requests a feature walkthrough, needs feature documentation, or wants to understand a specific capability in the codebase."
---

# Project Feature Explainer

## Workflow

1. **Identify Entry Points:** Use Grep to search for route definitions, exported functions, or API endpoints that trigger the feature.
2. **Trace Dependencies:** Use Read to examine imports and identify internal modules, services, or external APIs the feature relies on.
3. **Analyze Data Flow:** Map how data enters, transforms, and exits — note side effects (DB writes, cache invalidation, events).
4. **Draft Explanation:** Structure output using `references/explanation-template.md`. Refer to `references/example-output.md` for formatting and depth expectations.
5. **Verify Completeness:** Cross-reference with `references/checklist.md` before delivering.

## Mandatory Output Structure

### 1. Feature Summary
1–2 paragraphs: *what* the feature does and *why* it exists.

### 2. Technical Deep Dive
- **Key Components:** List files, classes, and functions involved with paths.
- **Logic Flow:** Step-by-step execution path.
- **State Changes:** Side effects (database updates, cache invalidation, events emitted).

### 3. Usage & Examples
- Code snippets or CLI commands with common parameters and expected outputs.
- Include a "Happy Path" example.

### 4. Sequence / Workflow Diagram
- Include a Mermaid diagram showing the interaction between components.

## References

- `references/explanation-template.md` — mandatory output template.
- `references/example-output.md` — example of a complete feature explanation.
- `references/checklist.md` — verification checklist (use before delivering).
