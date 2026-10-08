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
  - `og:image` is an absolute, reachable URL pointing to a high-resolution visual asset.
  - `og:url` is a valid canonical absolute URL matching destination domain.
  - Private messaging previews render an optimal rich branded card.
- **`PARTIAL`**:
  - `og:image` is present and reachable, and `og:title` is present.
  - However, `og:url` is missing/relative, or `og:description` is missing/generic.
  - Real-world messaging apps (WhatsApp, Slack, Teams, iMessage) **still render the actual image and title**, but domain provenance or descriptive context is degraded.
  - The live visual simulation MUST display the real image rather than an empty placeholder, while the diagnostic table highlights the missing canonical tags.
- **`FAILED`**:
  - `og:image` is completely missing, unresolvable relative path, or returns HTTP 404/5xx.
  - `og:title` or `og:description` is completely absent or returns empty placeholder text.
  - Private messaging shares render as plain raw text links or broken image icons.

---

## 4. Visual Chat Simulation Data Format

Format findings in markdown for reporting and styling:

```markdown
## Dark Social Footprint (Open Graph)

- **Status:** RESOLVED | PARTIAL | FAILED
- **og:title:** "AG Insurance — Supporter de votre vie"
- **og:description:** "Découvrez nos solutions d'assurance vie, santé et auto..."
- **og:image:** `https://www.ag.be/assets/og-share-1200x630.png` [Valid, 1200x630]
- **og:url:** `https://www.ag.be`
- **twitter:card:** `summary_large_image`

### Visual Simulation Contract
- **live_image_url:** `https://www.ag.be/assets/og-share-1200x630.png` (or `null` if absent/broken)
- **live_title:** "AG Insurance — Supporter de votre vie" (falls back to `<title>` if og:title missing)
- **live_description:** "Découvrez nos solutions d'assurance..." (falls back to meta description if missing)
- **live_domain:** "ag.be" (extracted from page URL)

| Metric | Stated Target | Live Rendering |
|---|---|---|
| Slack / Teams Preview | Rich Card with Visual Banner | ✅ Formatted (or ⚠️ Degraded Image Only, or ❌ Raw Link Fallback) |
| WhatsApp / SMS | Image Thumbnail + Description | ✅ Rich Snippet (or ⚠️ Partial Snippet, or ❌ Missing Card) |
```

---

## 5. Downstream Integration

- Directly determines Pillar 2 (Omnichannel Consistency & Dark Social) scoring in `scoring.md` (RESOLVED: 10/10, PARTIAL: 6.5–7.5/10, FAILED: 3.0–4.0/10).
- Injects side-by-side Live Preview vs Recommended Card mockups into `OVERVIEW.html`, ensuring real images are always rendered whenever `og:image` is present.

