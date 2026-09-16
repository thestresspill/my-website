# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static one-page portfolio/resume site for Vineet Jose / The Stress Pill, hosted on GitHub Pages at `thestresspill/my-website` (served from the `main` branch — this repo's local `main` tracks `origin/main` there). Pure HTML/CSS, no build step, no package manager, no JS framework, no dependencies (aside from a Google Fonts `<link>`). There is no local README to defer to.

## Commands

There is no build, lint, or test tooling — this is static markup served as-is by GitHub Pages. To preview a change, open `index.html` directly in a browser (`start "" index.html` on Windows works fine via `file://`, no local server needed).

Deploying is just committing and pushing to `origin/main`; GitHub Pages rebuilds automatically.

## Structure and conventions

- **`index.html`** — the entire site: a single self-contained HTML file with one inline `<style>` block, no shared stylesheet, no JS. Sections in order: sticky header/nav (Experience / Off the Clock / Contact anchors + Resume download button), hero (name, title line, stat callouts, CTA row, circular profile photo), `#experience` (achievement stat cards + role history cards), skills & education, `#offline` "Off the Clock" (tinted band covering music releases/support links, side-project apps, and a blog link), and `<footer id="contact">` (email/LinkedIn/resume CTA + language/hobby tags).
- **`assets/profile.jpg`** — the hero portrait, referenced via a relative `src="assets/profile.jpg"`.
- **`assets/Vineet-Jose-Resume.pdf`** — the downloadable resume, linked from the nav, hero, and footer via relative `href="assets/Vineet-Jose-Resume.pdf"`.
- **`sample_json.json`** — unrelated generic JSON boilerplate (a "glossary" example), untracked and unused; leave it alone unless asked to remove it.

The design system ("Organic") is defined as CSS custom properties at the top of `index.html`'s `<style>` block: `--color-bg` (cream `#f5ead8`), `--color-accent` (terracotta `#c67139`), `--color-accent-2` (sage `#7a8a5e`), plus `--space-*`, `--radius-lg`, and `--shadow-*` scales. Only the specific tonal-ramp steps (`-100`/`-600`/`-700`/`-800`) actually used by `.tag-*`/`.btn-primary` are defined — this isn't the full 9-step ramp, so don't assume e.g. `--color-accent-400` exists without checking. Headings use `--font-heading` (Caprasimo); body text uses `--font-body` (Figtree), both loaded from the Google Fonts CDN via `<link>` tags in `<head>` rather than bundled.

Two conventions worth knowing before editing markup:
- Heading *level* (`h1`–`h3`) is kept semantically correct (no skipped levels) independent of visual size — the "Off the Clock" subheadings are `<h3 class="h4-size">` to get smaller text at the correct heading depth, rather than literally using `<h4>`.
- Repeated card-as-link styling uses the `.card-link` class (`text-decoration:none; color:inherit;`) instead of duplicating that inline `style=` on every card anchor.

External links use `target="_blank" rel="noopener noreferrer"`; internal anchors (`#experience`, `#offline`, `#contact`) and the resume `download` links do not. Because `.nav a` and `.btn` both style `<a>` tags and the header nav contains a `.btn.btn-primary` Resume link, `.nav a` is scoped with `:not(.btn)` — removing that exclusion would silently break the button's text color via CSS specificity, so keep it if `.nav`'s link rules are ever touched.
