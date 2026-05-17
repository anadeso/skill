---
name: critical-review
description: Use this skill whenever the user wants you to analyze, review, validate, or audit technical documentation, specifications, requirements, API docs, design documents, implementation guides, or any other structured documentation for quality issues. Use it when the user mentions "review", "check", "analyze for issues", "validate", "audit", "quality check", or asks you to find problems/contradictions/ambiguities/gaps. Even if they don't explicitly ask to review something, use this skill whenever you suspect documentation quality might be an issue — for instance if they're confused about something in a specification, or if they mention contradictions between different documents.
---

# Critical Review Skill

This skill analyzes technical documentation systematically to identify quality issues that could cause confusion, misinterpretation, or implementation errors.

## Four Types of Issues

### 1. Contradictions
Statements that conflict with each other or contradict the overall intent:
- "The API returns JSON" vs. "responses are XML"
- "Field X is required" vs. schema shows it as optional
- Different sections describe the same behavior differently
- Code implementation differs from documented behavior

### 2. Ambiguities
Vague language, undefined terms, or multiple possible interpretations:
- Undefined terms: "handle errors gracefully" (what counts as graceful?)
- Vague measurements: "should be fast" (target latency?)
- Unclear conditionals: "if needed" (when?)
- Missing specifics: "use standard practices" (which practices?)

### 3. Inconsistencies
Different names, formats, or conventions for the same concept:
- Parameter names vary: `user_id`, `userId`, `id`
- Endpoint formats inconsistent: `/users/{id}/posts` vs `/user/posts/{id}`
- Time formats mixed: ISO 8601 vs. Unix timestamps
- Naming conventions shift: `getUser()` vs. `fetch_user()`

### 4. Logical Gaps
Missing steps, incomplete explanations, breaks in reasoning:
- Workflow described as "Step 1 → Step 2 → Step 4" (Step 3 missing)
- Error handling mentioned but recovery process undefined
- Prerequisites mentioned without setup instructions
- Circular dependencies that can't be resolved

## Analysis Process

1. **Understand the document's purpose** — What is it defining or explaining?
2. **Identify core concepts** — What are the main ideas?
3. **Check for contradictions** — Do statements conflict with each other or the overall intent?
4. **Find ambiguous language** — What terms are undefined? What could be misinterpreted?
5. **Trace consistency** — Do key concepts use consistent naming and formatting throughout?
6. **Map logical flow** — Are all steps present? Do processes complete without gaps?
7. **Consider implementation** — How would someone actually use this documentation?

## Output Format

ALWAYS use this exact structure for your analysis:

```
# Critical Review: [Document Title/Type]

## Summary
[2-3 sentences describing the document and its scope]

## Contradictions
- **[Term/Concept]**: [Description of conflict between statements]
  - Location 1: [Where first statement appears]
  - Location 2: [Where conflicting statement appears]
  - Impact: [Why this contradiction matters]

[List additional contradictions, or write "✓ No contradictions identified" if none found]

## Ambiguities
- **[Vague term or concept]**: [Explanation of what's unclear]
  - Issue: [Specifically what could be misinterpreted]
  - Questions: [What needs clarification]

[List additional ambiguities, or write "✓ No ambiguities identified" if none found]

## Inconsistencies
- **[Concept]**: [Description of variations found]
  - Variant 1: [First form used]
  - Variant 2: [Different form used]
  - Locations: [Where each variation appears]

[List additional inconsistencies, or write "✓ No inconsistencies identified" if none found]

## Logical Gaps
- **[Process/Section]**: [Description of what's missing]
  - Missing piece: [What should be there]
  - Location: [Where the gap occurs]
  - Impact: [Why this gap matters]

[List additional gaps, or write "✓ No logical gaps identified" if none found]

## Overall Assessment
[Brief summary: e.g., "Well-structured with minor inconsistencies" or "Multiple critical contradictions need resolution"]

## Recommendations
[Specific, actionable suggestions for improving the documentation, OR if document is well-written: "No significant improvements needed"]
```

## Guidelines for Analysis

**Be thorough and fair:**
- Look for real issues, not nitpicks
- A document with minor style inconsistencies is "generally well-written" not "heavily flawed"
- Focus on issues that impact understanding or implementation

**Explain impact:**
- For each issue, explain why it matters
- How could this confuse someone trying to understand or implement it?

**Provide specifics:**
- Quote or reference sections when possible
- Help the author identify exactly where to look

**Distinguish severity:**
- Major contradictions that break implementation ≠ cosmetic inconsistencies
- Reflect this in your recommendations

**Use document examples:**
- Reference specific examples if the document provides them
- Use actual quotes to illustrate issues

**Don't invent issues:**
- If something is clear and consistent, say so
- Write "✓ No [issue type] identified" rather than fabricating problems
- Distinguish between actual issues and stylistic preferences

## Common Scenarios

**API Specification:**
- Check: endpoint naming consistency, parameter format consistency, authentication claims vs. actual requirements, response format claims
- Watch for: "all public" claim with later authentication requirements

**Requirements Document:**
- Check: defined acceptance criteria, consistent terminology, complete workflows, specific vs. vague terms
- Watch for: undefined metrics ("efficient", "fast", "reasonable")

**Implementation Guide:**
- Check: all steps included, prerequisites explained, example completeness, state after each step
- Watch for: missing setup steps, undefined configuration options

**Technical Design:**
- Check: component dependencies, data flow clarity, role/responsibility definitions
- Watch for: circular dependencies, missing integration points

## When in Doubt

If you're unsure whether something is an actual issue:
- **Ask the question**: Flag it as a potential ambiguity
- **Be conservative**: Only report things that could reasonably cause problems
- **Explain your reasoning**: Help the author understand your concern
