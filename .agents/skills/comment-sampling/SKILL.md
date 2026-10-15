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

### Step 2: Verbatim Extraction & Full Conversational Loop (3 to 5 Comments)
If comments exist and are accessible:
1. Extract between **3 and 5 first-level comments** (focusing on discussions, objections, praise, or inquiries).
2. For each comment, capture:
   - `author`: Public profile name or professional title (e.g., "Courtier indépendant", "Directeur Marketing", or obfuscated handle if privacy-sensitive).
   - `verbatim`: The exact verbatim quote as written in the DOM (verbatim text, emoji included).
   - `likes`: Reaction / like count on the comment itself (or 0 if none).
3. **Capture the Full Conversational Loop (Brand Interaction):**
   - Inspect immediate sub-replies from the brand/creator account under each sampled comment.
   - If an official brand reply exists:
     * `brand_replied: true`
     * `brand_reply_author`: Official profile name (e.g. "Banque Triodos", "Socialsky")
     * `brand_reply_text`: Exact verbatim response from the brand account
     * `brand_reply_date`: Timestamp or relative date (or "Not available")
     * `conversational_stance`: Posture classification:
       - `Constructive Dialogue` (personalized substance, authentic technical or strategic answer)
       - `Support Deflection` (redirects to customer service e-mail/phone/form)
       - `Automated Template` (generic canned response, emoji-only reply)
   - If no brand reply is present on a comment that warranted follow-up (question, objection, critique):
     * `brand_replied: false`
     * `conversational_stance: "Radio Silence"`

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
      - author: "Thomas Dever (Head of Influence)"
        verbatim: "The diversity of answers says it all 🙂 Proper reporting to understand real ROI is a major focus in our influence vision!"
        likes: 1
        brand_interaction:
          brand_replied: true
          brand_reply_author: "Socialsky"
          brand_reply_text: "Thomas, agree. It all starts with the proper definition of brand objectives to translate into real impact."
          brand_reply_date: "2026-10-14"
          conversational_stance: "Constructive Dialogue"
      - author: "Broker Partner"
        verbatim: "L'application mobile plante toujours sur iOS 18 lors de la déclaration de sinistre."
        likes: 5
        brand_interaction:
          brand_replied: false
          conversational_stance: "Radio Silence"
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
