# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static one-page portfolio/resume site for Vineet Jose / The Stress Pill, hosted on GitHub Pages at `thestresspill/my-website` (served from the `main` branch — this repo's local `main` tracks `origin/main` there). Pure HTML/CSS, no build step, no package manager, no JS framework, no dependencies (aside from a Google Fonts `<link>`). There is no local README to defer to.

## Commands

There is no build, lint, or test tooling — this is static markup served as-is by GitHub Pages. To preview a change, open `index.html` directly in a browser (`start "" index.html` on Windows works fine via `file://`, no local server needed).

Deploying is just committing and pushing to `origin/main`; GitHub Pages rebuilds automatically.

## Structure and conventions

- **`index.html`** — the entire site: a single self-contained HTML file with an inline `<style>` block, no shared stylesheet, no JS. Sections in order: sticky header/nav (Experience / Off the Clock / Contact anchors + Resume download button), hero (name, title line, stat callouts, CTA row, circular profile photo), `#experience` (achievement stat cards + role history cards), skills & education, `#offline` "Off the Clock" (tinted band covering music releases/support links, side-project apps, and a blog link — this folds in what used to be separate `apps.html`/`music.html` pages), and `<footer id="contact">` (email/LinkedIn/resume CTA + language/hobby tags).
- **`assets/profile.jpg`** — the hero portrait, referenced via a relative `src="assets/profile.jpg"`.
- **`assets/Vineet-Jose-Resume.pdf`** — the downloadable resume, linked from the nav, hero, and footer via relative `href="assets/Vineet-Jose-Resume.pdf"`.
- **`sample_json.json`** — unrelated leftover boilerplate, untracked and unused; leave it alone unless asked to remove it.

The design system ("Organic") is defined as CSS custom properties at the top of `index.html`'s `<style>` block: `--color-bg` (cream `#f5ead8`), `--color-accent` (terracotta `#c67139`), `--color-accent-2` (sage `#7a8a5e`), plus 9-step tonal ramps for neutral/accent/accent-2, a `--space-*` spacing scale, `--radius-*`, and `--shadow-*`. Headings use `--font-heading` (Caprasimo); body text uses `--font-body` (Figtree). Both fonts are loaded from the Google Fonts CDN via `<link>` tags in `<head>` (same external-CDN pattern previously used for Font Awesome) rather than bundled — there is no local font file to update if swapping them.

External links use `target="_blank" rel="noopener noreferrer"`; internal anchors (`#experience`, `#offline`, `#contact`) and the resume `download` links do not.

`apps.html`, `music.html`, and `Pro2.jpg` no longer exist — their content was merged into `index.html`'s "Off the Clock" section during the September 2026 portfolio redesign. If re-adding standalone project/music pages is ever needed again, note the "Off the Clock" section already covers that content, so avoid re-duplicating it.
