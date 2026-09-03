# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-file web game — **Tabuada Turbo** — that helps ~10-year-old children memorize
multiplication tables (factors 2–9). Portuguese (pt-BR) UI, pastel kid-friendly visuals.

## Commands

There is no build, package manager, test runner, or linter. The entire app is `index.html`.

- **Run:** open `index.html` in a browser (`start index.html` on Windows).
- **Deploy / share:** published as a Claude Artifact at
  `https://claude.ai/code/artifact/8bb7ed18-dfde-41fd-b070-f5c6a911b5d5`.

## Editing workflow (important)

1. Make all changes in `index.html` — it is the source of truth (HTML + inline CSS + inline JS,
   no dependencies, no network calls except the Google Fonts `<link>`).
2. To update the Artifact, regenerate the wrapper-less copy and republish to the **same URL**.
   The Artifact publish step wraps the file in `<!doctype>/<html>/<head>/<body>`, so the
   published copy must have those stripped (keep `<title>`, the font `<link>`, `<style>`, then
   the body markup and `<script>`).
3. **Encoding:** always read/write as **UTF-8 without BOM**. In PowerShell 5.1, `Get-Content`
   and `Set-Content` default to ANSI and `Set-Content -Encoding utf8` adds a BOM — both corrupt
   the accented text and emoji. Use `[System.IO.File]::ReadAllText(path, [Text.Encoding]::UTF8)`
   and `[System.IO.File]::WriteAllText(path, s, (New-Object Text.UTF8Encoding $false))`.

## Architecture

Everything lives in the IIFE at the bottom of `index.html`.

- **Three screens, toggled via the `hidden` attribute:** `#overlay` (Start modal, blurred
  backdrop), `#game`, `#end`. `startSession()` resets state and shows the overlay; `begin()`
  (Start button / Enter / Space) hides it and calls `startTimer()`.
- **Session = `QUESTIONS_PER_SESSION` (10) questions.** `makeQuestion()` picks `a` (2–9) and
  `b` (1–10), builds 4 plausible distractors from neighbouring products, and Fisher–Yates
  shuffles the 5 options.
- **Timer restarts at `START_TIME` (60) every question.** Seconds remaining at the moment of a
  correct answer are added to `score`. Wrong answer or timeout = 0 points; `answered` guards
  against double-scoring while feedback shows, then `next()` advances.
- **`record`** (best session score) is an in-memory variable only — never persisted. A page
  reload resets everything to zero, which is intentional.
- **Input:** number keys 1–5 map to option buttons; buttons are also click/tap targets.

## Constraints to preserve

- No persistence (no `localStorage`), no build tooling, no external JS/CSS beyond Google Fonts.
- Keep the on-screen vertical order the game was specified with: timer → score → question →
  5 options → session record.
- Font stack must keep the offline fallback (`"Baloo 2", "Comic Sans MS", ...`); respect
  `prefers-reduced-motion` and the light/dark theme token blocks in `:root`.
