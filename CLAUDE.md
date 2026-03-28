# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal CV/resume website for Tiago de Campos — Data Science Specialist at Itaú-Unibanco. Hosted as a GitHub Pages site at `tiagocampo.github.io`.

## Architecture

Single-page static site. The entire application is **one file**: `index.html` containing all HTML, CSS, and JavaScript inline. No build step, no frameworks, no bundler.

- **CSS**: Custom properties in `:root` define the Itaú-branded color palette (`--itau-orange`, `--itau-blue`, etc.). Two font families loaded via Google Fonts: DM Sans (sans) and Playfair Display (serif).
- **Layout**: CSS Grid two-column layout (35% sidebar / 65% main content). Sidebar is `position: sticky` with scroll-synced highlight groups.
- **JS features**: IntersectionObserver-based fade-in animations, staggered sidebar entrance, scroll-synced sidebar highlights that change based on which main section is in viewport, and PDF generation via `html2pdf.js` (loaded from CDN).
- **Responsive**: Breakpoints at 960px (single column) and 600px (compact mobile).
- **Print**: Dedicated `@media print` styles for clean PDF output.

## Development

Open `index.html` directly in a browser — no server or build tooling required. For live reload during development, any static file server works (e.g., `python -m http.server`).

## Linting

Codacy is configured (`.codacy/codacy.yaml`) with eslint, semgrep, and lizard. No local linting setup required — Codacy runs on push.

## Content Language

All CV content is in **Brazilian Portuguese**. Maintain this when updating text sections.
