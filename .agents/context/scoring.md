# Deterministic Brand Audit Scoring Framework (10-Point Scale)

> [!IMPORTANT]
> **Unified 10-Point Standard:** All ratings, pillar evaluations, historical progression tables, and deliverable scores operate strictly on the deterministic 10-point scale (e.g. 6.6 / 10). US-style letter grades (Grade A, B-, etc.) and vanity follower-following ratios are strictly prohibited.

---

## 1. Core Evaluation Pillars (0 to 10 points each)

The brand audit measures omnichannel digital health across four core pillars:

### Pillar 1: Tone of Voice (ToV) & Community Reception (0–10 pts)
Evaluates alignment between stated positioning and real-world audience reception.

| Evaluation Criteria | Scoring Impact |
|---|---|
| Strong editorial voice, cohesive messaging across platforms | 8.5 – 10.0 |
| Minor tonal drift between corporate (B2B) and social/lifestyle channels | 7.0 – 8.4 |
| Severe dissonance between corporate claims and customer reality | 4.0 – 6.9 |
| Comments section acts as unhandled customer complaint overflow | **Capped at max 6.5 / 10** |
| Conversational Ratio ($\frac{\text{Comments}}{\text{Reactions}}$) $< 0.5\%$ | **Flag audience passivity / severe moderation** |

$$\text{Conversational Ratio} = \frac{\text{Total Comments}}{\text{Total Reactions}}$$

### Pillar 2: Omnichannel Consistency & Dark Social (0–10 pts)
Evaluates visual identity coherence and technical readiness for private channel sharing (WhatsApp, Slack, SMS, Teams).

| Evaluation Criteria | Scoring Impact |
|---|---|
| Complete Open Graph metadata (`og:title`, `og:description`, `og:image`, `og:url`), valid dimensions ($\ge 1200\times 630\text{px}$), Twitter Cards verified | 9.0 – 10.0 (`RESOLVED`) |
| Minor tag omissions or generic non-branded preview images | 6.0 – 8.9 |
| Missing Open Graph tags, broken image URLs, or unconfigured root domain metadata | 1.0 – 5.9 (`FAILED`) |
| Cross-platform handle discrepancies or unlinked active profiles | −1.5 penalty |

### Pillar 3: Publication Velocity & Engagement Trajectories (0–10 pts)
Evaluates sustained publishing rhythm, content half-life, and multi-format vitality.

| Evaluation Criteria | Scoring Impact |
|---|---|
| Active, predictable publishing cadence across all verified tier-1 platforms | 8.5 – 10.0 |
| Healthy format distribution (% Reels / Shorts, Carousels, Thought Leadership) | +1.0 bonus |
| Fading frequency (> 30 days without post on primary channel) | 4.0 – 6.0 |
| Broken cadence or abandoned channels (> 90 days silence) | 1.0 – 3.9 |
| Engagement trajectory ($\Delta$ reactions, $\Delta$ comments) positive over elapsed audit window | Trajectory: 🟢 Positive |

### Pillar 4: Conversion & Product Narrative (0–10 pts)
Evaluates commercial activation, link-in-bio infrastructure, and organic vs amplified discovery.

| Evaluation Criteria | Scoring Impact |
|---|---|
| Frictionless conversion paths, clear CTA, multi-link hub configured | 8.5 – 10.0 |
| Generic link-in-bio (pointing only to homepage without context) | 6.0 – 8.4 |
| Dead links, 404 targets, or missing calls to action | 1.0 – 5.9 |
| Confirmed native advertising badge in DOM (`ad_badge_present: true`) | Documented as verified paid media |
| Anomalous view velocity without DOM badge | Must use conditional formulation: *estimated amplified reach* (*portée amplifiée estimée*) with methodological caveat |

---

## 2. Composite Global Score Formula

$$\text{Global Consistency Score (/10)} = \frac{\text{P1 (ToV)} + \text{P2 (Dark Social)} + \text{P3 (Velocity)} + \text{P4 (Conversion)}}{4}$$

### Qualitative Performance Tiers (Strictly No Letter Grades)

| Score Range | Qualitative Tier Qualifier | CSS Badge Class | Strategic Meaning |
|:---:|:---:|:---:|---|
| **8.0 – 10.0 / 10** | *Excellence & Strong Cohesion* | `.score-high` | High brand authority, optimized omnichannel presence |
| **6.0 – 7.9 / 10** | *Moderate Cohesion in Consolidation* | `.score-medium` | Solid foundation, actionable tactical gaps identified |
| **< 6.0 / 10** | *Critical Misalignment* | `.score-low` | Major structural dissonance, broken touchpoints, urgent remediation needed |

---

## 3. Gap Resolution Matrix & Statuses

Every identified brand gap is assigned one of three deterministic lifecycle statuses:

- `🟢 RESOLVED` — Flaw or gap has been completely remediated by the brand.
- `🟡 IN_PROGRESS` — Partial progress, improved trajectory, or mitigation in progress.
- `🔴 PERSISTENT` — Flaw remains unaddressed and active across audit iterations.

> **1:1 Actionability Invariant:** Every gap marked `🔴 PERSISTENT` or `🟡 IN_PROGRESS` must receive a dedicated 4-tier tactical blueprint (Business Diagnostic, Platform Lever, Step-by-Step Rollout, Impact KPI).
