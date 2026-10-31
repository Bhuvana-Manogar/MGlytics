# YouTube Channel Analytics: Power BI Dashboard

A three-page Power BI report that analyses every video on a YouTube channel (4,668 videos, 2016 to July 2026) to show how the channel has grown, where it is strongest, and what to test next.


## What it answers

- How have views and engagement changed year by year?
- Which video lengths perform best?
- Which videos have high engagement but low reach, and are worth promoting again?
- Is growth coming from better videos or from uploading more?

## Dashboard pages

| Page | Content |
|---|---|
| Overview | Total views, likes, comments, engagement rate, views by video length, yearly views and engagement trend |
| Video Performance | Reach vs engagement scatter, top 10 videos, 92 "priority" videos |
| Growth Trends | Uploads vs average views per video, likes and comments per view, yearly summary |

### Page 1: Overview
<img width="1311" height="745" alt="page1_overview" src="https://github.com/user-attachments/assets/fd78e76f-ff28-4339-8c20-17a9726bc8cb" />


### Page 2: Video Performance
<img width="1317" height="792" alt="page2_video_performance" src="https://github.com/user-attachments/assets/68b3d57e-add9-4a80-bba1-207ccb64b35b" />


### Page 3: Growth Trends
<img width="1292" height="738" alt="page3_growth_trends" src="https://github.com/user-attachments/assets/01dd57a5-34da-4c76-ad5b-32d3a92a05d0" />

## Key findings

- 3.16 billion total views, 140M likes, 7.4M comments, 4.66% overall engagement.
- 2025 uploads were the strongest year (0.48 billion views).
- Videos over 15 minutes average the most views (0.72M) but are only 13% of uploads.
- Uploads doubled from 403 (2022) to 832 (2025), while average views per video fell from 0.93M to about 0.57M.
- Engagement fell from 6.5% (2021 uploads) to 2.6% (2026 uploads), mostly due to fewer comments per view.
- 92 videos (about 2%) have over 10% engagement and 200K to 1M views.

## Data

- Source: video-level YouTube data (video id, title, publish date, duration, views, likes, comments), extracted on 20 July 2026.
- Engagement rate = (likes + comments) / views.
- Years are grouped by the year a video was published.

## Measures used (DAX)

```DAX
Video Count = COUNTROWS(Query1)

Avg Views per Video = DIVIDE([Total Views], [Video Count])

Likes per View = DIVIDE([Total Likes], [Total Views])

Comments per View = DIVIDE([Total Comments], [Total Views])

Priority Gems =
CALCULATE(
    COUNTROWS(Query1),
    Query1[engagement_rate] > 10,
    Query1[view_count] >= 200000,
    Query1[view_count] < 1000000
)
```

`engagement_rate` is stored in percent units (for example 4.5 means 4.5%), so thresholds use whole numbers.

## Limits

- Newer videos have had less time to collect views, likes and comments, so part of the drop in recent averages is timing.
- 2026 is a part year. Years with few videos (2016: 16, 2017: 167) are less reliable.
- The analysis shows what happened, not why. Recommendations are ideas to test.

## Files

- `youtube.pbix`: Power BI report (add your file here)
- `YouTube_Channel_Performance_Report.pdf`: written report for the channel owner
- `images/`: dashboard screenshots used above

## How to open

Open `youtube.pbix` in Power BI Desktop and click Home, then Refresh if the data source path needs updating.


