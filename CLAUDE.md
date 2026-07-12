# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development

This is a static HTML/CSS/JS site with no build tooling, package manager, or test suite.

**To preview locally:**
```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Architecture

Six standalone HTML files, each self-contained with all CSS in a `<style>` block and all JS inline at the bottom. There is no shared stylesheet or JS module.

| File | Purpose |
|---|---|
| `index.html` | Main homepage (hero, services, about, beliefs grid, watch/sermons, events, prayer, newsletter, contact) |
| `belief-god.html` | "What We Believe" — God |
| `belief-jesus.html` | "What We Believe" — Jesus |
| `belief-scripture.html` | "What We Believe" — Scripture |
| `belief-response.html` | "What We Believe" — Response |

## Design System

All pages share the same CSS custom properties (duplicated per file):

```css
--purple: #5b2d8e
--purple-dark: #3d1a6e
--purple-light: #7a3fb5
--green: #3a9c4e
--gray-dark: #2e2e2e
--gray-mid: #6b6b6b
--gray-light: #f4f4f6
--white: #ffffff
--gold: #c9a84c
```

**Fonts**: Cinzel (headings/nav brand, loaded via Google Fonts), Lato (body text).

**Nav**: Fixed, 72px tall, `background: #1a0533`. The homepage also has a 2nd fixed strip (`.prayer-cta-strip`) below the nav at `top: 72px`, so page content on `index.html` needs `padding-top` that accounts for both bars.

## Key Patterns

- The church logo is embedded as a base64 JPEG directly in each HTML file — to update it, replace the `src="data:image/jpeg;base64,..."` value in every file.
- The homepage newsletter signup uses Mailchimp's classic embed (CSS loaded from `cdn-images.mailchimp.com`).
- Belief pages include a `.beliefs-strip` nav bar linking between the four belief pages; `index.html` links to them via the `.beliefs-grid` section.
- External links: YouTube channel for sermons/live stream, Google Maps embed in the contact section.
