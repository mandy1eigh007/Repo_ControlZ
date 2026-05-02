# Repo ControlZ: AI Build Foreman Training Guide

Repo ControlZ is a simple **living manual** for controlling AI coding agents.

This repo is **not an app**. It’s a documentation-and-templates repository for storing instructions, prompts, and workflow notes for managing AI coding tools (Codex, VS Code Chat / Copilot, Replit agents, Codespaces, and related workflows).

The main idea: **the repo is the durable memory, not the chat**.

## Quick start
1. Skim the guide: see `GUIDE.md`.
2. Use the reusable prompts: see `PROMPTS.md`.
3. Copy templates from `templates/` into your working repo (or keep them here and reference them).
4. Start tracking changes in `CHANGELOG.md`.

## Core workflow
1. User creates or opens a repo.
2. ChatGPT acts as foreman.
3. ChatGPT writes the agent prompt.
4. Codex / VS Code Chat / Copilot / Replit agent does the work.
5. User brings the output back for review.
6. ChatGPT inspects and gives the next step.

## Repo structure
- `GUIDE.md` — practical operating guide
- `PROMPTS.md` — reusable prompt library
- `templates/` — copy/paste templates for agent rules and project control
- `CHANGELOG.md` — record updates to this manual
