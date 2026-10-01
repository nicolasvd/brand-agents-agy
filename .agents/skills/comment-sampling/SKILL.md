---
name: comment-sampling
description: >-
  Deterministic qualitative comment sampling skill. Extracts 3 to 5 authentic first-level user verbatims on top-performing social posts with fast-exit handling for zero or disabled comments.
---

# Skill: comment-sampling

**Role:** Qualitative sentiment extractor and audience reception auditor.  
**Execution Context:** Wave 1 browser scanners (LinkedIn, Instagram, TikTok, Facebook, YouTube, X).  
**Core Invariant:** Extract strictly authentic user verbatims directly from DOM. Never summarize, rewrite, or hallucinate comments.

---

## 1. Objectives

- Capture the real voice of the community across the top 3 highest-resonance posts per audited social platform.
- Detect customer service overflow, community sentiment, recurring objections, or praise.
- Provide empirical grounding for the Wave 2 Tone of Voice (ToV) evaluation.

---

## 2. Sampling Protocol

For each of the Top 3 posts identified on a platform:

### Step 1: Comment Count & Accessibility Check (Fast-Exit)
1. Inspect the total comment counter in the DOM.
2. If `total_comments == 0` OR comments are explicitly turned off:
   - Record `comment_status: NONE_OR_DISABLED`.
   - **Immediately halt comment extraction** for this post (Fast-Exit).
   - Do not poll, wait, or retry. Proceed to the next post.

### Step 2: Verbatim Extraction (3 to 5 Comments)
If comments exist and are accessible:
1. Extract between **3 and 5 first-level comments** (ignore nested sub-replies unless directly clarifying the primary comment).
2. For each comment, capture:
   - `author`: Public profile name or professional title (e.g., "Courtier indépendant", "Directeur Marketing", or obfuscated handle if privacy-sensitive).
   - `verbatim`: The exact verbatim quote as written in the DOM (verbatim text, emoji included).
   - `likes`: Reaction / like count on the comment itself (or 0 if none).
3. Check for brand response:
   - Note whether an official account reply (`brand_replied: true/false`) exists on complaints or questions.

---

## 3. Output Schema (YAML / Markdown)

```yaml
top_posts_qualitative_sample:
  - post_url: "https://www.linkedin.com/feed/update/urn:li:activity:..."
    reactions: 142
    reposts: 18
    total_comments: 9
    comment_status: "ACTIVE"
    comments:
      - author: "Broker Partner"
        verbatim: "L'application mobile plante toujours sur iOS 18 lors de la déclaration de sinistre."
        likes: 5
        brand_replied: false
      - author: "Client Particulier"
        verbatim: "Excellente initiative pour la prévention routière !"
        likes: 2
        brand_replied: true
  - post_url: "https://www.linkedin.com/feed/update/urn:li:activity:..."
    reactions: 85
    reposts: 4
    total_comments: 0
    comment_status: "NONE_OR_DISABLED"
    comments: []
```

---

## 4. Downstream Utilization (Wave 2 Integration)

- Ingested by `brand-sub-analyst` to test for unaddressed customer friction.
- Feeds the Conversational Ratio calculation and informs the Tone of Voice capping rule.
