---
name: codebase-graph-lite
description: Map a codebase, trace callers or dependencies, and preview the impact of a proposed change with an evidence-backed Mermaid diagram. Use for architecture questions, request or command flows, and requests to understand code before editing.
---

# Codebase Graph Lite

Use the available file-reading and search tools. Work from the current source and configuration. This skill uses Markdown and Mermaid and requires no scripts, packages, or hooks.

## Trace the code

1. Scope the trace to the user's question. For a broad architecture map, start with project or package manifests and the application's entry points. For a specific flow, start with the command, route, job, or symbol the user named.
2. Read the relevant definitions and call sites. Follow interfaces through dependency injection registrations, including environment conditions when visible. In .NET, check endpoint mappings, command dispatch, the composition root, and project references as needed. Trace upward from the target when the user asks what might be affected.
3. Record the evidence for each relationship before you draw it. Distinguish calls, registrations, and project references by labeling them separately. A project reference establishes a dependency between projects. A call site establishes a call to the resolved symbol. For an interface call, cite the call site and the registration before drawing an edge to the implementation, and state any condition on that binding.
4. For reflection, generated code, feature flags, or runtime bindings you cannot resolve from the available files, show the point where the trace stops. If the source suggests a possible continuation, draw a dashed edge labeled with the condition or uncertainty and state what would confirm it. Treat existing maps and README files as navigation aids and check their claims against current source.

## Present the result

- Answer the question first. Draw the relevant architecture, branching, or call flow as a compact Mermaid diagram. Prefer `flowchart TD` when the diagram has several layers. Use short labels and label edges with their actual relationship. Use solid arrows for verified relationships and dashed arrows for inferred ones. Keep each diagram focused on one question.
- Add an evidence table with columns for relationship, source location, and what the source establishes. Give repo-relative paths and line numbers when available. For likely impact, distinguish confirmed callers from places that may be affected, and identify where the trace stopped.
- When asked to inspect or explain, keep the work read-only unless the user requests a saved map. When asked to inspect and then edit, share the pre-change map and the intended edit before changing files. After editing, verify and update any relationships the edit affected.
- If asked to save the map, write it as Markdown at the requested path, or use `docs/codebase-map.md` for a new repo-wide map. Include the scope and inspected revision if available. Mention any relevant uncommitted changes. When reusing a saved map, recheck the edges you rely on against current files.

## Write lasting documentation

When a mapping task produces documents for future maintainers, read [the documentation writing guide](references/writing-docs.md). Verify implementation and deployment claims against the relevant evidence and write for readers who have never seen the conversation.

When the task includes finishing a feature and preparing its PR or MR, read [the maintenance manual guide](references/maintenance-manual.md) and write or update the manual before submission. An analysis-only request remains read-only unless the user asks to save the result.
