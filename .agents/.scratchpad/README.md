# Antigravity Scratchpad Specification & Architecture — Brand Strategy

Transient inter-agent buffer for multi-agent workflows orchestrated by `brand-lead`.

> [!IMPORTANT]
> **Ephemeral Storage:** Files under `.agents/.scratchpad/{slug}/` (`w1-*.md`, `w2-draft-*.md`, `.done`) are ephemeral session buffers ignored by Git. Coordination, raw data ingestion, and draft synthesis schemas operate strictly in Markdown.

## Directory Structure

For each target brand slug `{slug}`:

```text
.agents/.scratchpad/{slug}/
├── w1-hub.md                # Homepage branding, value proposition, Open Graph tags & social links (brand-sub-hub-crawler)
├── w1-linkedin.md           # LinkedIn company bio, followers, cumulative post table & verbatims (browser subagent)
├── w1-instagram.md          # Instagram bio, followers, reels, grid posts & verbatims (browser subagent)
├── w1-tiktok.md             # TikTok bio, followers, likes, videos & verbatims (browser subagent)
├── w1-facebook.md           # Facebook page likes, followers, reaction typology & verbatims (browser subagent)
├── w1-youtube.md            # YouTube subscribers, cumulative channel views, videos & verbatims (browser subagent)
├── w1-x.md                  # X/Twitter bio, followers, tweets, impressions & verbatims (browser subagent)
├── w2-draft-audit.md        # Strategic audit critique, gap matrix, and 4-tier tactical blueprint (brand-sub-analyst)
├── w2-draft-brandbook.md    # Reverse brand book draft, tokens, and multi-audit history (brand-sub-analyst)
└── .done                    # Sentinel file indicating Styler completion and triggering GC cleanup
```

## Lifecycle State Machine

1. **Scratchpad Initialization:** Target directory `.agents/.scratchpad/{slug}/` created by `brand-lead`.
2. **Wave 1 (Hub & Parallel Channel Scans):**
   - Step 1: `brand-sub-hub-crawler` navigates to brand URL, captures screenshot, extracts Open Graph metadata, and outputs `w1-hub.md`.
   - Step 2: Native browser scanners run in parallel for all verified social channels, outputting `w1-{platform}.md` buffers with raw empirical metrics and semantic comment samples.
3. **Synchronization Barrier:** Wave 2 triggers only after all active Wave 1 crawler tasks complete.
4. **Wave 2 (Analyst Synthesis):** `brand-sub-analyst` ingests Wave 1 buffers (and historical archives in `reports/{slug}/markdown/` if in incremental mode), computes deterministic scores on the 10-point scale, and writes `w2-draft-audit.md` and `w2-draft-brandbook.md`.
5. **Promotion & Wave 3 Trigger (Styler):** `brand-lead` promotes scratchpad markdown files to permanent storage under `reports/{slug}/markdown/` and triggers `brand-sub-styler` asynchronously.
6. **Garbage Collection (Sentinel):** Once HTML compilation finishes, `brand-sub-styler` writes the `.done` sentinel file to `.agents/.scratchpad/{slug}/.done`. A background watchdog cleans up the ephemeral `.agents/.scratchpad/{slug}/` directory.
