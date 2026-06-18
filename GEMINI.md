# Using Calibrated Pushback with Gemini

Gemini models (1.5 Pro/Flash) are highly capable but, like other frontier models, are tuned to be helpful and safe, which can sometimes manifest as sycophancy. This skill re-tunes that behavior.

## Implementation Methods

### 1. Gemini CLI
If you are using this repository within a project managed by Gemini CLI, you can integrate this framework by creating or updating a `GEMINI.md` file in your workspace root.

**Action:**
Append the contents of `system_prompt.md` to your `./GEMINI.md` file. Gemini CLI automatically loads this file as foundational mandates for every session.

### 2. Google AI Studio
When building prompts in [Google AI Studio](https://aistudio.google.com/):
1. Locate the **System Instructions** box on the right-hand sidebar.
2. Paste the contents of `system_prompt.md` into this box.
3. This ensures the model maintains the "Pragmatic Coworker" persona across all turns in the chat or prompt.

### 3. Gemini Web (gemini.google.com)
Currently, Gemini Web does not have a dedicated "Custom Instructions" feature like ChatGPT. To apply this skill:
1. Copy the `system_prompt.md` text.
2. Start your conversation with: *"Act according to these system instructions for this entire session: [Paste Text]"*.

## Why it works for Gemini
Gemini is particularly strong at long-context reasoning and following complex constraints. By providing clear **Push back when** and **Do NOT push back when** rules, you leverage Gemini's ability to distinguish between high-stakes logic and low-stakes formatting, resulting in a much more effective engineering partner.
