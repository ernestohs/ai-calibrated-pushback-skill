# Using Calibrated Pushback with OpenAI Codex

Codex can load durable instructions before it starts working in a repository. This makes `AGENTS.md` the best place for always-on calibrated pushback, while a Codex skill is a better fit when you want the behavior available on demand.

## Implementation Methods

### 1. Codex CLI, IDE Extension, and App

Add the contents of `system_prompt.md` to an `AGENTS.md` file:

- Use `./AGENTS.md` at the repository root for project-specific behavior.
- Use `~/.codex/AGENTS.md` for personal defaults across repositories.
- Use a nested `AGENTS.md` or `AGENTS.override.md` when a subtree needs more specific instructions.

Codex loads the instruction chain at the start of a run or interactive session. Start a new session after changing the file so the updated guidance is applied.

### 2. Codex Web and Cloud Tasks

Commit an `AGENTS.md` file at the repository root containing the contents of `system_prompt.md`. This keeps the same working agreement available when Codex works on the repository remotely, including delegated tasks and pull-request work.

Keep repository-specific build, test, and review instructions in the same file, but separate them under clear headings so behavioral guidance does not obscure operational requirements.

### 3. Reusable Codex Skill

Use a skill when calibrated pushback should be explicitly selectable rather than always active.

Create either:

- `.agents/skills/calibrated-pushback/SKILL.md` for repository-scoped use.
- `$HOME/.agents/skills/calibrated-pushback/SKILL.md` for use across repositories.

Give the skill YAML frontmatter with a `name` and a trigger-focused `description`, then place the instructions from `system_prompt.md` in the body. Invoke it explicitly with `$calibrated-pushback`, or let Codex select it when the task matches its description.

## Why It Works for Codex

Codex combines instructions with direct access to code, commands, and external tools. The framework's reversibility and blast-radius rules help it distinguish routine implementation from actions that deserve scrutiny, such as destructive commands, insecure shortcuts, or changes with unclear requirements. The mode definitions also let you ask for criticism, mentoring, or fast execution without losing the exception rule for significant harm or irreversible damage.
