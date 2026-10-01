# Workspace Rules — AI Brand Strategy Team (brand-agents-agy)

## 1. Zero Hallucination & Fact Integrity
- Never invent, extrapolate, or guess company metrics, follower counts, view numbers, tech stacks, or executive names.
- If a data point cannot be verified via reliable sources, explicitly write `Unverified` or `Not available`.
- Adhere strictly to epistemic rigor: never assert unverified advertising spend ("Paid Media") without direct DOM badge proof.

## 2. Passive Safety (Read-Only External Posture)
- Never publish posts, submit web forms, send messages, or mutate third-party platforms.
- All brand intelligence audits and deliverables are local artifacts only.

## 3. Context & Scratchpad Hygiene
- Subagents must never modify files outside their designated `.agents/.scratchpad/{slug}/` scope.
- Internal reasoning, logs, and prompt contracts operate in English. Match the user's language (French or English) in final executive summaries and narrative deliverables.
