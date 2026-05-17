# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Goal

Develop a Claude Code skill that analyzes specifications and documentation to identify and report:
- **Contradictions**: statements that conflict with each other or the specification
- **Ambiguities**: vague terms, undefined criteria, or multiple interpretations
- **Inconsistencies**: different names or formats used for the same concept
- **Logical gaps**: missing steps or breaks in reasoning chains

The skill will help users review technical documents, API specs, requirements, and other documentation for quality issues.

## Repository Structure

```
6.1-criando-skills/
├── CLAUDE.md                              # This file
├── prompt.md                              # Skill requirements (in Portuguese)
├── skills-lock.json                       # Dependency on skill-creator
├── .claude/skills/skill-creator/          # Skill development framework
│   ├── SKILL.md                           # Skill development workflow & reference
│   ├── scripts/                           # Development tools
│   │   ├── run_eval.py                    # Run evaluation tests
│   │   ├── run_loop.py                    # Optimize skill description
│   │   ├── aggregate_benchmark.py         # Aggregate test results
│   │   ├── quick_validate.py              # Validate skill structure
│   │   ├── generate_report.py             # Create test reports
│   │   └── improve_description.py         # Improve triggering accuracy
│   ├── eval-viewer/                       # HTML viewer for test results
│   ├── agents/                            # Specialized evaluation agents
│   └── references/                        # JSON schemas, documentation
└── <skill-name>-workspace/                # Created during development (iteration results)
```

## Skill Development Workflow

This project uses the **skill-creator** framework. Development follows these phases:

### 1. **Capture Intent & Draft** (initial phase)
   - Clarify what the skill should do (contradictions, ambiguities, inconsistencies, logical gaps)
   - When it should trigger (e.g., "review this specification", "check my documentation")
   - Expected output format (list of issues, detailed report, suggestions)
   - Write a draft SKILL.md with:
     - `name`: skill identifier (e.g., `spec-analyzer`)
     - `description`: when to trigger and what it does (make it "pushy" — include trigger contexts)
     - Instructions: detailed guidance for Claude on how to analyze documents

### 2. **Test & Evaluate**
   - Create 2-3 realistic test prompts in `evals/evals.json`
   - Spawn parallel test runs (with skill + baseline without skill)
   - Save outputs to `<skill-name>-workspace/iteration-1/`
   - Use the evaluation viewer to review results qualitatively

### 3. **Improve Based on Feedback**
   - Read user feedback from the viewer
   - Refine skill instructions based on what worked/didn't work
   - Rerun tests into `iteration-2/`, comparing against previous iteration
   - Repeat until results satisfy requirements

### 4. **Optimize Description**
   - Create 20 eval queries (mix of should-trigger and should-not-trigger)
   - Run description optimizer to improve triggering accuracy
   - Test trigger rates across realistic user prompts

## Development Commands

### Initialize Skill Structure
```bash
# Create the SKILL.md file with frontmatter:
# ---
# name: spec-analyzer          # or your chosen name
# description: When to use, what it does, trigger contexts
# ---

# Create initial test cases in evals/evals.json:
# {
#   "skill_name": "spec-analyzer",
#   "evals": [
#     {"id": 1, "prompt": "...", "expected_output": "...", "files": []}
#   ]
# }
```

### Run & Evaluate Tests
```bash
# Uses the skill-creator to spawn tests with and without your skill
# This happens in the background — check the workspace directory for results
python -m scripts.run_eval --skill-path <path-to-skill> --iterations 3

# View results in browser (qualitative outputs + quantitative benchmark)
# The viewer opens automatically with:
# - Outputs tab: review each test case with feedback textbox
# - Benchmark tab: pass rates, timing, token usage, analyst notes

# Save feedback.json after user reviews in the viewer
cat <workspace>/iteration-N/feedback.json
```

### Validate & Improve
```bash
# Quick validation of SKILL.md structure
python -m scripts.quick_validate <path-to-skill>

# Optimize description for better triggering (after tests pass)
python -m scripts.run_loop \
  --eval-set <path-to-trigger-eval.json> \
  --skill-path <path-to-skill> \
  --max-iterations 5
```

### Generate Reports
```bash
# Aggregate benchmark results from an iteration
python -m scripts.aggregate_benchmark <workspace>/iteration-N --skill-name spec-analyzer

# Generate markdown report of all results
python -m scripts.generate_report <workspace>/iteration-N --output report.md

# Package final skill for distribution
python -m scripts.package_skill <path-to-skill>
```

## Key Files During Development

- **`SKILL.md`** — the skill definition (name, description, detailed instructions)
- **`evals/evals.json`** — test cases with prompts and expected outputs
- **`scripts/`** — reusable helper scripts bundled with the skill (optional)
- **`references/`** — documentation files loaded as context (optional)
- **`<skill-name>-workspace/`** — test results organized by iteration
  - `iteration-1/eval-0/`, `eval-1/`, etc. — individual test results
  - `benchmark.json` — quantitative results summary
  - `feedback.json` — user reviews from the viewer

## Skill Writing Patterns

### SKILL.md Structure
```markdown
---
name: spec-analyzer
description: Use this skill whenever the user wants you to review or analyze technical documentation, specifications, requirements, or API docs for quality issues. Identify contradictions, ambiguities, inconsistencies, and logical gaps.
---

# Specification Analyzer

[Detailed instructions for how Claude should analyze documents...]

## Output Format
ALWAYS format your analysis as:
### Contradictions
- [issue]: [explanation]

### Ambiguities
- [term]: [what's unclear]

### Inconsistencies
- [concept]: [variants found]

### Logical Gaps
- [location]: [missing step]
```

### Defining Output Expectations
Use consistent formatting in test cases:
```json
{
  "prompt": "Review this API spec for issues...",
  "expected_output": "Structured report with sections for contradictions, ambiguities, inconsistencies, and gaps"
}
```

## Common Development Patterns

### Making a Skill Trigger Reliably
- Skill description should include specific contexts and trigger phrases
- Examples: "whenever the user mentions specs", "needs documentation review", "wants to validate requirements"
- Avoid making it too narrow — think about different ways users phrase this request
- Prioritize accuracy over coverage: better to miss some cases than falsely trigger

### Testing Edge Cases
- Test with incomplete documents (e.g., fragments, rough drafts)
- Test with documents in different domains (APIs, requirements, design docs)
- Test with intentionally broken specs (missing sections, contradictions)
- Test with well-written specs (ensure no false positives)

### Iterating on Instructions
- If tests show the skill missing issues, expand the definition or add examples
- If tests show it finding non-issues, constrain the scope or clarify criteria
- Look at the actual transcripts from test runs to see where time is wasted
- Prefer explanations of *why* something matters over rigid ALWAYS/NEVER rules

## Evaluation & Assertions

Good assertions for this skill should check:
- **Completeness**: Did it find all/most issues?
- **Accuracy**: Are reported issues actually valid?
- **Organization**: Is output in the expected format?
- **Usefulness**: Would a user find the analysis actionable?

Avoid assertions that require subjective judgment; those are better reviewed manually in the viewer.

## Workspace Organization

Once you start testing:
```
spec-analyzer-workspace/
├── iteration-1/
│   ├── eval-0/                       # Test case 1
│   │   ├── with_skill/outputs/       # Outputs when skill is used
│   │   ├── without_skill/outputs/    # Baseline outputs (no skill)
│   │   ├── eval_metadata.json        # Assertions for this eval
│   │   └── grading.json              # Pass/fail results
│   ├── iteration-2/                  # After first iteration
│   ├── benchmark.json                # Aggregated results
│   ├── feedback.json                 # User feedback from viewer
│   └── timing.json                   # Performance data
```

## Tips for Success

1. **Start narrow, expand carefully** — begin with a focused definition of what the skill does, then expand based on test feedback
2. **Real examples matter** — use actual spec documents or requirements from your domain
3. **Don't over-instruct** — explain the reasoning behind each step rather than writing rigid rules
4. **Watch transcripts** — if the model is doing unproductive work, look for unnecessary instructions to remove
5. **Generalize from feedback** — if a test case fails, think about what pattern it represents, not just the specific example
6. **Run full iterations** — spawn both with/without-skill runs in parallel to get meaningful comparisons

## Reference

Full skill development methodology: `.claude/skills/skill-creator/SKILL.md`

JSON schema documentation: `.claude/skills/skill-creator/references/schemas.md`

Grading agents and benchmarking: see `.claude/skills/skill-creator/agents/`
