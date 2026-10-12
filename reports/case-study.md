# X Viral Intelligence: What Makes SF-Tech Posts Travel?

**Portfolio research case study · October 2026**

## Executive summary

We retrieved **150 of 160** selected historical X posts using the official API. **65** were manually classified for topical relevance. Of these, **26** had no optional context-dependence note and are *candidates* for reusable writing analysis; **39** carried notes, often about news, launches, or specific events. Blank notes do **not** establish that writing caused success.

**Key insight:** viral reach and reusable writing are different research targets. A product launch can travel because the event is noteworthy; a question, comparison, or joke may offer a transferable writing technique. Our dataset cannot causally separate these effects.

## Dataset and limitations

- **150** retrieved posts, **10** unavailable; **128** distinct author IDs.
- **85** posts have no human relevance review.
- **68** post texts contain at least 275 characters and are flagged as potentially incomplete, not confirmed truncated.
- Posts were selected from discovery sources; they are **not a random sample of X** and include many unusually successful accounts.
- No verified follower demographics, qualified professional interactions, referrals, interviews, or hiring outcomes were supplied.
- Engagement totals were captured at different post ages. Media, follower count, and algorithmic distribution are unobserved.

## Human-labeled comparison (descriptive only)

| Group | Posts | Median positive view count |
|---|---:|---:|
| Unannotated writing candidates | 26 | 552,917 |
| Context-noted posts | 39 | 431,053 |

This is **not a causal comparison**: the groups were formed by a reviewer's optional notes, not random assignment.

## Author-aware examples

Same-author comparisons use the median of *other retrieved posts from that author*, not the author's complete timeline. They are highly selected and should be treated as exploratory.

- [https://x.com/i/status/2040470801506541998](https://x.com/i/status/2040470801506541998): **2.80×** the sampled same-author median; 7,328,278 views.
- [https://x.com/i/status/1827143768459637073](https://x.com/i/status/1827143768459637073): **0.87×** the sampled same-author median; 2,831,988 views.
- [https://x.com/i/status/1937902205765607626](https://x.com/i/status/1937902205765607626): **0.69×** the sampled same-author median; 2,402,042 views.
- [https://x.com/i/status/1976077806443569355](https://x.com/i/status/1976077806443569355): **0.21×** the sampled same-author median; 716,543 views.
- [https://x.com/i/status/1976082963382272334](https://x.com/i/status/1976082963382272334): **0.11×** the sampled same-author median; 397,000 views.

## Baseline model: deliberately modest

We test whether surface-level text features can predict **log engagement per 1,000 views**. The comparison is a training-set median baseline versus a standardized, regularized Ridge model. Five repeatable author-grouped train/test splits prevent the same author from appearing in both sides of any split. This is a *diagnostic exercise*, not a deployable virality predictor.

- Eligible posts: **135**; authors: **114**.
- Baseline mean held-out MAE: **0.5680**.
- Ridge mean held-out MAE: **0.5610**.
- Ridge change versus baseline: **+1.2%** (positive means improvement).

The text-feature model improves this proxy in these splits, but this does **not** validate career-outcome prediction.

## What we can responsibly conclude

1. Context-dependent news and launches should be analyzed separately from transferable writing patterns.
2. Absolute view counts alone can be misleading because of author audience differences.
3. Our observed engagement proxy is **not** a measure of professional reach or job opportunities.
4. The project demonstrates data ingestion, human-in-the-loop labeling, selection-bias awareness, reproducible evaluation, and honest reporting of uncertainty.

## Practical career strategy

Publish a short thread explaining the selection-bias finding, show the reproducible GitHub repository, and invite growth, data, and AI practitioners to challenge the methodology. Track qualified conversations and referrals separately from views. Do not claim a proven virality formula.

## Reproduce

Install `numpy` and `scikit-learn` using `requirements.txt`, then run `python scripts/build_portfolio.py` from the repository root. All inputs are bundled in `data/`; the script makes no network calls and writes `reports/results.json`, `reports/analyzed-posts.csv`, and `reports/case-study.md`.
