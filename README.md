# Weekly Commercial Brief Co-Build

A follow-along guide for a 50-minute co-build in Lyzr Agent Studio. Participants build a manager agent and three specialist agents. Together they turn a week of retail sales data into a commercial brief, with margin guardrails and a named human approver on every action.

**Open the guide:** `https://<your-username>.github.io/commercial-brief-cobuild/`

## What gets built

| Agent | Job | Data access |
| --- | --- | --- |
| Sensing Agent | Finds the four biggest week-on-week movements, ranked by contribution | Weekly Sales semantic model |
| Diagnosis Agent | Explains each movement with a cause, evidence and a confidence level | Semantic model and Category Context knowledge base |
| Pricing & Guardrail Agent | Proposes options, blocks anything that breaks a margin or stock rule, names an approver | Category Context knowledge base |
| Commercial Brief Manager | Runs the three agents in order and writes the brief | Sub-agents only |

The loop: **sense → diagnose → propose → guardrail check → human approves**. Agents propose and people decide. Nothing is executed.

## What's in this repo

```
index.html                     The follow-along guide
files/weekly_sales_sdm.csv     Sample sales data for the semantic model
files/category_context.txt     Market, channel and SKU notes, guardrails G1–G5 and approvers for the knowledge base
files/cobuild-files.zip        Both data files in one download
```

## The sample data

4 SKUs × 4 UAE channels (Talabat Mart, Noon Minutes, Careem Quik, Carrefour UAE) × 2 weeks. Everything moves by less than 2% week on week, except four planted stories:

| Story | Tempting move | What the agents should do |
| --- | --- | --- |
| A 25% promo lifts sales 21.5% but cuts contribution 39% | Extend the promo | Block it (margin floor), end the promo |
| A competitor cuts price on a core SKU | Match the price | Block it (margin falls to 21.7% vs a 32% floor), hold |
| A SKU drops to 58% in-stock | Buy paid visibility | Block it (stock before spend), fix supply |
| A SKU grows with nothing changed | Buy paid visibility | Investigate first |

All data, brand details, guardrails and approvers are illustrative.

## Running the session

1. Download the two data files from the guide's Setup section.
2. Create the semantic model and knowledge base in Agent Studio (about 5 minutes).
3. Build each agent from the copy-ready Name, Description, Role, Goal and Instructions fields.
4. Run that agent's tests (they're under each agent in the guide) before moving on.
5. Run the full brief through the manager.

The guide also includes a Troubleshooting section with fixes for the issues found in rehearsal.

## Publishing with GitHub Pages

1. Push these files to the root of the repo's default branch.
2. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, and choose the default branch and `/ (root)`.
3. The `.nojekyll` file stops GitHub's Jekyll processing so the files are served as they are.
