# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

BillScan is a landing page for an AI-powered medical bill auditing tool. The site is hosted on GitHub Pages at **billscan.info**.

## Deployment

- **Hosting:** GitHub Pages (auto-deploys on push to master)
- **Domain:** billscan.info (configured via CNAME file, DNS through GoDaddy)
- **To deploy:** `git push` to master branch

## Architecture

This is a static site with no build process:
- `index.html` - Main landing page with hero animation (bill scanning → error detection → envelope folding → savings display)
- `confirmed.html` - Waitlist signup confirmation with animated envelope opening
- Standalone animation files (`animation-counter.html`) for marketing content

## Waitlist Backend

Uses Supabase for waitlist signups:
- **Project:** `https://bsooywuaxoyfixwxcsxh.supabase.co`
- **Table:** `waitlist` (email, created_at)
- Form in `index.html` submits via REST API, redirects to `confirmed.html` on success

## Brand Guidelines

| Element | Value |
|---------|-------|
| Primary Blue | #2563eb |
| Hover Blue | #1d4ed8 |
| Text Dark | #111827 |
| Text Gray | #6b7280 |
| Error Red | #dc2626 |
| Success Green | #059669 |
| Font | Inter (400, 500, 600, 700, 800) |
| Logo | `BillScan_` (underscore in blue) |

## Hero Animation Structure

The envelope animation uses CSS 3D transforms with JavaScript-controlled class toggling:
- `.fold-bottom`, `.fold-sides`, `.fold-top` classes control flap positions
- Animation sequence controlled by `setTimeout` chains in `<script>` tag
- When reusing the envelope (e.g., in `confirmed.html`), copy the full envelope HTML structure and CSS from `index.html`
