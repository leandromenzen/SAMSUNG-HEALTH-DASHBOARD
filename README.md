# Samsung Health Dashboard

A visual, analytical dashboard for your exported **Samsung Health** data — much more in-depth than the app's own charts. A single self-contained HTML file that reads your exported CSVs and turns them into charts, comparisons, and cross-metric insights.

No install, no server, no account. Just open the file, pick the folder with your CSVs, and the dashboard builds itself instantly — **entirely in your browser**. No data ever leaves your machine.

---

## ✨ What's inside

### 📋 Overview
Consolidated KPIs (average heart rate, average sleep, steps/day, current weight) plus automatic highlights based on your recent data.

### ❤️ Heart
- Heart rate throughout the day (pick any date)
- Minimum, maximum, and resting heart rate
- Heart rate distribution by hour of day
- Average heart rate by day of the week
- Elevated heart rate episodes outside of workouts
- Resting heart rate trend over time

### 😴 Sleep
- Bedtime and wake-up time
- Total sleep duration per night
- Stage breakdown: light, deep, REM sleep, and awakenings
- Sleep schedule regularity
- Weekday vs. weekend comparison
- Full table of every recorded night

### 🏃 Exercise
- Distance, duration, calories, and heart rate per session
- Weekly distance and calorie trends
- Training load (acute vs. chronic)
- Distance vs. average heart rate relationship
- Detailed table of all sessions

### 📊 Evolution
Weight, steps, sleep, heart rate, workout frequency, and stress — all plotted over time, side by side.

### 🔀 Cross-analysis
The most analytical part of the dashboard — it cross-references different metrics to answer questions like:
- On nights you slept less than 6h30, what was your average heart rate the next day?
- How does your heart rate behave on workout days compared to rest days?
- Is there a relationship between sleep duration and stress level?
- Do more active days (more steps) lead to longer sleep that night?

Each cross-analysis includes an automatically calculated correlation coefficient (r).

---

## 🚀 How to use

1. **Export your Samsung Health data**
   In the app, go to *Settings → Sync data with Samsung Cloud* (or *Manage data → Download personal data*) and export a `.zip` file.

2. **Extract the `.zip`** into a folder on your computer. It should contain `.csv` files (named like `com.samsung.shealth.tracker.heart_rate.*.csv`, `com.samsung.health.sleep_stage.*.csv`, etc.).

3. **Open `samsung_health_dashboard.html`** by double-clicking it — it works in any modern browser (Chrome, Edge, Firefox).

4. Click **"Select folder"** and choose the folder where you extracted the CSVs.

5. That's it — the dashboard builds itself. Whenever you export new data from Samsung Health, just click "Select folder" again to refresh.

> Browsers can't watch a folder for changes on their own for security reasons — refreshing is always a manual one-click action.

---

## 🔒 Privacy

Everything runs locally, in your browser's JavaScript. There's no backend, no upload, no telemetry. The file is fully self-contained: the libraries it uses (PapaParse for CSV parsing and Chart.js for charts) are embedded directly in the HTML, so the dashboard even works without an internet connection.

---

## 🛠️ Tech stack

- Plain HTML + CSS + JavaScript (no build step, no runtime dependencies)
- [PapaParse](https://www.papaparse.com/) for CSV parsing
- [Chart.js](https://www.chartjs.org/) for charts

---

## ⚠️ Known limitations

- **HRV**: Samsung Health's CSV export doesn't include actual HRV numeric values (they're stored in internal binary files), so this metric shows as unavailable.
- **Exercise types**: Samsung Health identifies activities by internal numeric codes; the dashboard recognizes the most common ones (walking, running, cycling, swimming, strength training, yoga) and falls back to `Activity #NNN` for the rest.
- Works best in modern browsers that support folder selection via `<input webkitdirectory>` (Chrome, Edge, Firefox, Opera).
