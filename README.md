# Website Channel Performance Analysis

An exploration of hourly GA4 traffic data to figure out which channels actually drive value for the site, not just which ones show up the most in the numbers.

## About the data

The dataset is a Google Analytics 4 export covering April 6 to May 3, 2024, broken down by hour and channel (3,182 rows total). Channels present: Direct, Organic Social, Organic Search, Referral, Email, Organic Video, and Unassigned.

## What I was trying to find out

- What do sessions and users look like over the course of the month?
- Which channel brings in the most users, and what does that suggest about where to invest?
- Which channel holds attention longest, and what might explain that?
- How much does engagement rate swing between channels?
- Which channels convert visits into engaged sessions, and where is engagement lagging?
- Are there specific hours where certain channels spike?
- Does more traffic in a given period line up with better engagement, or do they move independently?

## Findings

Organic Social brings in the most sessions by a wide margin (60,627, about 38% of total traffic), but it's not the strongest performer on engagement — its rate sits at 53.9% and its session-weighted average engagement time (52 seconds) is the lowest among the high-volume channels.

Referral traffic tells a different story. It pulls in half the sessions of Organic Social, but converts to engagement at 66.6% and holds attention almost twice as long, around 94 seconds on average.

Organic Video stands out the most on a per-session basis — 77.3% engagement rate and roughly 180 seconds of average engagement time — but with only 141 sessions over the whole period, it's too small a sample to draw firm conclusions from. Worth watching, not worth scaling yet.

Unassigned traffic is close to noise: 0.7% engagement rate. That's more likely a tracking or attribution gap than a real audience segment, and probably worth a separate look outside this analysis.

All engagement-time figures here are weighted by session count rather than averaged straight across hourly buckets — a flat average would give equal weight to a slow hour with a handful of sessions and a busy one with hundreds, which distorts the comparison.

## What's in the notebook

1. Sessions and users over time
2. Total sessions by channel
3. Session-weighted average engagement time by channel
4. Engagement rate distribution by channel
5. Engaged vs. non-engaged sessions by channel
6. Traffic by hour of day and channel
7. Engagement rate against session volume over time

## Built with

pandas, numpy, matplotlib, seaborn

## Files

```
website-analysis/
├── Website_Analysis.ipynb
├── data-export.csv
├── requirements.txt
└── README.md
```

## Running it locally

```bash
pip install -r requirements.txt
jupyter notebook Website_Analysis.ipynb
```

## A couple of caveats

GA4's Users metric isn't additive — the same visitor can be counted in multiple hourly buckets, so any total built by summing Users across time or channel is an approximation, not a deduplicated count. Sessions don't have this problem and can be summed safely.

This uses GA4's default channel grouping rather than a custom attribution model, so there's no campaign- or source-level detail beneath each channel.
