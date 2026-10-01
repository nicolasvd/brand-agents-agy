---
name: opengraph-audit
description: >-
  Dark Social and Open Graph auditing skill. Evaluates HTML metadata, Twitter cards, asset reachability, and generates visual chat preview simulations for private messaging apps.
---

# Skill: opengraph-audit

**Role:** Dark Social & Metadata Verification Engine.  
**Execution Context:** Wave 1 Hub Crawler (`brand-sub-hub-crawler`) and Wave 2 Strategic Analyst (`brand-sub-analyst`).  
**Core Invariant:** Inspect literal HTML DOM tags (`<meta property="og:...">`, `<meta name="twitter:...">`). Flag relative or unresolvable image URLs as broken.

---

## 1. Objectives

- Audit the brand's Dark Social footprint — how URLs appear when shared privately via WhatsApp, Slack, Teams, iMessage, LinkedIn DMs, or SMS.
- Detect missing, truncated, or broken Open Graph tags that hurt click-through rates and perceived authority.
- Provide clear visual simulation data for the HTML Executive Hub (`OVERVIEW.html`).

---

## 2. Technical Inspection Checklist

Extract and validate the following standard metadata elements from the brand's root domain:

| Tag | Expected Value | Diagnostic Check |
|---|---|---|
| `og:title` | Brand or Page Title | Must not be empty, generic, or truncated (< 65 chars recommended) |
| `og:description` | Brand Value Proposition | Must clearly communicate the core offering (< 155 chars) |
| `og:image` | Absolute Image URL | Must be absolute (`https://...`), reachable (200 OK), and $\ge 1200\times 630\text{px}$ |
| `og:url` | Canonical Page URL | Must match canonical destination (https, proper domain) |
| `twitter:card` | Card Format | Typically `summary_large_image` or `summary` |

---

## 3. Dark Social Status Determination

Evaluate overall tag health and assign a deterministic status:

- **`RESOLVED`**:
  - `og:title`, `og:description`, and `og:image` are all present.
  - `og:image` is an absolute URL pointing to a valid, high-resolution visual asset.
  - Private messaging previews render a rich branded card.
- **`FAILED`**:
  - `og:image` is missing, relative (e.g., `/img/preview.png` without origin), or returns HTTP 404.
  - `og:title` or `og:description` is completely absent or returns default CMS placeholder text.
  - Private messaging shares render as plain raw text or broken image icons.

---

## 4. Visual Chat Simulation Data Format

Format findings in markdown for reporting and styling:

```markdown
## Dark Social Footprint (Open Graph)

- **Status:** RESOLVED | FAILED
- **og:title:** "AG Insurance — Supporter de votre vie"
- **og:description:** "Découvrez nos solutions d'assurance vie, santé et auto..."
- **og:image:** `https://www.ag.be/assets/og-share-1200x630.png` [Valid, 1200x630]
- **og:url:** `https://www.ag.be`
- **twitter:card:** `summary_large_image`

### Visual Simulation
| Metric | Stated Target | Live Rendering |
|---|---|---|
| Slack / Teams Preview | Rich Card with Visual Banner | ✅ Formatted (or ❌ Raw Link Fallback) |
| WhatsApp / SMS | Image Thumbnail + Description | ✅ Rich Snippet (or ❌ Missing Card) |
```

---

## 5. Downstream Integration

- Directly determines Pillar 2 (Omnichannel Consistency & Dark Social) scoring in `scoring.md`.
- Injects side-by-side Broken vs Recommended card mockups into `OVERVIEW.html`.
