# X Viral Intelligence — SF-Tech Writing Research

**Reproducible data science and growth research portfolio** · October 2026

**Question:** Which features of high-reach SF-tech posts are reusable writing techniques, and which depend on an exceptional news event, product launch, or author audience?

## Headline findings

- **150/160** selected X posts retrieved through an official, one-time API lookup; **65** manually relevance-reviewed.
- **26** reviewed posts had no optional context-dependence note; **39** had notes. These are *candidate groups*, **not validated causal labels**.
- **128** distinct author IDs; within-author comparisons are limited by a selectively collected sample.
- A simple text-feature Ridge model improved mean held-out MAE by just **1.2%** over a constant-median baseline across five author-grouped splits. **Too small and unstable to support a useful predictive claim** (the model lost in three splits and won in two).
- Career-relevant audience reach, follower demographics, referrals, and interviews **were not observed**. Likes and views must not be represented as job outcomes.

**[Read the case study](reports/case-study.md)** · **[Structured results](reports/results.json)** · **[Publishing drafts](docs/publishing-drafts.md)**

## Reproduce locally

```bash
python -m pip install -r requirements.txt
python scripts/build_portfolio.py
python -m unittest discover -s tests -v
```

No API credentials, scheduled actions, paid API calls, or cloud services are needed.

## Research design

1. Use existing API retrieval records, reviewer labels, and author-aware summary.
2. Keep human notes distinct from machine inferences.
3. Compare descriptive groups without claiming causality.
4. Fit a deliberately simple text-only regression for engagement per 1,000 views, evaluated with **author-grouped splits** against a training-median baseline.
5. Publish limitations and negative/inconclusive findings alongside results.

## Limitations and responsible use

The sample was assembled through historical discovery, **not random sampling**; it overrepresents interesting/viral posts. Some text may be truncated; metrics were collected at different post ages; media and follower demographics are missing. The baseline predicts a proxy for engagement among *selected* posts, not virality, career outcomes, or optimal posting time. Splits are author-grouped but not chronological; temporal generalization remains untested.

**Publication caution:** Raw data includes third-party post text. For a public repository, publish the analysis, aggregated results, and links, but **do not commit the `data/` folder or `reports/analyzed-posts.csv` without checking redistribution rights**. The source bundle is for your private repo; see `docs/PUBLICATION.md`.

## Skills demonstrated

Data acquisition and validation · data cleaning · human-in-the-loop annotation · author-aware comparisons · leakage-aware ML evaluation · research communication · growth experimentation design.
