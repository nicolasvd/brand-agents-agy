# Rule: Brand Fact-Checking & Epistemic Rigor

> [!IMPORTANT]
> **Core Mandate:** All brand diagnoses, audience metrics, visual audits, and deliverable scores must be anchored in verified empirical data. Never invent, extrapolate, or guess follower numbers, video views, advertising budgets, or executive statements.

---

## 1. Source Hierarchy (Descending Reliability)

1. **Direct DOM Inspection via Native Browser:** Live, hydrated DOM elements from verified brand channels (follower counts, canonical post links, engagement metrics, Open Graph tags).
2. **Official Brand Properties:** Homepage HTML, Dark Social metadata (`og:*`, `twitter:*`), and published corporate statements.
3. **Official Advertising Transparency Repositories:** Meta Ad Library, Google Ads Transparency Center, LinkedIn Ad Library (when verified via explicit browser lookup).
4. **Reputable Press & Industry Reports:** TechCrunch, Forbes, L'Écho, Trends-Tendances, etc.

---

## 2. Epistemic Rigor (Paid vs Organic Media)

Asserting advertising spend or paid amplification carries significant strategic consequences:

- **Confirmed Paid Media:** Asserted ONLY when an explicit, native advertising badge is detected in the DOM (`ad_badge_present: true`, such as "Promoted", "Sponsorisé", "Commandité", "Publicité").
- **Absence of Badge:** When anomalous engagement or outsized view-to-follower ratios are observed without an official DOM badge (e.g., 900k views on an account with 10k followers):
  - Strictly prohibit categorical claims of "massive ad spend" or "paid campaigns".
  - Formulate diagnoses strictly in the conditional mood: *suggests probable paid media amplification or an exogenous algorithmic recommendation spike*.
  - Use the standardized technical term: **estimated amplified reach** (*portée amplifiée estimée*).
  - Mandatorily append the methodological caveat:
    > *Methodological Note: Finding deduced from public read-only indicators. Without direct ad-tech platform access, this amplification remains a highly probable but uncertifiable estimate.*

---

## 3. Real Comment Sampling & Fast-Exit Protocol

To evaluate community resonance and real tone of voice without hallucination:

1. **Top 3 Posts Sampling:** For the top 3 posts on each audited platform, extract 3 to 5 first-level, authentic comment verbatims (author handle/role, verbatim quote, comment likes).
2. **Fast-Exit Sentinel:** If a post or video has 0 comments or comments are disabled:
   - Immediately record `comment_status: NONE_OR_DISABLED`.
   - Do NOT spend latency searching or retrying.
   - Do NOT fabricate placeholder comments.

---

## 4. Conversational Engagement Ratio & Tone of Voice Capping

$$\text{Conversational Ratio} = \frac{\text{Total Comments}}{\text{Total Reactions}}$$

- **Passivity Threshold ($< 0.5\%$):** If the conversational ratio falls below $0.5\%$, flag a presumption of severe comment moderation or passive audience engagement.
- **Support Overflow Detection:** Identify if the public comment section is acting as an unhandled customer support backlog.
- **Pillar 1 Capping Rule:** If persistent customer service complaints or unresolved customer friction appear in the qualitative comment sample without brand replies, Pillar 1 (Tone of Voice) is strictly **capped at a maximum of 6.5 / 10**.

---

## 5. Standardized 10-Point Evaluation Scale

- All performance ratings, pillar scorecards, frontmatter metadata, and historical progression tables must strictly and exclusively use the unified **10-point scale** (e.g. 6.6 / 10).
- Absolute prohibition of US-style letter grades (`Grade A`, `B-`, `C+`, etc.) or `.grade-*` styling classes.
- Qualitative appraisals must use explicit qualifiers:
  - `8.0 – 10.0 / 10`: *Excellence & Strong Cohesion* (`.score-high`)
  - `6.0 – 7.9 / 10`: *Moderate Cohesion in Consolidation* (`.score-medium`)
  - `< 6.0 / 10`: *Critical Misalignment* (`.score-low`)

---

## 6. Local Path Hygiene & Relative Sanctuary

- Never output or propagate absolute local filesystem paths (e.g., `file:///Users/...`, `/Users/...`, `/var/folders/...`, `/tmp/...`).
- All media assets, screenshots, and cross-report links must use clean project-relative paths:
  - `reports/{slug}/assets/screenshot-{channel}-{date_compact}.png`
  - `reports/{slug}/markdown/channels/{channel}.md`
  - `reports/{slug}/OVERVIEW.html`
