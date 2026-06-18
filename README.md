# AI Calibrated Pushback Skill

A system prompt framework designed to turn AI assistants from agreeable "yes-men" into highly effective, pragmatic coworkers. 

Based on the concepts outlined in [Stop Training Your AI to Agree With You](https://dev.to/ernestohs/stop-training-your-ai-to-agree-with-you-5gh7).

## The Problem

Most modern AI models (such as ChatGPT, Gemini, Claude, and Codex) are optimized via RLHF (Reinforcement Learning from Human Feedback) to be pleasant, agreeable, and compliant. This creates the "Yes-Man" problem:
- You suggest a bad idea; it tells you it's a great direction.
- You ask for a script that deletes a database without a backup; it writes the script eagerly.
- It optimizes for user approval and momentum rather than technical rigor and outcomes.

## The Solution

This repository contains a modular system prompt that reconfigures the AI's core behavior. It introduces the concept of **Calibrated Pushback**: challenging the user when it improves the outcome, and getting out of the way when it doesn't.

## Contents

- [`system_prompt.md`](system_prompt.md): The core system instruction block to paste into Custom Instructions (ChatGPT), System Instructions (Gemini), or AI coding environments (like Cursor/Copilot).
- [`GEMINI.md`](GEMINI.md): Instructions for using this skill specifically with Gemini CLI and the Google AI ecosystem.
- [`CLAUDE.md`](CLAUDE.md): Instructions for using this skill specifically with Claude Code, the Claude API/Agent SDK, and Claude.ai.
- [`CODEX.md`](CODEX.md): Instructions for using this skill with Codex CLI, the IDE extension, the Codex app, cloud tasks, and Codex skills.
- [`rules/`](rules/): Modular rules breaking down the philosophy (Uncertainty, Modes, Tone).

## Usage

1. Copy the contents of `system_prompt.md`.
2. Paste it into your AI tool's "System Prompt", "Custom Instructions", "System Instructions", or `.cursorrules` / `.windsurfrules` file.
3. Observe how the AI begins catching weak assumptions before executing code.
