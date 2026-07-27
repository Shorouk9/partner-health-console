# Partner Health Console

**Live prototype → https://shorouk9.github.io/partner-health-console/**

An AI-assisted account health and next-best-action console for restaurant partnerships in the UAE food-delivery market. Built as an application exercise.

> All partner names, figures and call notes are **invented**. No confidential, proprietary or real customer data is used anywhere in this project.

---

## What it does

Eighteen synthetic restaurant partners across Dubai, Abu Dhabi, Sharjah, Al Ain and Ras Al Khaimah. For each one it produces:

- a **health score out of 100**, with every component shown separately
- a **modelled churn risk**
- **one** recommended action — retention, upsell or growth — with the AED at stake
- a **draft outreach message** referencing a real number from the account

And across the book: a portfolio brief, a five-item priority queue, and the cross-cutting patterns that belong to Ops or Marketing rather than to any individual Account Manager.

## Two layers, deliberately separated

**Layer 1 — deterministic scoring.** The score is calculated in code, not by a language model. The same data always produces the same score, the maths is auditable, and an Account Manager can see exactly which component cost them points.

| Component | Weight |
|---|---|
| Order-volume trend (last 4 wks vs prior 4) | 25 |
| Operational reliability (cancellations, prep SLA) | 20 |
| Customer rating and its direction | 15 |
| Basket-size trend | 10 |
| Menu freshness | 10 |
| Marketing participation | 10 |
| Relationship recency | 10 |

**Layer 2 — the language model.** It does only the three things it is genuinely better at: reading unstructured call notes, explaining the score in commercial language, and drafting the outreach. Both prompts are in the **Prompt Library** tab.

## Design decisions

- **One action per partner, per week.** A dashboard that surfaces nine opportunities produces zero.
- **Ranked by value at stake, not lowest score.** Sorting by health sends a team to chase its smallest, most-lost accounts first.
- **The model must be able to say "no action needed".** A tool that always finds something to do gets ignored within a month.
- **Seasonality is named explicitly.** Ramadan, Eid, DSF and the summer exodus move UAE food volumes enough to fake a churn signal.
- **Missing data stays missing.** The denominator shrinks rather than the model imputing a number.

## Running it

One self-contained `index.html`. No build, no dependencies, no tracking — open the file or the link above.

## What this is not

A 60-minute prototype on synthetic data. A real build would need a churn model validated against actual historical churn rather than a hand-weighted rubric, back-testing across at least four quarters, an honest false-positive rate, and a feedback loop capturing which recommendations Account Managers acted on and which they ignored — that last one being the only thing that makes the weights better over time.
