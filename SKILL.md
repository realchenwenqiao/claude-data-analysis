---
skillName: claude-data-analysis
description: Professional data analysis assistant for Claude Code. 6 modules, 25+ sub-skills covering cleaning, visualization, reporting, SQL, statistics, and monitoring.
version: 1.0.0
author: realchenwenqiao
license: MIT
---

# Claude Data Analysis Skill

Professional data analysis toolkit that transforms Claude Code into a full-featured BI assistant.

## Core Capabilities

When this skill is loaded, Claude gains expertise in:

1. **Data Cleaning & Preparation**
   - Format standardization (CSV, JSON, Parquet, Excel)
   - Missing value strategies (imputation, interpolation, dropping)
   - Outlier detection (statistical + ML methods)
   - Schema validation and normalization

2. **Automated Visualization**
   - Chart type recommendation based on data characteristics
   - Interactive dashboards (Plotly, Chart.js, ECharts)
   - Publication-quality exports (SVG, PNG, PDF)
   - Color palette optimization (WCAG accessible)

3. **Report Generation**
   - Executive PDF summaries with branding
   - Multi-sheet Excel workbooks with pivot tables
   - PowerPoint decks with auto-layout
   - Responsive HTML dashboards

4. **SQL Intelligence**
   - Query optimization and index suggestions
   - Join path visualization
   - Schema documentation
   - Performance bottleneck analysis

5. **Statistical Analysis**
   - Regression models (linear, polynomial, logistic)
   - Clustering (K-means, hierarchical, DBSCAN)
   - Time series forecasting (ARIMA, Prophet-style)
   - Hypothesis testing and confidence intervals

6. **Data Quality Monitoring**
   - Anomaly scoring and drift detection
   - KPI threshold alerting
   - Trend analysis and forecasting
   - Automated health reports

---

## Sub-Skills

### `/data-clean` - Data Cleaning Pipeline

**Purpose:** Transform raw, messy data into analysis-ready datasets.

**Arguments:**
- `--input`: Source file path (CSV, JSON, Excel, Parquet)
- `--output`: Cleaned output path
- `--strategy`: Cleaning strategy (auto|aggressive|conservative|custom)
- `--report`: Generate cleaning summary (true|false)

**Workflow:**
1. Load and profile dataset (shape, types, missing, unique)
2. Detect and handle missing values
3. Identify outliers using IQR, Z-score, or isolation forest
4. Normalize formats (dates → ISO 8601, currencies → float)
5. Validate data integrity
6. Export cleaned dataset + cleaning log

**Example:**
```
/data-clean --input raw_sales.csv --output clean_sales.csv --strategy auto --report true
```

---

### `/data-viz` - Visualization Generator

**Purpose:** Create professional visualizations from any dataset.

**Arguments:**
- `--data`: Input dataset
- `--type`: Chart type (auto|bar|line|scatter|pie|heatmap|treemap|radar|3d)
- `--interactive`: Enable interactivity (true|false)
- `--export`: Output format (html|svg|png|pdf|all)
- `--palette`: Color scheme (default|accessible|brand|custom)

**Workflow:**
1. Analyze data characteristics (dimensions, measures, time-series?)
2. Recommend optimal chart type if `--type auto`
3. Generate visualization code (Plotly/Chart.js)
4. Apply color palette and styling
5. Export in requested format(s)

**Example:**
```
/data-viz --data metrics.csv --type auto --interactive true --export all
```

---

### `/data-report` - Report Generator

**Purpose:** Generate business-ready reports and presentations.

**Arguments:**
- `--data`: Analysis results or raw data
- `--format`: Output format (pdf|excel|pptx|html|all)
- `--title`: Report title
- `--template`: Style template (executive|technical|minimal|brand)
- `--sections`: Include sections (summary|details|charts|recommendations|all)

**Workflow:**
1. Analyze data to extract key insights
2. Generate executive summary
3. Create detailed analysis sections
4. Embed visualizations
5. Format according to template
6. Export in requested format(s)

**Example:**
```
/data-report --data analysis.json --format pdf --title "Q1 Performance Review" --template executive
```

---

### `/sql-help` - SQL Assistant

**Purpose:** Optimize, explain, and debug SQL queries.

**Arguments:**
- `--query`: SQL query to analyze
- `--mode`: Operation mode (optimize|explain|schema|debug)
- `--dialect`: SQL dialect (postgres|mysql|sqlite|snowflake|bigquery)
- `--schema`: Database schema file (optional)

**Workflow:**
1. Parse and validate SQL syntax
2. Identify performance bottlenecks
3. Suggest index optimizations
4. Explain join paths visually
5. Generate execution plan analysis
6. Provide rewritten optimized query

**Example:**
```
/sql-help --query "SELECT * FROM orders o JOIN customers c ON o.customer_id = c.id WHERE o.date > '2024-01-01'" --mode optimize --dialect postgres
```

---

### `/stats-analyze` - Statistical Analysis

**Purpose:** Perform advanced statistical analysis and modeling.

**Arguments:**
- `--data`: Input dataset
- `--method`: Analysis method (regression|cluster|timeseries|test|correlation)
- `--target`: Target variable for supervised methods
- `--predict`: Prediction horizon (e.g., 30days, 12months)
- `--confidence`: Confidence level (0.90|0.95|0.99)

**Workflow:**
1. Load and validate dataset
2. Perform specified statistical method
3. Calculate metrics (R², p-values, confidence intervals)
4. Generate model diagnostics
5. Create visualization of results
6. Export analysis report

**Example:**
```
/stats-analyze --data sales_history.csv --method timeseries --predict 90days --confidence 0.95
```

---

### `/data-monitor` - Data Quality Monitor

**Purpose:** Monitor data quality and detect anomalies.

**Arguments:**
- `--data**: Historical data for baseline
- `--new**: New data to check
- `--alert**: Alert type (anomalies|drift|threshold|all)
- `--threshold**: Anomaly threshold (0.80-0.99)
- `--schedule**: Monitoring frequency (hourly|daily|weekly)

**Workflow:**
1. Establish baseline statistics from historical data
2. Compare new data against baseline
3. Calculate anomaly scores
4. Detect distribution drift (KS test, KL divergence)
5. Generate alert if threshold exceeded
6. Create monitoring report

**Example:**
```
/data-monitor --data baseline.csv --new today.csv --alert anomalies --threshold 0.95
```

---

## Integration Patterns

### Chain Commands for Full Pipeline

```bash
# Complete analysis pipeline
/data-clean --input raw.csv --output clean.csv
/data-viz --data clean.csv --type auto --export charts/
/data-stats --data clean.csv --method regression --target revenue
/data-report --data results.json --format pdf --title "Analysis Report"
```

### Parallel Analysis

```bash
# Run multiple analyses simultaneously
/stats-analyze --data data.csv --method regression &
/stats-analyze --data data.csv --method cluster &
/stats-analyze --data data.csv --method correlation &
```

### Scheduled Monitoring

```bash
# Set up continuous monitoring
/data-monitor --data baseline.csv --new daily/*.csv --schedule daily --alert drift
```

---

## Output Standards

All outputs follow consistent standards:

### File Naming
- Cleaned data: `{original}_cleaned_{timestamp}.csv`
- Visualizations: `{dataset}_viz_{charttype}_{timestamp}.html`
- Reports: `{topic}_report_{timestamp}.{format}`
- Analysis: `{method}_analysis_{timestamp}.json`

### JSON Schema for Analysis Results
```json
{
  "metadata": {
    "timestamp": "ISO8601",
    "method": "string",
    "data_source": "string"
  },
  "statistics": {
    "r_squared": "number|null",
    "p_value": "number|null",
    "confidence_interval": ["lower", "upper"]
  },
  "insights": ["string"],
  "recommendations": ["string"],
  "visualizations": ["path"]
}
```

### Report Templates

| Template | Style | Use Case |
|----------|-------|----------|
| executive | Clean, minimal, highlights | Board presentations |
| technical | Detailed, code snippets | Developer documentation |
| minimal | Plain, no styling | Email attachments |
| brand | Custom colors, logo | Client deliverables |

---

## Best Practices

### Data Size Guidelines
- <10MB: Direct analysis
- 10-100MB: Streaming/chunked processing
- >100MB: Use Parquet + Arrow, or database connection

### Performance Tips
- Use `--strategy conservative` for large datasets
- Enable `--interactive false` for batch exports
- Cache intermediate results with `--cache true`

### Error Handling
- All errors logged to `{output}_errors.log`
- Partial outputs preserved on failure
- Retry suggestions included in error messages

---

## Dependencies

### Required
- Python 3.10+
- Claude Code CLI

### Recommended
- pandas, numpy (data manipulation)
- scipy, statsmodels (statistics)
- matplotlib, plotly (visualization)
- openpyxl, python-pptx (reports)

### Optional Integrations
- PostgreSQL/MySQL connectors
- Apache Arrow (large data)
- Redis (caching)
- S3/GCS (cloud storage)

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-05-13 | Initial release with 6 core modules |

---

## Support

- GitHub Issues: [realchenwenqiao/claude-data-analysis](https://github.com/realchenwenqiao/claude-data-analysis)
- Email: cwq940061186@gmail.com

---

*This skill transforms Claude Code into a professional data analyst. Use it to automate your entire data workflow.*