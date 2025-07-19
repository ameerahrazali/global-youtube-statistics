# YouTube Statistics Analysis

This repository presents a **structured data analysis** of global YouTube channel statistics using **R**. The project explores **trends across content categories and countries** using both **descriptive and inferential statistics**. Key performance indicators such as **subscriber count**, **total views**, and **upload volume** are analyzed. The final output includes **visualizations, simulation-based inference, and clear interpretations**.

**Report:** [View HTML Report](https://ameerahrazali.github.io/pages/youtube_stats_analysis.html)  
**Dataset:** [Kaggle – Global YouTube Statistics 2023](https://www.kaggle.com/datasets/nelgiriyewithana/global-youtube-statistics-2023)

---

## Objectives

- **Explore patterns** in YouTube performance metrics across countries and content types  
- **Identify key factors** influencing subscriber count and video views  
- **Compare performance** between categories using statistical testing and bootstrap simulation  

---

## Dataset Overview

The dataset contains information on **top-ranking YouTube channels globally**, sourced from Kaggle. It includes various **performance metrics and metadata** describing the channels.

### Data Dictionary (Used Variables)

| Variable         | Description                                                   |
|------------------|---------------------------------------------------------------|
| `Youtuber`       | Name of the YouTube channel                                   |
| `Rank`           | Global ranking based on subscriber count                      |
| `Grade`          | Letter grade assigned by third-party evaluators              |
| `subscribers`    | Total number of subscribers                                   |
| `video.views`    | Total accumulated video views                                 |
| `video.uploads`  | Number of videos uploaded                                     |
| `category`       | Content category (e.g., Entertainment, Music)                 |
| `title`          | Channel description or tagline                                |
| `Country`        | Country of origin                                             |
| `Abbreviation`   | Country abbreviation                                          |

---

## Analytical Workflow

### 1. **Data Preparation**  
- Imported the dataset and cleaned column names  
- Converted data types and removed duplicates or incomplete records  

### 2. **Descriptive Analysis**  
- Computed summary statistics for subscribers, views, and uploads  
- Aggregated metrics by category and country  
- Visualized trends using histograms, bar charts, and boxplots  

### 3. **Data Visualization**  
- Developed an interactive bubble chart (subscribers vs video views)  
- Used `highcharter` to compare countries and content categories  

### 4. **Inferential Analysis**  
- Applied bootstrap simulation and hypothesis testing to compare:  
  - Mean subscribers between Music and Entertainment categories  
  - Confidence intervals for mean differences  

---

## Key Insights

- **Entertainment and Music** are the leading content categories by subscriber and view counts  
- **Upload volume alone does not predict higher subscriber numbers**. Instead, content type and audience targeting matter more  
- **Countries like the United States and India dominate** in number of top channels, while others such as **South Korea show high engagement per channel**  
- There is **statistically significant evidence of subscriber count differences** across content categories  

---

## Tools Used

- **Programming Language:** R  
- **Libraries:** `tidyverse`, `psych`, `highcharter`, `stringr`  
- **Documentation:** R Markdown  
- **Version Control:** Git and GitHub  

---

## Project Structure

```yaml
global-youtube-statistics/
├── data/
│   └── Global YouTube Statistics.csv
├── youtube_stats_analysis.Rmd       # R Markdown source file
├── youtube_stats_analysis.html      # Rendered HTML report
├── .gitignore
└── README.md                        # Project documentation
```
---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/ameerahrazali/global-youtube-statistics.git
   ```
2. Open the .Rmd file in RStudio.
3. Run or knit the document to generate the HTML report.

--- 

## Future Improvements

While the current analysis focuses on a subset of variables, the dataset contains **richer information** that can be utilized in future enhancements:

- Incorporate **`channel_type`**, **`video_views_rank`**, and **`country_rank`** to analyze performance by content specialization  
- Analyze **recent performance trends** using **`video_views_for_the_last_30_days`** and **`subscribers_for_last_30_days`**  
- Add a **financial perspective** using:  
  - `lowest_monthly_earnings`  
  - `highest_monthly_earnings`  
  - `lowest_yearly_earnings`  
  - `highest_yearly_earnings`  
- Explore how **channel age** (using `created_year`, `created_month`, and `created_date`) affects growth  
- Integrate **country-level socioeconomic indicators**, such as:  
  - `Gross tertiary education enrollment (%)`  
  - `Population`  
  - `Unemployment rate`  
  - `Urban_population`  
- Visualize **channel locations** using **`Latitude`** and **`Longitude`** for geospatial analysis  

These enhancements would enable **more comprehensive insights** and support **multivariate modeling** of YouTube success factors.

