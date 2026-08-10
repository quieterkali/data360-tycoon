# Data 360 Tycoon

An interactive, low-poly simulation of **Salesforce Data 360** (formerly Data Cloud).

**▶ [Play it](https://quieterkali.github.io/data360-tycoon/)** · **📖 [Companion primer](https://quieterkali.github.io/data360-tycoon/primer.html)**

Follow three convoys of customer records from their source depots, through ingestion,
harmonization and identity resolution, out to activation — watching the data physically
change shape at every stop, and watching the bill grow.

---

## Why a simulation and not a document

Built following [Laurentiu Gabriel's method for learning complex topics with LLMs](https://laurentiugabriel.github.io/blog/articles/how-i-use-llms-to-learn/):

1. Build the foundational knowledge base for the topic.
2. **Review the accuracy of that knowledge base.**
3. Turn it into a low-poly, RollerCoaster Tycoon-style simulation.
4. Publish it.

Step 2 is the one that matters. Before this simulation was built, the accuracy pass caught
four real errors in the knowledge base behind it — including a constraint that had been
stated as a hard rule and was simply wrong. A simulation makes facts stick; it makes
*wrong* facts stick just as well. The corrections are documented in the primer.

## The route

| # | Stop | District | What it teaches |
|---|---|---|---|
| 1 | Source Depots | Sources | Three systems, three schemas, same people |
| 2 | Data Stream | Sources | DSO; streaming costs more than batch |
| 3 | DLO Yard | Ingest & Lake | Raw storage, faithful to the source |
| 4 | Transform Works | Ingest & Lake | Cheapest place to drop dead weight |
| 5 | Mapping Hall | Modeling | DMO; 89 standard objects; the core design work |
| 6 | Category Gate | Modeling | Profile / Engagement / Other, and what each unlocks |
| 7 | Match Plaza | Identity | Exact, fuzzy, normalized — AND within a rule, OR across rules |
| 8 | Reconciliation Tower | Identity | Which value wins; the highest multiplier on the platform |
| 9 | Unified Individual | Identity | **Sources are linked, never deleted** |
| 10 | Insights Foundry | Consumption | Billed on every refresh |
| 11 | Segment Yard | Consumption | Rows *processed*, not rows returned |
| 12 | Data Graph Depot | Consumption | Pre-computed, no joins at read time |
| 13 | Vector Wing | Consumption | Keyword + vector + hybrid indexes, one ensemble query |
| 14 | Query API Dock | Consumption | SQL over DMOs, no ETL |
| 15 | Activation Gates | Activation | The only stop that produces value |

## Two instruments

- **Credit meter** — runs the documented formula `credits = (d ÷ u) × m` live at every stop,
  where `u` is 1 million for every usage type. Watch it spike at profile unification.
- **Ingest ⟷ Zero-Copy toggle** — flip it and the warehouse convoy stops physically
  travelling. A federated query beam fires instead and the meter recomputes.

## Challenges

Every one of the 15 stops has a challenge, and the HUD keeps score. Three kinds:

| Kind | What it asks |
|---|---|
| **Checkpoint** | An applied decision — batch or streaming, where to filter, which tool for a 100ms read |
| **Sequence** | Click stages in the order they actually happen |
| **Do the maths** | Work `credits = (d ÷ u) × m` by hand and type the answer |

Seven of them are **recall** challenges, tagged with the earlier stop they reach back to —
answering about a *previous* step is what makes it stick, which is the whole reason the method
recommends them. Two of them chain: the Insights Foundry has you compute 90 credits for one
run, then the Segment Yard asks what the same insight costs refreshed hourly. Arriving at
2,160 yourself lands harder than reading that refresh frequency matters.

## Controls

| Key | Action |
|---|---|
| `Space` | Play / pause |
| `S` | Next stop |
| `R` | Restart |
| `F` | Toggle follow camera |
| `L` | Toggle signs |

Drag to pan, scroll to zoom, double-click for an overview, click any building to read it.

## ⚠️ On the numbers

**The credit multipliers in the simulation are illustrative, not real rates.**

Salesforce publishes actual multipliers only in its rate card, and Trailhead's own `m=15`
example is explicitly labelled illustrative. The rates also move between releases. What *is*
documented, and what the simulation teaches faithfully:

- the formula `credits = (d ÷ u) × m`, with `u` = 1 million for every usage type
- the six billable categories: Connect · Harmonize & Unify · Analyze & Predict · Act ·
  Segment & Activate · Real-Time Processing
- profile unification carries the **highest** multiplier of any usage type
- streaming consumes more credits than batch for equivalent work

Pull the current rate card before putting a number in front of a customer.

## Built with

Vanilla JavaScript and a 2D canvas. No build step, no dependencies, no network calls —
a single self-contained HTML file.

## Sources

[Data 360 Architecture](https://architect.salesforce.com/fundamentals/data-360-architecture) ·
[DMO & Mapping guide](https://developer.salesforce.com/docs/data/data-cloud-dmo-mapping/guide/c360dm-model-data.html) ·
[Identity Resolution Rulesets](https://help.salesforce.com/s/articleView?language=en_US&id=data.c360_a_identity_resolution_ruleset.htm&type=5) ·
[Credit consumption](https://trailhead.salesforce.com/content/learn/modules/data-cloud-credit-consumption-quick-look/get-started-with-data-cloud-credit-consumption) ·
[Zero Copy](https://www.salesforce.com/data/connectivity/zero-copy/)
