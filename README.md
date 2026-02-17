# What Motorcycle Should I Buy? -- Interactive Quiz

An expert-level motorcycle recommendation quiz for [Riders Share](https://www.riders-share.com), the peer-to-peer motorcycle rental marketplace. This interactive tool guides users through 20 questions across 6 sections to deliver personalized motorcycle recommendations from a curated database of 214 models.

Built as a standalone web app hosted on GitHub and embedded on the Riders Share blog via iframe.

---

## What the Quiz Does

The quiz walks users through a structured decision framework that mirrors how experienced riders actually choose motorcycles. Instead of generic "pick a style" quizzes, this tool evaluates experience level, physical fit, riding environment, budget, ownership philosophy, and advanced preferences to surface 3-5 tailored recommendations.

Each result includes a primary recommendation (best overall match), a secondary alternative (same category, different character), and a used alternative when applicable. Every result page includes a Riders Share rental CTA so users can try before they buy.

## Model Database

214 motorcycles across 5 categories, split between currently available new models and curated used recommendations (including out-of-production legends).

| Category | New Models | Used Recommendations | Total |
|---|---|---|---|
| Cruiser | 15 | 30 | 45 |
| Standard / Naked | 12 | 25 | 37 |
| Sport / Sportbike | 12 | 30 | 42 |
| Adventure / Dual-Sport | 15 | 30 | 45 |
| Touring & Sport-Touring | 15 | 30 | 45 |
| **Total** | **69** | **145** | **214** |

The used-market section is intentionally the largest component. Out-of-production models like the Harley-Davidson Sportster Evolution, Yamaha V-Max, and Victory touring bikes are included alongside current used inventory. Used price ranges reflect private-party and dealer asking prices from Cycle Trader, Autotrader Motorcycles, and Facebook Marketplace as of early 2026.

## Quiz Structure: 20 Questions, 6 Sections

**Section 1 -- Riding Experience & Skill Assessment (Q1-Q3)**
Evaluates current experience level, highest displacement ridden with confidence, and formal training history. This section establishes the primary safety filter that governs all downstream recommendations.

**Section 2 -- Riding Environment & Use Case (Q4-Q7)**
Determines primary use case (commuting, recreation, touring, adventure, track, casual), paved/unpaved split, expected ride distances, and passenger requirements.

**Section 3 -- Physical Fit & Ergonomics (Q8-Q10)**
Captures height, inseam, and preferred riding position. Eliminates seat-height mismatches and flags bikes that may need lowering kits.

**Section 4 -- Budget & Ownership Philosophy (Q11-Q13)**
Sets the budget gate (6 tiers from under $5K to $25K+), willingness to buy used, and maintenance tolerance. This section determines whether the user enters the new-bike path, the used-bike path, or a hybrid recommendation set.

**Section 5 -- Style, Priorities & Ride Character (Q14-Q17)**
Multi-select priority ranking (comfort, agility, power, style, versatility, reliability), electronic rider aids importance, engine character preference, and brand loyalty.

**Section 6 -- Advanced Decision Factors (Q18-Q20)**
Weight management comfort, aftermarket/customization importance, and riding climate. These refine the final recommendation set with practical real-world considerations.

## Scoring & Recommendation Engine

The engine processes answers through 5 sequential stages:

**1. Experience Level Match (Q1-Q3)**
Primary safety filter. The engine never recommends a motorcycle above the user's validated experience tier. Cross-references self-assessed experience with displacement history and training to prevent over-self-assessment.

**2. Category Assignment (Q4-Q7)**
Determines the primary motorcycle category from use case, terrain preference, distance expectations, and passenger needs. Ties are broken by ergonomic preference from Q10.

**3. Physical Fit Filter (Q8-Q10)**
Eliminates bikes with seat heights that don't match the user's measurements. Flags models where a lowering kit could resolve a marginal mismatch. Riding position preference confirms or adjusts the category assignment.

**4. Budget Gate (Q11-Q12)**
Routes users into new, used, or mixed recommendation paths. Budgets under $5,000 always trigger the Used Path. Budgets under $8,000 for beginners strongly suggest used. Users who select "new only" (Q12:D) receive new-bike-only results regardless of budget.

**5. Refinement Factors (Q13-Q20)**
Maintenance tolerance, style priorities, electronics preference, engine character, brand loyalty, weight comfort, aftermarket importance, and climate filter the remaining pool down to 3-5 final recommendations.

**Output:** Primary recommendation (best match) + Secondary (alternative in same category) + Used Alternative (when applicable) + Riders Share rental CTA.

## "Buy Used" Recommendation Path

The quiz includes a dedicated used-bike recommendation path because the motorcycle community overwhelmingly agrees: buying used for your first (and often second) bike is the smart move.

### When the Used Path Triggers

- Budget under $5,000 at any experience level
- Beginner rider with budget under $8,000 (strong suggestion)
- Any user selecting "simplicity and reliability" as their top priority (Q14:F)
- Optionally surfaces as a secondary recommendation alongside every new-bike result

### Why It Exists

The used path exists because it reflects how experienced riders actually advise new riders. The quiz reinforces messaging that aligns with community wisdom: you will likely drop your first bike (used means a $50 scratch, not $5,000 heartbreak), you will outgrow your first bike (less investment now means a smarter upgrade later), and most beginner bikes change minimally between model years (same bike, thousands less).

### Budget-to-Category Mapping

When the used path activates, the engine maps the user's budget to the best available model in their preferred category across 6 tiers: Under $3K, $3K-$5K, $5K-$7K, $7K-$10K, $10K-$15K, and $15K+. Every tier has curated picks for all 5 categories.

## Audit Fixes Applied

Before development, the V3 model database was audited bike-by-bike to verify that every model had a viable quiz routing path. The audit identified 6 required fixes, all of which have been applied:

**1. Triumph Bonneville T120: Moved from Cruiser Used to Standard/Naked Used.**
The T120 has an upright riding position, not a feet-forward cruiser stance. Replaced in the Cruiser category with a comparable model.

**2. Kawasaki Ninja 1000/1000SX: Moved from Sport Used to Touring/Sport-Touring Used.**
Kawasaki classifies this model under their sport-touring segment. It features pannier mounts and touring capability that align with the Touring category's quiz paths.

**3. Honda VFR800: Moved from Sport Used to Touring/Sport-Touring Used.**
The VFR800 is a V4 sport-tourer with shaft drive (later models) and VTEC, designed for distance riding rather than pure sport riding.

**4. Honda NC700X/NC750X: Duplicate removed.**
Previously appeared in both Standard/Naked Used and Adventure Used. Consolidated to Standard/Naked only (road-biased platform with 17" wheels). Crossover note added in Adventure section for users who might benefit from it.

**5. Suzuki Burgman 650: Removed from Touring Used.**
The Burgman is a maxi-scooter, not a motorcycle. No quiz question addresses scooter/automatic/CVT preference, and a motorcycle recommendation quiz should recommend motorcycles.

**6. Cruiser-Tourer Crossover Logic: Added.**
For hybrid models like the Honda CTX1300 and Kawasaki Vulcan 1700 Voyager, the engine now surfaces these when a Cruiser rider selects long-distance riding (Q6:D-E) OR a Touring rider selects a feet-forward position (Q10:A).

## Riders Share Rental CTA Integration

Every quiz result includes a "Rent this model on Riders Share before you buy" prompt. This is especially valuable for used-bike recommendations, where the buyer can confirm the model is the right fit before committing. Riders Share's peer-to-peer fleet frequently includes the exact models the quiz recommends.

**Funnel:** Quiz Result > Rent on Riders Share > Buy with Confidence

## Tech Stack

> **Note:** Tech stack is not yet finalized. The quiz will be built as a standalone web application suitable for iframe embedding. The architecture below is a placeholder and will be updated once the stack decision is made.

**Possible approaches:**

- **React / Next.js** -- Component-based UI with state management for quiz flow and scoring
- **Vanilla JS + HTML/CSS** -- Lightweight, zero-dependency approach for fast load times and simple embedding

**Shared requirements regardless of stack:**

- Responsive design (mobile-first; most motorcycle shoppers browse on phones)
- JSON-based model database (easy to update without code changes)
- Client-side scoring engine (no backend required)
- Accessible (WCAG 2.1 AA minimum)
- Fast initial load (quiz is embedded via iframe on blog pages)
- Analytics-ready (track completion rates, most common results, drop-off points)

## Iframe Embedding

> **Placeholder:** Embedding instructions will be added once the app is deployed.

The quiz will be hosted on GitHub Pages (or equivalent static hosting) and embedded on the Riders Share blog via iframe. Embedding documentation will include the iframe snippet, recommended dimensions, responsive scaling instructions, and any required cross-origin considerations.

```html
<!-- Placeholder - update URL after deployment -->
<iframe
  src="https://[TBD]/motorcycle-quiz/"
  width="100%"
  height="800"
  frameborder="0"
  title="What Motorcycle Should I Buy? Quiz by Riders Share"
></iframe>
```

## Project Structure

```
motorcycle-quiz/
  README.md
  LICENSE
  .gitignore
  /src           # Application source (structure TBD based on stack)
  /data          # Model database JSON files
  /assets        # Images, icons, Riders Share branding
  /docs          # Quiz content documents and audit trail
```

## Credits

Quiz data, content strategy, and recommendation engine design by [RiZen Metrics](https://rizenmetrics.com) for [Riders Share](https://www.riders-share.com).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
