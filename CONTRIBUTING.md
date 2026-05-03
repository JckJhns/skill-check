# Contributing to SkillCheck 🎲

Thanks for your interest in improving SkillCheck! Whether you're a seasoned skill
author or just rolled your first character, here's how to get involved.

## Ways to contribute

### Report issues
If SkillCheck missed something it should have caught, produced a false positive, or
behaved unexpectedly, open an issue with:
- The skill you tested (or a minimal reproduction)
- The depth level you ran
- What you expected vs what happened

### Add or improve test types
SkillCheck's test coverage lives in the `skill-check/references/` directory. Each depth level
(quick-check.md, standard-check.md, deep-check.md) defines which tests run and how.

To add a new test type:
1. Decide which depth level it belongs at (Quick for static, Standard for execution-based,
   Deep for edge cases)
2. Add the test definition to the appropriate reference file
3. If it's a new category, add it to `skill-check/SKILL.md`'s Phase 2 test list
4. Add a test fixture to `skill-check/evals/files/` if the new test needs one
5. Add an eval to `skill-check/evals/evals.json` that exercises the new test
6. Update the expected test counts in the relevant reference files

### Improve best practice checks
The 22 best practice checks in `skill-check/references/best-practices.md` are aligned with the
[Agent Skills open standard](https://agentskills.io). If the standard evolves or you
identify a common quality issue that should be checked, propose a new BP check.

Each check needs: a clear description of what to look for, how to check it (ideally
with a programmatic approach), a severity level, and a "why" explaining the reasoning.

### Improve mock file generation
`skill-check/references/mock-files.md` covers mock generation for common file types. If you encounter
a file type that's missing or a generation approach that could be better, improve it.

### Fix or improve existing content
Typos, unclear instructions, stale examples, missing "why" explanations — all welcome.

## Guidelines

### Keep the SKILL.md slim
The main SKILL.md should stay under 500 lines. It's the orchestrator —
it tells the agent the flow and when to read each reference file. Detail belongs in
`skill-check/references/`.

### Follow the skill's own best practices
SkillCheck checks skills against BP-1 through BP-22. It should pass its own checks.
If you add content, make sure it follows the conventions SkillCheck recommends to others.

### Test your changes
After making changes, run SkillCheck on itself using the evals in `skill-check/evals/evals.json`.
This ensures changes don't break existing behaviour.

### Keep cross-platform compatibility in mind
SkillCheck follows the Agent Skills open standard. Avoid adding checks or behaviour
that only works on one platform (e.g., Claude-specific paths without fallbacks).

## Structure quick reference

| File | Purpose |
|------|---------|
| `skill-check/SKILL.md` | Main instructions — flow and orchestration |
| `skill-check/references/quick-check.md` | Quick Check test definitions |
| `skill-check/references/standard-check.md` | Standard Check test definitions |
| `skill-check/references/deep-check.md` | Deep Check test definitions |
| `skill-check/references/best-practices.md` | 22 best practice checks |
| `skill-check/references/mock-files.md` | Mock file generation recipes |
| `skill-check/references/report-format.md` | Report template and collapsing rules |
| `skill-check/references/eval-schema.md` | evals.json format reference |
| `skill-check/references/example-run.md` | Worked example |
| `skill-check/references/finding-the-skill.md` | Skill discovery when no path given |
| `skill-check/references/incomplete-skills.md` | Handling half-written skills |
| `skill-check/evals/evals.json` | SkillCheck's own test cases |
| `skill-check/evals/files/` | Test fixture skills |
