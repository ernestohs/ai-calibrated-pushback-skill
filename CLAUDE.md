# Using Calibrated Pushback with Claude

Claude models (Opus, Sonnet, Haiku) are trained to be helpful, harmless, and honest. The "helpful" objective can drift into agreeableness — validating weak plans and executing risky requests without flagging them. This skill re-tunes that behavior toward calibrated, evidence-based pushback.

## Implementation Methods

### 1. Claude Code (CLI)
If you are using this repository within a project managed by Claude Code, integrate this framework via a `CLAUDE.md` file.

**Action:**
Append the contents of `system_prompt.md` to a `CLAUDE.md` file at your project root (or to `~/.claude/CLAUDE.md` for global use). Claude Code automatically loads these files as standing instructions for every session, and treats them as overriding default behavior.

### 2. Claude API / Agent SDK
When calling the Messages API or building with the Agent SDK:
1. Pass the contents of `system_prompt.md` as the top-level `system` parameter.
2. The system prompt persists across every turn of the conversation, keeping the "pragmatic coworker" persona stable.
3. For agentic loops, the same system prompt keeps tool-use decisions honest — Claude will flag a destructive action (e.g. an unbacked database drop) before invoking the tool rather than after.

### 3. Claude.ai (Web / Desktop)
1. Open **Settings → Profile** and locate the **personal preferences** / custom instructions field.
2. Paste the contents of `system_prompt.md` there, or add it as the project's custom instructions when using a Claude Project.
3. This applies the persona across new conversations without re-pasting each time.

## Why it works for Claude
Claude responds well to explicit, structured constraints and to stated reasoning about *why* a rule exists. The **Push back when** / **Do NOT push back when** split maps cleanly onto Claude's strength at weighing reversibility and blast radius, so it spends scrutiny where it matters and stays out of the way on low-risk, well-specified tasks. The **EXCEPTION RULE** for significant harm, data loss, or irreversible damage aligns with Claude's safety training, reinforcing rather than fighting it.
