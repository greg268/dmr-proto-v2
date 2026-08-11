# Daily Market Report — Prototype v2

Static HTML/CSS/JS prototype for user testing the redesigned Daily Market Report, the news lists behind it, and the individual stock articles. No build step — open any file directly, or serve the folder as-is.

**Live:** https://greg268.github.io/dmr-proto-v2/

## What v2 changes

v1 presented the day as a 28-row table of announcements. v2 replaces that with **twelve curated items** — beats, misses, large price moves and stocks widely held by members — selected algorithmically with analyst override, and presented as editorial rather than tabular data.

Nothing is dropped: the full list still exists on the news page, where every announcement carries a plain-English summary. The report links to it, and it links back.

## Pages

**Send testers to `index.html`.** Everything else is reachable from it.

| File | What it is |
| --- | --- |
| `index.html` | The Daily Market Report. Twelve items under "The stories that matter", with a state selector top-right (see below). |
| `news.html` | Today's news — all 58 announcements, in two tabs: **My portfolio news** (11) and **All news** (58). Reached from the two cards at the foot of the report, or directly with `?tab=folio` / `?tab=market`. |
| `previous-reports.html` | Archive listing. |
| `ao.html` `bbsn.html` `cgs.html` `gaw.html` `hsp.html` `like.html` `pzc.html` `snws.html` | The eight individual stock articles — one per item that carries an analyst view. Reached via **View analysis**. |
| `test-links.html` | Facilitator-only index of every page. **Don't send this to testers.** Note: it does not currently list `news.html`. |
| `img/` | Analyst photographs and the screenshots used inside the articles. Paths are relative and nested — keep the folder structure intact. |

## The three states

`index.html` carries a state selector in the top right. It exists so one page can be tested at three points in the day, and it is **prototype scaffolding — not a real feature**. Hide or ignore it when framing a session.

| State | What a reader sees |
| --- | --- |
| **08:30 — before any analysis** | All twelve items with summaries, prices and earnings verdicts, but **no analyst notes**. A red live line states that notes are added through the day. |
| **12:30 — analysis coming in** | Six notes published, two still to come. A "what's new since your last visit" bar appears with jump links. |
| **17:05 — complete** | All eight notes in; four items remain summary-only by choice. The live badge and the live line disappear. |

**The open research question** is whether 08:30 is worth opening at all, given it contains no analyst judgement — or whether it is just the news list with fewer items. Ask that directly.

## Interaction worth knowing before you facilitate

Each item on the agenda has **three** targets, and which one a participant reaches for is itself a finding:

- **The headline** opens the full RNS in a bottom sheet. It works on all twelve items in every state. It has no underline at rest, so watch whether people discover it.
- **The ticker chip** (e.g. `PZC`) in the metadata row goes to the StockReport. Hovering it previews that page.
- **View analysis** opens the atomic article. Only present where an analyst note exists, so absent entirely at 08:30.

On `news.html`, filters live behind **News types** (a modal side sheet) plus three chips — Beats, Misses, Analyst picks. Beats and Misses combine as OR; Analyst picks narrows whatever is showing.

## Data

All content is placeholder for testing — **nothing here reflects real Stockopedia data**, and prices, comments and holdings are invented.

Two figures are worth knowing because participants may check them:

- 58 announcements, of which 12 are on the agenda and **8 carry an analyst view**. Coverage is deliberately limited to the eight items that have an article behind them.
- 11 announcements sit in the reader's portfolios.

Both pages hold their own copy of the twelve agenda rows. They agree today, but **editing one will not update the other** — reconcile by hand, or extract a shared data file before the next round.

## Conventions

Lato for text, **Material Symbols Outlined** for all icons — never a hand-drawn path. Around 25 inherited stroke-based SVG icons are still awaiting conversion; the news page's own icons are converted and can be used as the reference.

## Known gaps

- `test-links.html` doesn't list `news.html`.
- If Material Symbols fails to load, ligature names render as text — the folder marker beside a company name would read "PZ Cussonsfolder". Relevant on locked-down networks.
- The agenda's four uncovered items use hand-written headlines; in production these need generating.
