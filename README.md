# DMoney Fitness Tracker

A single-page fitness dashboard that pulls data from Google Sheets and visualizes progress toward weight loss and body composition goals.

## Features

- **Overview** — At-a-glance progress bars, trends, and key stats
- **Weight & Body Fat** — Weight and body fat tracking with charts and day-over-day changes
- **Calories** — Daily consumed vs. burned with deficit tracking
- **Activity** — Rucking distance, lift streak, and sleep tracking
- **Measurements** — Weekly body measurements (chest, waist, hips) with trend chart and change-from-start deltas
- **Challenges & PRs** — Separated into weight-based and time-based sections, each with their own charts, metrics, and log tables

## Google Sheets Structure

Data lives in a Google Sheet with five tabs, published as CSV. The dashboard fetches it client-side using [PapaParse](https://www.papaparse.com/). Charts are rendered with [Chart.js](https://www.chartjs.org/).

No build step, no backend — just a single `index.html` file.

### Weight (gid: 0)
| Column | Description |
|--------|-------------|
| Date | Entry date |
| Weight | Weight in lbs |
| Body Fat Lbs | Body fat in lbs |

### Calories (gid: 1245612249)
| Column | Description |
|--------|-------------|
| Date | Entry date |
| Consumed | Calories consumed |
| Burned | Calories burned |

### Activity (gid: 780168580)
| Column | Description |
|--------|-------------|
| Date | Entry date |
| Rucking Distance Miles | Rucking distance in miles |
| Lifted | Yes/No |
| Sleep Hours | Hours of sleep |

### Measurements (gid: 2074990521)
| Column | Description |
|--------|-------------|
| Date | Sunday measurement date |
| Chest | Chest measurement in inches |
| Waist | Waist measurement in inches |
| Hips | Hip measurement in inches |

### Challenges (gid: 1121342237)
| Column | Description |
|--------|-------------|
| Date | Entry date |
| Name | Challenge/PR name |
| Weight | Weight in lbs (for weight-based challenges) |
| Time | Time value e.g. 5:30 (for time-based challenges) |
| Notes | Optional notes |

## Setup

1. Create a Google Sheet with tabs for Weight, Calories, Activity, Measurements, and Challenges
2. Publish the sheet to the web (File > Share > Publish to web) as CSV
3. Update the `gid` values in `index.html` to match your sheet's tab IDs
4. Open `index.html` in a browser or deploy to any static host

## Changelog

### 2026-04-05
- Added Measurements tab with chest, waist, and hips tracking (trend chart, delta metrics, log table)
- Split Challenges & PRs into separate weight-based and time-based sections with independent charts and tables

### 2026-04-04
- Updated body fat goal from 15 lbs to 20 lbs
- Fixed CSV date normalization to ISO format for correct chart labels
- Fixed broken JS
- Switched to published CSV URLs for Google Sheets
