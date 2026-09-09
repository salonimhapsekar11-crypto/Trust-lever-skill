# Trust-lever-skill
A Claude skill that audits beauty, health, and wellness ecommerce landing pages against a 5-lever purchase confidence framework, and outputs a single self-contained HTML report.

What it does

Give it a landing page screenshot or URL and a short prompt. It reads the page for five trust levers — Authenticity, Social Proof, Transparency, Familiarity, and Risk & Safety — scores each 1–5, and produces:

A scorecard with total /25 and band (Trust-strong / developing / at risk / absent)
Quick wins: real design opportunities a product designer can act on next, never typo or copy fixes
Priority recommendations, ranked by impact, with effort signal and which trust layer they address
A competitor benchmark against the closest 4–5 brands, with interactive filters when more than one market or adjacent category is in scope (e.g. clean beauty → derma cosmetics → probiotics)
A "what to validate with real users" section: testable hypotheses, recommended research methods (unmoderated tests, qualitative interviews, diary studies, five-second tests), and specific funnel data to examine

The HTML report mirrors the audited brand's own visual language — palette, type weight, tone — rather than a generic dashboard template. Above the fold stays light: no em-dashes, no dense paragraphs.

Structure
trust-lever-audit/
  SKILL.md              — the full method and operating contract
  references/
    evals.md             — 14-point self-check run before every report ships
    example.md            — three worked examples across brand types and categories
    memory.md             — optional running log of brands audited over time
Calibration

Primary calibration: clean beauty, K-beauty, skincare, supplements, probiotics, health tech. Other categories can use the framework but need additional lever weighting — SKILL.md flags this automatically when applied outside its primary range.

Use

Load trust-lever-audit/SKILL.md as a Claude skill. Trigger phrases include "audit this page," "does this page build trust," "why isn't this converting," "trust audit," "CRO review," or sharing a landing page screenshot directly.
