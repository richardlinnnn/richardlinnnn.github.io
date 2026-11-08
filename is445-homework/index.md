---
layout: default
title: Illinois Professional Licensing — IS 445
---

<style>
.is445-wrapper {max-width: 1000px; margin: 0 auto; color:#1f2937; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Arial, sans-serif; line-height:1.7;}
.is445-wrapper h1 {font-size:2.25rem; line-height:1.2; margin-bottom: .35rem;}
.is445-wrapper h2 {font-size:1.45rem; margin-top: 2rem;}
.is445-wrapper .small {color:#556479; font-size:.95rem;}
.is445-wrapper .links a {display:inline-block; padding:.5rem .9rem; margin:.5rem .7rem .5rem 0; border:1px solid #2378a4; color:#185d80; border-radius:6px; text-decoration:none;}
.is445-wrapper .chart-box {border:1px solid #dbe4ef; border-radius:10px; padding:8px; background:white;}
.is445-wrapper iframe {display:block; width:100%; border:0; height:510px;}
@media(max-width:720px){ .is445-wrapper iframe{height:600px;} }
</style>

<div class="is445-wrapper" markdown="1">

# Illinois Professional Licensing Patterns

<p class="small">IS 445 · Two Altair/Vega-Lite visualizations · Public Fall 2022 course sample</p>

<p>This project explores the recorded statuses and original issue years of a sample of Illinois professional licenses. It is based on historical sampled records, not a complete or current count of all active licenses.</p>

<div class="links">
<a href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/licenses_fall2022.csv" target="_blank" rel="noopener">The Data</a>
<a href="https://github.com/richardlinnnn/richardlinnnn.github.io//blob/main/is445-homework/analysis.ipynb" target="_blank" rel="noopener">The Analysis</a>
</div>

## Visualization 1: License status composition

<div class="chart-box">
<iframe src="{{ '/is445-homework/chart1.html' | relative_url }}" title="Stacked bar chart of license status by licensing category" loading="lazy"></iframe>
</div>

The first visualization compares how recorded license statuses are distributed across the eight most common license types in this sample. I used a horizontal 100% stacked bar chart because the licensing categories have different numbers of records, and percentages make it easier to compare their composition. The y-axis shows the license type, while the x-axis represents the share of records. I used blue for active, amber for not renewed, and gray for other statuses, so the different groups are easy to recognize without creating too many legend categories. In Python, I trimmed inconsistent text, removed missing categories and statuses, selected the eight most common license types, grouped less common status labels into “Other,” and counted the number of records in each group. These results show patterns in the provided sample, not the current status of every Illinois professional license.

## Visualization 2: Original issue counts over time

<div class="chart-box">
<iframe src="{{ '/is445-homework/chart2.html' | relative_url }}" title="Interactive line chart of original license issue counts with license type dropdown" loading="lazy"></iframe>
</div>

The second visualization shows the number of records whose original issue date falls in each year from 1990 through 2022. I chose a line chart because it makes changes over time easier to follow. The x-axis represents the original issue year, and the y-axis represents the number of sampled license records. I used a single blue line rather than different colors for every category, since the plot displays one selected license type at a time. For data preparation, I converted the original issue dates into datetime values, extracted their years, removed invalid dates and years outside the chosen range, and counted records by license type and year. I also calculated a combined series for the eight included types so there is a useful overview when the page first loads.

**Interactivity:** The dropdown below the second chart lets visitors switch between the combined view and individual license types. This provides a clearer comparison than displaying many overlapping lines at once. Hover tooltips also show the exact year and number of records. The dropdown uses an Altair parameter and filter, so it is interactive beyond ordinary panning or zooming.

<p class="small">Source: UIUC iSchool Data Visualization course dataset (`licenses_fall2022.csv`). Status and issue-date comparisons are descriptive for this sample and should not be interpreted as statewide rates.</p>

</div>
