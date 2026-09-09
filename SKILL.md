---
name: trust-lever-audit
description: Audits beauty ecommerce and health brand landing pages against a 5-lever purchase confidence framework. Outputs a structured scorecard with scores, observations, quick wins, priority recommendations, competitor comparison, and a user research plan. Use when user shares a landing page screenshot, asks 'does this page build trust', 'why isn't this converting', 'audit this page', 'review this landing page', 'trust audit', 'conversion analysis', 'brand credibility review', or requests a CRO or UX review. Primarily covers clean beauty, K-beauty, skincare, supplements, probiotics, and health tech. Other industries require additional calibration.
metadata:
  author: Saloni
  version: 3.6.0
---

# Trust Lever Framework — Audit Skill

## How to run this skill — read first

This is the operating contract. Follow it exactly on every run.

**The flow:** the user gives a screenshot (or URL) and a short prompt. You produce a single self-contained HTML one-pager with the full analysis. That HTML report is the deliverable — always.

**Hard rules:**
1. **Always output the HTML report. Never deliver the audit as plain chat text.** A short framing line in chat is fine, but the audit itself — Page Read, scorecard, quick wins, recommendations, competitor view, research plan — lives in one HTML file saved to disk and served locally. If you find yourself writing the scorecard as chat text, stop and build the HTML instead.
2. **Do not ask clarifying questions.** Proceed with sensible defaults and state any assumption inline in the report's Page Read. The user's screenshot plus a short prompt is enough to start. Only pause if the screenshot is missing or unreadable.
3. **Start from this SKILL.md, not the reference files.** The full method is contained here. Do not read or wait on `references/example.md` before producing an audit — it is an optional quality reference, never a blocking step. Never tell the user an example file is missing.
4. **Multiple markets or industries → build interactive filter buttons.** If the prompt names more than one market (e.g. EU, UK, US) or more than one adjacent category, do not ask how to present them and do not write them out as separate text blocks. Build the competitor benchmark as an interactive switcher with filter buttons, defaulting to the first market named. Score only the markets the user asked for.
5. **Mirror the brand's design** in the HTML — palette, typography weight, tone — so the report reads as native. Keep the above-the-fold light: no heavy text blocks, no em-dashes there.
6. **After producing the audit, always run a self-check against `references/evals.md` before delivering.** Read evals.md, run through all 14 structural checks silently, and append a compact eval summary block at the bottom of the HTML report showing which checks passed and which failed. If any check fails, revise that section before output — do not deliver a report with a known failing check. This is a single-agent self-review, not the full two-agent loop, but it must run on every audit. **If any check still fails after self-revision, flag it clearly at the bottom of the report and instruct the user to run the same page description through the two-agent eval loop artifact (`trust-lever-eval-loop-v2.jsx`) for a clean-context evaluation before sharing the report externally.**

**HTML design rules (always apply):**
- No em-dashes or heavy text above the fold
- Above the fold: brand mark, one-line thesis, score chips only — no paragraphs
- Quick wins must be meaningful design opportunities a product designer can act on, not typos or copy fixes
- Competitor benchmark always uses interactive filter buttons to switch between markets and adjacent categories
- User research section always includes: hypotheses, at least two research methods (unmoderated test, qualitative interviews, diary study, or five-second test), and specific funnel data points to examine

Everything below is the method the HTML report applies.

## Bundled files (optional references — never block on these)
- `references/evals.md` — pass/fail criteria and the evaluation loop. For grading an audit's quality, not for producing one.
- `references/example.md` — three worked examples (rebuy, rhode, Natural Cycles). An optional quality reference. Do not read it as a prerequisite to running an audit.
- `references/memory.md` — running notes on brands audited. Optional.

## What This Audit Measures

Trust on a landing page operates at three levels:

- **Identity trust** — does the brand feel like it was made for someone like me?
- **Credibility trust** — is this brand who it says it is, and can I verify that?
- **Purchase confidence** — is it safe enough for me to say yes right now?

This audit examines all three through five observable levers. It is a snapshot of one page, for a cold or sceptical audience, at the point of first contact. It does not measure long-term brand trust, which is built across the entire customer relationship.

The audit is grounded only in what is visible on the page. If a signal is not visible to the user, it does not count.

---

## Score Thresholds

### Per lever — 3 bands

| Score | Band | What to do |
|-------|------|------------|
| 4–5 | Pass | Lever is well-handled. Note what is working. No immediate action needed. |
| 3 | Caution | Lever is partially present but inconsistent or unexplained. Flag in recommendations with a specific note on what is missing and why it creates friction. |
| 1–2 | Critical | Lever is weak or absent. Elevate to priority recommendations immediately. A Critical on Identity trust levers (Authenticity, Familiarity) or Risk & Safety for a high-consideration product is a conversion-critical gap. |

### Total score — 4 bands out of 25

| Score | Band | Signal |
|-------|------|--------|
| 21–25 | Trust-strong | Benchmark-competitive. Focus on optimisation and differentiation, not trust repair. |
| 15–20 | Trust-developing | Core signals present but gaps likely harming conversion at the consideration stage. Prioritise by lever. |
| 9–14 | Trust at risk | Multiple levers weak or absent. Trust is likely a primary drop-off cause. Recommend research before redesign. |
| Below 9 | Trust absent | Page is not equipped to convert a sceptical buyer. Address structural gaps before any CRO testing. |

**Note:** Always contextualise the total score against product type and price point. A 14/25 with Critical scores on Authenticity and Familiarity for a £80/month subscription skincare product is more urgent than a 12/25 spread across levers for a low-AOV single purchase.

---

## Before You Score

State two things before scoring:

1. **Assumed target audience** — one sentence. This anchors Familiarity scoring and frames all lever observations.
2. **Brand type — challenger or scaled.** This determines which route the Authenticity lever is scored against (see below). A challenger or D2C brand earns authenticity through founders and story; a scaled or faceless brand earns it through longevity, third-party standing, and process transparency. Auditing a scaled brand against "is there a founder story" would unfairly penalise a brand that is trustworthy through scale.

Do not score until both are stated.

---

## The 5 Trust Levers

### 1. Authenticity
**User question:** Is this a real, accountable brand that will actually stand behind the product?

The underlying question is not "is there a founder story" — it is "is there a real, accountable entity behind this that will stand behind what it sells." A founder story is one way to answer that. A scaled or faceless brand answers it differently. Score against the route that fits the brand type stated in the Page Read. A brand can reach a 5 on either route.

**Route A — Founder / challenger brand**
Best for D2C, challenger, and early-stage brands. Observable signs:
- Founder or origin story present and specific
- Named people behind the brand, not just a logo
- Doctor-authored, formulator-authored, or expert-authored content
- Credentials are verifiable, not just decorative
- Sourcing or formulation explained publicly in the brand's own voice

**Route B — Institutional / scaled brand**
Best for large, established, or faceless brands with no individual to foreground. Observable signs:
- Longevity and operational scale stated plainly (founded year, units shipped, customers served, stores, countries)
- Verifiable third-party standing — stock listing, regulatory registration, recognised certifications, credible press, named review platforms (eKomi, Trustpilot)
- Process and infrastructure transparency — the testing, refurbishment, supply chain, or labs behind the product, showing real systems and people even when none are named
- Accountability surface — reachable support, real address, named policies, visible responsiveness to reviews
- Category authority — being the default, OEM partnerships, or the platform other brands build on

**Score anchors (apply to whichever route fits):**
| Score | What it looks like |
|-------|--------------------|
| 5 | Strong, specific, verifiable accountability. Route A: named founder, specific origin story, verifiable credentials, sourcing explained. Route B: clear longevity and scale, third-party standing, and process transparency all present |
| 4 | Accountability present but one dimension thin. Route A: founder mentioned but story shallow, or credentials not independently verifiable. Route B: scale and standing strong but process behind the product not shown |
| 3 | Some accountability signal but shallow. Route A: "about" section exists but no named humans. Route B: longevity stated ("est. 2015") but no third-party proof or process visible |
| 2 | Vague gestures only — "our experts", "trusted by millions" with no names, numbers, or verification on either route |
| 1 | No authenticity signals visible — logo only, anonymous brand, no story and no institutional proof |

**Benchmark references:** Ritual (Route A — named founder, sourcing mapped publicly). rebuy (Route B — twenty years, six million customers, recognised third-party rating stated early).

---

### 2. Social Proof
**User question:** Has this worked for someone like me?

**Observable signs:**
- Before/after with specific condition named
- Review source attributed (Trustpilot, verified purchase, etc.)
- Reviews that feel real — mix of positive and critical
- Demographic or condition specificity in testimonials
- Volume of reviews visible and credible
- Video or named photo testimonials

**Score anchors:**
| Score | What it looks like |
|-------|--------------------|
| 5 | Reviews attributed to specific conditions or demographics, source verified, mix of positive and critical visible, video or photo testimonials with names |
| 4 | Strong review volume and attribution but no critical reviews, or specificity missing |
| 3 | Generic positive reviews present, source unnamed or unverified |
| 2 | One or two quotes with no attribution or verification |
| 1 | No social proof visible |

**Benchmark reference:** Skin + Me — condition-specific reviews, dermatologist context given.

**Manufactured-signal check:** Apply the manufactured-signal modifier below before finalising this score. Reviews that read as fabricated cap the lever at 2 regardless of volume.

---

### 3. Transparency
**User question:** Do I know exactly what I am getting into?

**Observable signs:**
- Statistics shown with methodology explained
- Active ingredient names and concentrations visible
- What the product cannot do is stated
- Who the product is not for is stated plainly
- Limitations of the science acknowledged
- Data processing and storage communicated
- Pricing and subscription terms clear upfront

**Score anchors:**
| Score | What it looks like |
|-------|--------------------|
| 5 | Methodology explained, limitations of science acknowledged, what the product cannot do stated plainly, pricing and subscription terms upfront |
| 4 | Ingredients and pricing transparent but limitations or methodology not stated |
| 3 | Some ingredient information visible but concentrations missing, or pricing buried |
| 2 | Generic claims ("clinically proven") with no supporting detail |
| 1 | No transparent information — all claims, no evidence |

**Benchmark reference:** Zoe — science limitations stated, what it cannot yet tell you acknowledged.

---

### 4. Familiarity
**User question:** Does this feel like an experience I recognise and can navigate confidently?

Score Familiarity only relative to the assumed target audience stated before scoring. Do not score against a universal standard.

**Observable signs:**
- Consistent clinical or brand language throughout
- Imagery feels real and unretouched
- Tone matches the assumed audience (clinical-casual for health, warm for wellness)
- Navigation and layout follows expected patterns for this category
- No jarring tonal or visual inconsistencies
- Diverse and representative imagery that reflects the intended buyer
- Models and skin tones match the audience the product claims to serve

**Score anchors:**
| Score | What it looks like |
|-------|--------------------|
| 5 | Tone, imagery, and layout fully consistent and precisely matched to the assumed audience throughout — no moments of friction |
| 4 | Consistent overall with one or two tonal or visual inconsistencies that do not derail the experience |
| 3 | Generally recognisable but noticeable gaps — warm copy with overly clinical imagery, or layout that breaks convention in a confusing way |
| 2 | Significant inconsistencies — tone shifts, mismatched imagery, or layout that creates confusion |
| 1 | Experience feels unfamiliar or untrustworthy for this audience — no clear tonal or visual coherence |

**Benchmark reference:** Hims/Hers — clinical-casual tone consistent, imagery feels real not aspirational.

---

### 5. Risk & Safety
**User question:** Do I feel protected enough to say yes?

**Observable signs:**
- Money back guarantee visible at point of purchase
- Certifications visible (GMP, ISO, third-party tested)
- Allergen and ingredient transparency
- Clinical study or trial references
- Cancellation and return terms upfront, not buried
- Free trial or no-commitment messaging where relevant
- Regulatory language present

**Score anchors:**
| Score | What it looks like |
|-------|--------------------|
| 5 | Guarantee above the fold, third-party certifications downloadable or linked, return and cancellation terms upfront |
| 4 | Guarantee present and certifications visible but terms not fully upfront |
| 3 | Money back guarantee mentioned but buried, or certifications present with no verification link |
| 2 | Vague safety language ("safe and effective") with no supporting signals |
| 1 | No risk reduction signals visible — no guarantee, no certifications, no terms |

**Benchmark reference:** Care/of — certificates downloadable, guarantee above fold.

---

## Scoring System

Score each lever 1–5 using the anchors above. Apply the per-lever bands and total score bands from the Score Thresholds section at the top.

**Consistency rule:** If a lever is partially present, always note what exists and what is missing. Partial presence with no reasoning given = maximum score of 3.

**Benchmark brands** (Ritual, Skin + Me, Zoe, Hims/Hers, Care/of) calibrate the score anchors only. They are not scored themselves. Do not assume current knowledge of their live sites — use them as reference points for what strong signals look like, not as live comparisons.

### Manufactured-signal modifier

A signal that reads as manufactured erodes trust more than an absent one, because it trips a visitor's scepticism. The scale must be able to register this, so presence alone is never enough — the signal also has to read as earned.

You are not detecting fraud. You cannot prove a review is fake from the page; only a platform with backend data can. What you assess is whether a signal reads as credible or manufactured to a sceptical visitor. Score the signal, not your suspicion. State findings as a visitor risk ("a sceptical buyer may read these as manufactured"), never as an accusation ("these are fake").

Apply this mainly to Social Proof, and to Authenticity where AI-generated founder photos or fabricated press are plausible. The research-backed suspicion cues, drawn from the consumer fake-review detection literature (Walther et al., 2023; Journal of Retailing and Consumer Services, 2022):

- **Uniform valence** — every review positive, no critical or mixed voice. The single strongest cue.
- **Generic, detail-free language** — "great product, love it" with no specific circumstance, condition, or timeline.
- **No attribution** — no names, photos, verified-purchase tags, dates, or third-party source on the rating.
- **Suspiciously perfect or templated register** — flawless, formal, near-identical phrasing across reviews. Counter-intuitively, too perfect is itself a tell now that AI can generate reviews at scale.
- **Unnamed aggregate source** — a star number on the brand's own page with no link to a named third party (Trustpilot, App Store, eKomi).

**The rule:** if two or more cues converge on a signal, that signal scores no higher than 2 on its lever, even when the signal is technically present and high-volume. A single cue is not enough — require convergence before flagging, so the audit does not over-read one weak review.

### Critical-lever cap

A strong total can hide one broken signal at the decision point. One conversion-critical trust failure is not offset by a beautiful aesthetic elsewhere. So any lever scored 1 or 2 (Critical) caps the overall band at "Trust at risk" or lower, regardless of the numeric total. Lead the verdict with that lever, not the average.

### What not to do

These are the failure modes the rules above exist to prevent. Check the finished audit against them.

- **Do not cluster every lever at 3 or above.** A scorecard where nothing drops below 3 is a sign the anchors were read leniently, not that the page is strong. Most real pages have at least one lever that is genuinely weak. If every score lands 3–5, re-read the 1 and 2 anchors and the manufactured-signal modifier before accepting it. A 3 is a real finding ("partial, inconsistent"), not a polite default.
- **Do not score on presence alone.** A signal that is present but generic, buried, or manufactured is not a pass. Volume of reviews, a guarantee in the footer, or an "about" link all exist, yet may do no trust work. Score whether the signal is read and believed, not whether it is technically there.
- **Do not flag fakeness on a single cue, and never call reviews fake.** The manufactured-signal modifier needs two or more convergent cues, and even then the finding is framed as visitor risk ("may read as manufactured"), not an accusation. One uniform-positive review set alone is a note, not a flag. Weigh countervailing credibility (strong attribution, named reviewers) before capping.
- **Do not let the total override a Critical lever.** A 20/25 with a Critical on Risk & Safety is "Trust at risk", not "Trust-developing". Lead with the broken lever. Averaging is forgiving by design; the cap exists to stop that.
- **Do not invent signals that are not on the page.** Score only what is visible. If a guarantee, certification, or founder story is not shown, it is not present for the user either — do not credit it from outside knowledge of the brand.
- **Do not skip brand-type classification.** Scoring a scaled, faceless brand on the founder route (Route A) will wrongly tank its Authenticity. State challenger or scaled first, then score the matching route.
- **Do not let quick wins drift into trivia.** Quick wins are structural or visual design opportunities, not typos, copy nits, or colour tweaks. If a product designer could not meaningfully act on it, it does not belong there.
- **Do not deliver only an inline summary.** The deliverable is the brand-mirrored HTML report. A chat summary is a preview of it, not a substitute.

---

## References

The manufactured-signal modifier and the suspicion cues are grounded in the consumer fake-review detection literature, not intuition. Cite these when the method is challenged:

- Walther, M. et al. (2023). *A systematic literature review about the consumers' side of fake review detection — which cues do consumers use to determine the veracity of online user reviews?* Classifies consumer detection cues into five categories: review, textual, reviewer, seller, and platform characteristics.
- Salminen, J. et al. (2022). *Creating and detecting fake reviews of online products.* Journal of Retailing and Consumer Services, 64. On fake reviews eroding trust in the review system as a whole.
- Research on consumer suspicion (vignette studies) on the cues of comprehensibility, specificity, exaggeration, and negligence, and on AI-generated reviews where suspiciously perfect or over-specific language is itself a tell.
- PowerReviews (2022) survey of ~13,000 US shoppers: 81% are concerned about fake reviews and 63% are more concerned than five years ago — useful framing for the scale of perceived-fakeness risk.

These support the core stance: the audit scores *perceived* credibility, because trust erosion is driven by what a sceptical visitor perceives, not by verified fraud the auditor cannot prove from the page.

---

## Output Format

**Required deliverable:** every audit is delivered as a self-contained HTML page, saved locally and served so the user can open it in a browser. Inline chat summaries are a preview, not the deliverable. The HTML report mirrors the audited brand's design language (palette, typography weight, tone) so it reads as native to the brand. It carries every section below in order, uses the dot system for lever scores, and keeps the above-the-fold area light — no heavy text blocks, no em-dashes there. See `references/example.md` for the structure and quality bar.

### Step 1 — Page Read
State:
- Industry and product type
- Assumed target audience (one sentence)
- Brand type — challenger or scaled (determines the Authenticity route)
- Any identity trust considerations specific to this brand — provenance, model representation, language, cultural context

### Step 2 — Scorecard

Mirror the design language of the page being reviewed in the report output — reflect the typography weight, tone, and colour palette so the report feels native to the brand rather than generic.

| Trust Lever | Score /5 | Band | What They Do Well | Key Gap |
|-------------|----------|------|-------------------|---------|
| Authenticity | | | | |
| Social Proof | | | | |
| Transparency | | | | |
| Familiarity | | | | |
| Risk & Safety | | | | |
| **Total** | **/25** | | | |

### Step 3 — Quick Wins

Identify 2–4 meaningful design opportunities a product designer can act on independently. These should be:
- Directly tied to a lever gap visible on the page
- Medium effort — not typos or copy tweaks, but structural or visual changes with real conversion impact
- Achievable without a full redesign or cross-functional dependency

For each quick win:
- What is missing or misplaced
- Which lever it addresses
- What the fix looks like in practice

**Examples of quick wins:** guarantee badge buried below the fold → move above CTA; review attribution missing → add source label and verified purchase tag; founder name present but no face or story → add one paragraph with photo; ingredient list present but concentrations hidden in FAQ → surface on product card.

### Step 4 — Priority Recommendations

Ranked by impact. For each:
- What is missing
- Why it matters for this specific brand and audience
- What good looks like (reference benchmark where relevant)
- Effort signal: Low / Medium / High
- Which trust layer it addresses (identity trust / credibility trust / purchase confidence)

### Step 5 — What to Validate With Real Users

Based on the lever gaps identified, state:

**Hypotheses to test** — translate each Critical or Caution lever into a testable assumption. For example: "We believe buyers are dropping off at the pricing section because subscription terms are not visible upfront."

**Recommended research methods:**

| Method | Best for |
|--------|----------|
| Unmoderated usability test | First-impression trust signals — what does a cold visitor notice, question, or miss in the first 30 seconds? |
| Qualitative interviews | Hesitation moments and decision language — what words do buyers use when they're unsure? What would make them feel safer? |
| Diary study | Subscription or health products where trust evolves — track how confidence changes from first visit to first use to renewal |
| Five-second test | Above-the-fold clarity — can a new visitor identify what the product is, who it's for, and why they should trust it within five seconds? |

**Funnel data to examine:**
- Scroll depth at each trust signal section (guarantee, reviews, ingredient list, pricing)
- Heatmaps and click maps around the primary CTA and pricing area
- Session recordings at the consideration stage — look for hesitation patterns, back-navigation, and FAQ visits before drop-off
- Drop-off rate between product page and checkout initiation
- Return visit rate before first purchase — high return rate often signals a trust gap, not a product gap

### Step 6 — Competitor Benchmark (always included, never asked)

Include a competitor benchmark in every audit by default. Do not ask whether the user wants one, and do not ask which market to use — infer the market(s) from the prompt and the page.

- Identify the closest 4–5 competitors for the brand's category and market, and score each on the same five trust levers using the dot system.
- **If the prompt names more than one market** (e.g. EU, UK, US), build the benchmark as an interactive switcher with filter buttons, one per named market, defaulting to the first. Each market shows its own relevant competitor set. Do the same for adjacent categories where relevant. Score only the markets the user named.
- Mark the audited brand with a "you are here" tag so its position against the field is instantly legible.
- Frame scores as a directional read of public positioning, not a full teardown.

---

## Competitor Scoring Format

Score each competitor on the same 5-lever, 1–5 scale. Display scores using a dot system for fast visual scanning:

● = filled (lever present) | ○ = absent

Each score maps to dots as follows: 1 = ●○○○○, 2 = ●●○○○, 3 = ●●●○○, 4 = ●●●●○, 5 = ●●●●●

| Brand | Authenticity | Social Proof | Transparency | Familiarity | Risk & Safety | Total /25 | Standout signal |
|-------|-------------|--------------|--------------|-------------|----------------|-----------|-----------------|
| [Competitor A] | ●●●●○ 4 | ●●●○○ 3 | ●●○○○ 2 | ●●●●● 5 | ●●●○○ 3 | 17 | [One line: what they do that the audited brand does not] |

The standout signal column should identify the single lever or signal where the competitor meaningfully outperforms the audited brand — and what a designer could learn from it.

---

## Industry-Specific Notes

This skill is calibrated for the following categories. Other industries can use the framework but require additional lever calibration not included here.

### Clean Beauty / K-Beauty / Skincare
- **Identity trust is the dominant lever.** Provenance mismatches (founded in one country, produced in another, modelling a third demographic) create legitimacy gaps that no amount of certification fixes. Audit Familiarity and Authenticity first.
- Unretouched or minimally retouched imagery is a strong Familiarity signal — AI-polished skin reads as fake to an increasingly sceptical buyer
- Condition-specific social proof outperforms generic positive reviews
- Dermatologist or formulator attribution adds significant Authenticity weight
- Ingredient transparency (INCI names, concentrations) is expected by an informed buyer in this category

### Supplements / Nutrition / Probiotics
- Risk & Safety carries extra weight — fear of harm or ineffectiveness is a real conversion blocker
- Ingredient transparency is non-negotiable: strain specificity for probiotics, dosage and source for supplements
- Before/after claims are heavily scrutinised — specificity, attribution, and realistic timelines matter
- Third-party testing certification (Informed Sport, NSF, USP) is a strong differentiator
- Social proof needs condition or goal specificity — "helped my bloating" outperforms "great product"

### Health Tech
- Data privacy and storage transparency functions as a standalone trust lever in this category
- Clinical credibility signals (peer-reviewed references, trial citations) matter more here than in beauty
- Guidance through complex or diagnostic products needs to feel reassuring, not clinical
- Familiarity scoring should account for the fact that health tech buyers are often anxious, not just sceptical — tone and layout need to reduce cognitive load, not add to it

### Extending to Other Industries
If applying this skill outside the three categories above, note the following before scoring:
- The lever definitions and score anchors were calibrated for high-consideration, direct-to-consumer health and beauty products with a cold audience
- Categories with different purchase dynamics (low-AOV impulse products, B2B, marketplace listings) will need lever weighting adjusted and new score anchors defined
- Flag in the Page Read step that the audit is operating outside its primary calibration range

---

## General Notes
- Always analyse only what is visible on the landing page unless told otherwise
- Flag if the page is in a language other than English and note any cultural trust conventions that may apply — particularly relevant for K-beauty brands marketing in Western markets
- Do not infer signals that are not visible — if you cannot see it, it is not present for the user either
- Benchmark brands are references for what a 5 looks like — do not assume current knowledge of their live sites
- The audit does not distinguish between genuine and manufactured trust signals — it reads what is visible. Whether the signals are earned or constructed is a question for the design team and research, not the audit itself
