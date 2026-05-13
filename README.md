# Claude Data Analysis Skill

> Professional data analysis assistant for Claude Code. 6 core modules, 25+ sub-skills, automated reporting, and BI-ready outputs.

## Quick Install

```bash
git clone --depth 1 https://github.com/realchenwenqiao/claude-data-analysis.git
cd claude-data-analysis
# Copy SKILL.md to your project's .claude/skills/ folder
```

## What This Skill Does

Turn Claude Code into your personal data analyst:

| Module | Capabilities |
|--------|-------------|
| **Data Cleaning** | Format conversion, missing value handling, outlier detection, deduplication |
| **Auto Visualization** | Chart recommendation, interactive dashboards, export to PNG/SVG |
| **Report Generation** | PDF reports, Excel exports, PowerPoint slides, HTML dashboards |
| **SQL Assistant** | Query optimization, schema analysis, join suggestions, performance tuning |
| **Statistical Analysis** | Regression, clustering, time series, hypothesis testing, predictions |
| **Data Monitoring** | Anomaly detection, trend alerts, KPI tracking, drift monitoring |

## Sub-Skills Overview

### 1. `/data-clean`
Clean messy datasets with one command:
- Handle missing values (fill, drop, interpolate)
- Detect and fix outliers (IQR, Z-score, ML-based)
- Normalize formats (dates, currencies, units)
- Remove duplicates and validate integrity

### 2. `/data-viz`
Generate professional visualizations:
- Auto-recommend best chart type
- Create interactive Plotly/Chart.js dashboards
- Export to high-quality PNG/SVG/PDF
- Color palette optimization (accessibility-friendly)

### 3. `/data-report`
Generate business-ready reports:
- Executive summary PDF (branding-ready)
- Detailed Excel workbook with pivot tables
- PowerPoint presentation (auto-layout)
- HTML dashboard (responsive, embeddable)

### 4. `/sql-help`
SQL query assistance:
- Optimize slow queries (index suggestions)
- Explain complex joins visually
- Schema documentation generator
- Query plan analysis

### 5. `/stats-analyze`
Statistical analysis toolkit:
- Linear/multiple regression
- K-means clustering
- Time series forecasting (ARIMA, Prophet)
- A/B test significance calculator

### 6. `/data-monitor`
Data quality monitoring:
- Anomaly score calculation
- Trend drift alerts
- KPI threshold checks
- Scheduled report generation

## Example Usage

```bash
# In Claude Code, invoke any sub-skill:

/data-clean --input sales.csv --output clean_sales.csv

/data-viz --data clean_sales.csv --type auto --export dashboard.html

/data-report --data results.xlsx --format pdf --title "Q1 Sales Analysis"

/sql-help --query "SELECT * FROM orders WHERE..." --optimize

/stats-analyze --data metrics.csv --method regression --predict 30days

/data-monitor --data daily_stats.csv --alert anomalies --threshold 0.95
```

## Output Formats

| Format | Use Case |
|--------|----------|
| PDF | Executive reports, board presentations |
| Excel | Detailed analysis, pivot tables |
| PowerPoint | Stakeholder presentations |
| HTML | Interactive web dashboards |
| JSON | API integration, automation |
| SVG/PNG | Publication-ready charts |

## Requirements

- Python 3.10+ (for analysis modules)
- Node.js 18+ (for visualization generation)
- Claude Code CLI

Optional integrations:
- Pandas, NumPy, SciPy (Python)
- Plotly, Chart.js (Visualization)
- Apache Arrow (Large datasets)

## Why This Skill?

**vs. Traditional BI Tools:**

| Feature | Claude Data Analysis | Power BI | Tableau |
|---------|---------------------|----------|---------|
| Cost | Free + MIT | $10/user/mo | $15/user/mo |
| Setup | 5 minutes | Hours | Hours |
| Customization | Unlimited | Limited | Limited |
| AI Insights | Built-in | Add-on | Add-on |
| Terminal-based | Yes | No | No |

## Roadmap

- [ ] Database direct connection (PostgreSQL, MySQL, MongoDB)
- [ ] Real-time streaming data support
- [ ] ML model integration (scikit-learn, TensorFlow)
- [ ] Multi-language reports (中文, 日本語, Español)
- [ ] Cloud deployment templates

## License

MIT License - Free for personal and commercial use.

## Author

Built for Claude Code by realchenwenqiao.

---

**Star this repo if it helps your data analysis workflow!**