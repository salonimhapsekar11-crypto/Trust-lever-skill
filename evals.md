# Trust Lever Audit — Evaluation Loop

Use this file two ways:
1. **Single-agent self-check** — after producing every audit, run through the 14 checks below silently and append a compact pass/fail summary to the bottom of the HTML report, per SKILL.md rule 6.
2. **Two-agent eval loop** — if any check still fails after self-revision, the user should run the same page description through `trust-lever-eval-loop-v2.jsx` (a separate clean-context grading pass) before sharing the report externally. That artifact is not bundled here; it is a companion tool referenced for teams that want a second, context-free reviewer.

---

## The 14 Structural Checks

**Setup & framing**
1. Assumed target audience is stated in one sentence before any scoring appears.
2. Brand type (challenger vs scaled) is stated, and Authenticity is scored against the matching route (A or B), not both.

**Above the fold**
3. Above-the-fold contains brand mark, one-line thesis, and score chips only — no paragraphs.
4. No em-dashes anywhere above the fold.
5. No heavy/dense text blocks above the fold.

**Scoring integrity**
6. All 5 levers (Authenticity, Social Proof, Transparency, Familiarity, Risk & Safety) are scored 1–5 with the dot notation (●●●○○).
7. Total score is summed correctly out of 25 and mapped to the correct band (Trust-strong / developing / at risk / absent).
8. Every Critical (1–2) score has a specific note on what's missing and why it creates friction, not just a number.

**Quick wins vs recommendations**
9. Quick wins are real design opportunities a product designer can act on — not typos, spelling, or copy-only fixes.
10. Each quick win names what's missing, which lever it addresses, and what the fix looks like.
11. Priority recommendations include effort signal (Low/Medium/High) and which trust layer (identity/credibility/purchase confidence) each addresses.

**Competitor benchmark**
12. Competitor benchmark is present by default (never asked for) and uses interactive filter buttons if more than one market or adjacent category was named in the prompt.
13. Audited brand is marked "you are here" in the competitor table.

**Research plan**
14. "What to Validate With Real Users" section includes hypotheses framed as testable assumptions, at least two research methods with a stated use case, and specific funnel data points (not generic "run some tests").

---

## Scoring the Self-Check

- **12–14 pass:** Deliver as-is.
- **9–11 pass:** Revise failing sections once, then re-check. Deliver if it reaches 12+.
- **Below 9 pass, or still failing after one revision:** Deliver the report but flag clearly at the bottom which checks failed, and recommend a clean-context pass through the two-agent eval loop before the report is shared externally.

## Common Failure Patterns
- Quick wins that are actually copy edits ("fix the typo in paragraph 3") — these are not design opportunities and should be dropped or reframed.
- Competitor benchmark scored from memory instead of visible page evidence, presented as current fact.
- Research methods listed without a "best for" — a method with no stated use case is filler, not a plan.
- Above-the-fold paragraph creeping in under the guise of a "brand story intro."
