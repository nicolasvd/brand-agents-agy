---
name: incremental-crawl-protocol
description: >-
  5-step incremental crawl and re-audit protocol for brand social channels. Implements pinned post bypass, K=2 termination counter, engagement trajectory tracking, and screenshot restraint.
---

# Skill: incremental-crawl-protocol

**Role:** High-efficiency, low-footprint re-audit engine for social platforms.  
**Execution Context:** Wave 1 Browser Scanners (`brand-lead` → native browser subagents).  
**Core Invariant:** Never duplicate or re-scrape already archived posts. Maintain cumulative longitudinal history.

---

## 1. Context & Ingestion Contract

Triggered when `AUDIT_MODE == INCREMENTAL_UPDATE`. The scanner is supplied with previous historical state extracted from `reports/{slug}/markdown/channels/{platform}.md`:
- `known_post_urls`: Array of canonical post URLs already documented in the cumulative archive.
- `latest_post_date`: Publication date of the most recent post recorded in the prior audit.
- `header_screenshot`: Path to the existing valid header screenshot.
- `top_posts_to_recheck`: Array of top-performing post URLs and baseline metrics to re-evaluate for engagement growth trajectory ($\Delta$).

---

## 2. The 5-Step Protocol

### Step 1: Header & Bio Inspection (Screenshot Reuse)
- Navigate to the channel profile.
- Inspect bio text, handle, verification status, and follower count (zero following).
- **Screenshot Restraint:** If avatar, banner, and bio are visually identical to the archive and `header_screenshot` exists:
  - Reuse the existing `header_screenshot`.
  - Do NOT capture a new header screenshot.
  - Only capture a fresh header screenshot to `reports/{slug}/assets/screenshot-{platform}-{date_compact}.png` if branding or bio has changed.

### Step 2: Feed Crawl with Pinned Bypass & $K=2$ Termination
- Scroll progressively down the feed/grid (`window.scrollBy(0, 500)`).
- **Pinned Post Bypass:** Social networks often pin 1 to 3 prominent posts to the top of profiles.
  - Inspect each post for pinned indicators (pin icon, "Pinned", "Épinglé").
  - If a pinned post is already known or older, record its latest engagement if needed, but **do NOT increment the termination counter**.
- **Termination Counter ($K=2$):**
  - For unpinned posts, check if `post_url` is in `known_post_urls` OR publication date $\le$ `latest_post_date`.
  - Maintain consecutive match counter $K$.
  - When $K = 2$ consecutive unpinned posts are recognized as known or older, **halt scrolling immediately**.

### Step 3: Longitudinal Engagement Re-check ($\Delta$ Trajectory)
- For each post listed in `top_posts_to_recheck`:
  - Fetch fresh reactions, comments, and shares/reposts.
  - Compute the delta relative to baseline:
    $$\Delta \text{Metric} = \text{Fresh Metric} - \text{Baseline Metric}$$
  - Record the trajectory (e.g., `72 -> 88 (+16 👍)`).

### Step 4: Post Screenshot Restraint
- Capture **zero screenshots** for previously archived posts.
- Capture at most **1 screenshot** ONLY if a newly published post demonstrates breakout virality or exceptional strategic significance (save to `reports/{slug}/assets/{platform}-post-{date_compact}-breakout.png`).

### Step 5: Cumulative Table Merge & YAML Frontmatter Update
- Prepend newly scraped posts above previously known posts in the cumulative markdown table.
- Update frontmatter:
  - Increment `total_audits`.
  - Update `latest_audit_date: "{date}"`.
  - Update `latest_post_date: "{newest_post_date}"`.
  - Update `top_posts_to_recheck` list with current top performers.
- Write merged buffer to `.agents/.scratchpad/{slug}/w1-{platform}.md`.
