# GEO measurement — Tranco top 10,000 domains

Crawl date: 2026-11-19 (main pass 08:47-11:21 UTC, two segments; crawler process was killed by a service restart at rank 5,000 and resumed from the batch checkpoint) (robots.txt + llms.txt measurement; method in crawl.py).

## Fetch success

- Domains measured: 10,000
- robots.txt retrieved (HTTP 200): 6,397 (64.0%)
- robots.txt refused (HTTP 401/403, treated as fully disallowed): 694 (6.9%)
- robots.txt missing/unreachable (no_robots): 2,909 (29.1%)

## AI crawler access in robots.txt

Blocked % is of the 7,091 sites with a determinable robots policy (robots.txt retrieved or 401/403).

| User-agent | Blocked | Blocked % | Allowed |
|---|---|---|---|
| GPTBot | 1,764 | 24.9% | 5,327 |
| OAI-SearchBot | 1,127 | 15.9% | 5,964 |
| ChatGPT-User | 1,245 | 17.6% | 5,846 |
| ClaudeBot | 1,711 | 24.1% | 5,380 |
| Claude-SearchBot | 1,131 | 15.9% | 5,960 |
| Claude-User | 1,150 | 16.2% | 5,941 |
| PerplexityBot | 1,321 | 18.6% | 5,770 |
| Perplexity-User | 1,175 | 16.6% | 5,916 |
| Google-Extended | 1,611 | 22.7% | 5,480 |
| CCBot | 1,828 | 25.8% | 5,263 |
| Bytespider | 1,821 | 25.7% | 5,270 |
| Meta-ExternalAgent | 1,637 | 23.1% | 5,454 |
| Amazonbot | 1,602 | 22.6% | 5,489 |
| Applebot-Extended | 1,601 | 22.6% | 5,490 |

## llms.txt adoption

- /llms.txt present (HTTP 200, non-HTML body): 1,123 (11.23% of 10,000)
- /llms-full.txt present: 222 (2.22%)
- Both files: 219
- Either file: 1,126

## Comparison with June 2026 Rankability study (Tranco top 10k)

Rankability (data as of June 2026, cited via aiscan.site) found 558 sites with either file: 556 with llms.txt and 112 with llms-full.txt (implying ~110 with both).

- llms.txt: 1,123 now vs 556 then (+567, up)
- llms-full.txt: 222 now vs 112 then (+110, up)
- Either file: 1,126 now vs 558 then (+568, up)

Caveats: the Tranco list itself changes daily, so the two samples are not identical domain sets; counting rules may also differ slightly (this crawl follows redirects and rejects HTML soft-404 bodies). Treat the comparison as directional, not exact.

## Method caveats

- robots verdicts use RFC 9309 group selection (agent-specific group beats "*"; longest matching rule for "/" wins; Allow wins ties).
- HTTP 401/403 on robots.txt is counted as fully disallowed (robots_status=restricted); other non-200s and transport failures are no_robots.
- llms bodies were capped (2 MB / 5 MB) during download; presence only needs the status code and the first bytes, so the cap does not affect the count except for pathological cases.
- One snapshot in time; robots.txt and llms.txt files change without notice.
- 2,168 domains produced no HTTP response at all for robots.txt on either scheme (transport-dead: DNS/connect failure or a hanging server). For those, the two llms probes were skipped and counted as absent — a host that cannot answer robots.txt cannot serve llms.txt either, short of pathological path-specific filtering.
- Reachability is measured from this crawler's network egress, which drops some connections under parallel load: a low-concurrency second-chance pass over the transport-dead set recovered 707 domains that then answered normally. A residual share of the no_robots set is therefore likely to be egress-related false negatives rather than genuinely dead sites; treat the unreachable share as an upper bound.
