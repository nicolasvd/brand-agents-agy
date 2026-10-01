# Rule: Output Formatting & Brand Hub & Spoke Architecture

> [!IMPORTANT]
> **Linguistic Hierarchy & Chat Mirroring:**
> - **Internal Engine (100% Technical English):** All agent definitions, prompt templates, declarative rules, HTML templates, scratchpads, and execution logs operate strictly in technical English.
> - **Conversational Chat (Strict Language Mirroring):** Conversational chat responses systematically mirror the user's prompt language (French for French, English for English).
> - **Deliverables (`reports/`):** Universal English UI shell and schema. Analytical deliverable copy adapts to the user's language.

---

## 1. Hub & Spoke Architecture

For every audited brand, deliverables are organized into a decoupled Hub & Spoke structure under `reports/{slug}/`:

```text
reports/
├── index.html                               # Global Brands Portal & Cockpit
└── {slug}/                                  # Brand workspace
    ├── OVERVIEW.html                        # Central Hub: Executive Reverse Brand Book
    ├── STRATEGIC-AUDIT.html                 # Spoke: Multi-Audit Scorecard & 4-Tier Action Plan
    ├── channels/                            # Channel Spokes (Dedicated platform reports)
    │   ├── linkedin.html
    │   ├── instagram.html
    │   ├── tiktok.html
    │   ├── facebook.html
    │   ├── youtube.html
    │   └── x.html
    ├── assets/                              # Permanent screenshots and stylesheets
    │   ├── css/
    │   │   └── design-tokens.css
    │   ├── screenshot-hub.png
    │   └── ...
    └── markdown/                            # AI Source of Truth (Permanent Markdown)
        ├── REVERSE-BRAND-BOOK.md
        ├── STRATEGIC-AUDIT.md
        └── channels/
            ├── linkedin.md
            ├── instagram.md
            └── ...
```

---

## 2. Deliverable Roles & Scope

| Component | Path | Audience | Source File |
|---|---|---|---|
| **Global Portal** | `reports/index.html` | Strategist | Bootstrap from `.agents/context/templates/index-template.html` |
| **Executive Hub** | `reports/{slug}/OVERVIEW.html` | Leadership & CMO | `reports/{slug}/markdown/REVERSE-BRAND-BOOK.md` |
| **Strategic Critique** | `reports/{slug}/STRATEGIC-AUDIT.html` | Brand Strategists | `reports/{slug}/markdown/STRATEGIC-AUDIT.md` |
| **Channel Spokes** | `reports/{slug}/channels/{platform}.html` | Community Managers | `reports/{slug}/markdown/channels/{platform}.md` |
| **Canonical Archives** | `reports/{slug}/markdown/**/*.md` | Subagents (AI Memory) | Produced by Wave 1 & Wave 2 agents |

---

## 3. Strict Relative Path Hygiene

Never generate HTML attributes or markdown links with absolute filesystem URIs (`file:///Users/...`, `/var/folders/...`, etc.). Always use strict relative paths:
- From Hub: `assets/...`, `channels/{platform}.html`, `markdown/...`
- From Channels: `../assets/...`, `../OVERVIEW.html`, `../STRATEGIC-AUDIT.html`, `../markdown/channels/{platform}.md`
- From Global Portal: `{slug}/OVERVIEW.html`, `{slug}/STRATEGIC-AUDIT.html`

---

## 4. Machine Metadata Standard (YAML Frontmatter)

Every canonical Markdown deliverable begins with standard frontmatter:

```yaml
---
slug: "{slug}"
brand_name: "{brand_name}"
primary_url: "{primary_url}"
first_audit_date: "YYYY-MM-DD"
latest_audit_date: "YYYY-MM-DD"
total_audits: 1
score: 6.6
dark_social_status: "RESOLVED|FAILED"
audits_history:
  - audit_id: 1
    date: "YYYY-MM-DD"
    score: 6.6
    mode: "INITIAL_BASELINE|INCREMENTAL_UPDATE"
---
```

---

## 5. Universal Completion Block

When concluding an audit run, the orchestrator outputs the standardized completion block in chat:

### 📦 Deliverables Generated
- **Executive Hub:** `reports/{slug}/OVERVIEW.html`
- **Strategic Audit:** `reports/{slug}/STRATEGIC-AUDIT.html`
- **Channel Deep-Dives:** `reports/{slug}/channels/*.html`
- **AI Data Archives:** `reports/{slug}/markdown/`
- **Portal Updated:** `reports/index.html`
