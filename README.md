# AnswerIndex Data — AI Crawler & llms.txt Adoption Index

Open datasets from [AnswerIndex](https://answerindex.org), an independent measurement publication that publishes original data on how the web treats AI crawlers. Every number here comes from a crawl AnswerIndex ran itself; the full per-domain data is published so anyone can check the arithmetic or reuse the figures.

**Cite as:** AnswerIndex, *AI Crawler & llms.txt Adoption Index*, November 2026. https://answerindex.org/reports/2026-11-ai-crawler-index/

Free to use with attribution to AnswerIndex.

## November 25, 2026 edition

Measured **November 25, 2026** over the **Tranco top 10,000** websites — the second monthly census, six days after the first edition (same domain list, same counting rules, so the changes below are exact).

Files:

| File | Contents |
|---|---|
| `results-2026-11-25.csv` | Per-domain results for all 10,000 measured sites (see columns below) |
| `summary-2026-11-25.md` | The measurement summary: fetch success, per-agent blocked/allowed counts, llms.txt adoption, the June 2026 comparison, and method caveats |

### Headline findings

- **llms.txt adoption:** 1,129 of the top 10,000 sites (11.29%) publish `llms.txt`; 219 (2.19%) publish `llms-full.txt`; 219 publish both, 1,129 publish at least one. Six days on: +6 llms.txt, −3 llms-full.txt vs November 19.
- **AI crawler blocking:** of the 10,000 domains, 6,368 returned a robots.txt (63.7%), 715 refused it with HTTP 401/403 (7.2%, treated as fully disallowed) and 2,917 had no determinable policy (29.2%). Blocked shares below are of the **7,083** sites with a determinable policy.
- **Training vs. search:** every training / data-collection crawler is blocked by 22.9–26.1% of determinable sites; every search / user-fetch agent by 18.9% or less. Blocking inched up 0.2–0.4 points on every agent since November 19.
- **What changed in six days:** 21 sites newly block every training crawler — in every case the robots.txt file itself is unchanged; the sites started refusing requests (HTTP 403) or became unreachable. 6 sites moved the other way. 28 sites newly publish llms.txt; 22 stopped (9 true removals, 13 unreachable).

| User-agent | Blocked | Blocked % | Allowed |
|---|---|---|---|
| CCBot | 1,849 | 26.1% | 5,234 |
| Bytespider | 1,846 | 26.1% | 5,237 |
| GPTBot | 1,782 | 25.2% | 5,301 |
| ClaudeBot | 1,734 | 24.5% | 5,349 |
| Meta-ExternalAgent | 1,660 | 23.4% | 5,423 |
| Google-Extended | 1,628 | 23.0% | 5,455 |
| Amazonbot | 1,625 | 22.9% | 5,458 |
| Applebot-Extended | 1,623 | 22.9% | 5,460 |
| PerplexityBot | 1,338 | 18.9% | 5,745 |
| ChatGPT-User | 1,264 | 17.8% | 5,819 |
| Perplexity-User | 1,196 | 16.9% | 5,887 |
| Claude-User | 1,173 | 16.6% | 5,910 |
| Claude-SearchBot | 1,151 | 16.3% | 5,932 |
| OAI-SearchBot | 1,144 | 16.2% | 5,939 |

### Method note (this edition)

The first crawl pass returned fewer reachable sites than the November 19 baseline, so all 1,615 domains whose verdict changed were re-measured from the original egress with a low-concurrency second pass. The published figures are the repaired counts; see `summary-2026-11-25.md` and the report methodology section for detail.

Full report with charts and methodology: https://answerindex.org/reports/2026-11-25-ai-crawler-index/

## November 2026 edition

Measured **November 19, 2026** over the **Tranco top 10,000** websites.

Files:

| File | Contents |
|---|---|
| `results-2026-11-19.csv` | Per-domain results for all 10,000 measured sites (see columns below) |
| `summary.md` | The measurement summary: fetch success, per-agent blocked/allowed counts, llms.txt adoption, the June 2026 comparison, and method caveats |

### Headline findings

- **llms.txt adoption:** 1,123 of the top 10,000 sites (11.23%) publish `llms.txt`; 222 (2.22%) publish `llms-full.txt`; 219 publish both, 1,126 publish at least one. In Rankability's June 2026 measurement of the same tier the counts were 556 / 112 / 558 — roughly a doubling in five months (directional: the Tranco list changes daily, so the samples are not identical domain sets).
- **AI crawler blocking:** of the 10,000 domains, 6,397 returned a robots.txt (64.0%), 694 refused it with HTTP 401/403 (6.9%, treated as fully disallowed) and 2,909 had no determinable policy (29.1%). Blocked shares below are of the **7,091** sites with a determinable policy.
- **Training vs. search:** every training / data-collection crawler is blocked by 22.6–25.8% of determinable sites; every search / user-fetch agent by 18.6% or less. The web is not blocking AI — it is blocking training.

| User-agent | Blocked | Blocked % | Allowed |
|---|---|---|---|
| CCBot | 1,828 | 25.8% | 5,263 |
| Bytespider | 1,821 | 25.7% | 5,270 |
| GPTBot | 1,764 | 24.9% | 5,327 |
| ClaudeBot | 1,711 | 24.1% | 5,380 |
| Meta-ExternalAgent | 1,637 | 23.1% | 5,454 |
| Google-Extended | 1,611 | 22.7% | 5,480 |
| Amazonbot | 1,602 | 22.6% | 5,489 |
| Applebot-Extended | 1,601 | 22.6% | 5,490 |
| PerplexityBot | 1,321 | 18.6% | 5,770 |
| ChatGPT-User | 1,245 | 17.6% | 5,846 |
| Perplexity-User | 1,175 | 16.6% | 5,916 |
| Claude-User | 1,150 | 16.2% | 5,941 |
| Claude-SearchBot | 1,131 | 15.9% | 5,960 |
| OAI-SearchBot | 1,127 | 15.9% | 5,964 |

### CSV columns

| Column | Meaning |
|---|---|
| `domain` | Measured domain |
| `rank` | Rank in the Tranco list (snapshot downloaded 2026-11-19) |
| `robots_status` | `ok` (robots.txt retrieved), `restricted` (HTTP 401/403 — treated as fully disallowed), `no_robots` (missing/unreachable) |
| one column per agent (`GPTBot`, `OAI-SearchBot`, `ChatGPT-User`, `ClaudeBot`, `Claude-SearchBot`, `Claude-User`, `PerplexityBot`, `Perplexity-User`, `Google-Extended`, `CCBot`, `Bytespider`, `Meta-ExternalAgent`, `Amazonbot`, `Applebot-Extended`) | `allowed` / `blocked` verdict for that user-agent; `no_robots` when no policy could be determined |
| `llms_txt` | 1 if `/llms.txt` returned HTTP 200 with a non-HTML body, else 0 |
| `llms_full_txt` | Same for `/llms-full.txt` |

### Method in brief

Each domain was probed for `/robots.txt`, `/llms.txt` and `/llms-full.txt` (redirects followed; an HTML body counts as a soft-404, i.e. absent). Robots.txt verdicts use RFC 9309 group selection: an agent-specific group beats the `*` group, the longest matching rule for `/` wins, and Allow wins ties. A robots.txt refused with HTTP 401/403 counts as fully disallowed for every agent; other failures count as no determinable policy.

### Caveats

- 2,168 domains produced no HTTP response at all for robots.txt; for those, the llms probes were skipped and counted as absent. Reachability was measured from the crawler's network egress, which drops some connections under parallel load, so the unreachable share is an **upper bound** and llms.txt adoption a slight **undercount**.
- The June 2026 comparison is directional, not exact (different daily Tranco snapshots; counting rules may differ slightly).
- One snapshot in time: robots.txt and llms.txt files change without notice.

Full report with charts and methodology: https://answerindex.org/reports/2026-11-ai-crawler-index/
Per-agent pages: https://answerindex.org/crawlers/

The index is a monthly series. Next edition: December 2026.
