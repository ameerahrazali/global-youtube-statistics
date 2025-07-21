# YouTube Statistics Analysis

This repository presents a **structured data analysis** of global YouTube channel statistics using **R**. The project explores **trends across content categories and countries** using both **descriptive and inferential statistics**. Key performance indicators such as **subscriber count**, **total views**, and **upload volume** are analyzed. The final output includes **visualizations, simulation-based inference, and clear interpretations**.

**Report:** [View HTML Report](http://rpubs.com/ameerahrazali/youtube-stats-analysis)  
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
- Visualized trends using bar charts

### 3. **Data Visualization**  
- Developed an interactive bubble chart (subscribers vs video views)  
- Used `highcharter` for bubble chart and 3D column chart  

### 4. **Inferential Analysis - Normality and Non-Parametric Tests**
- Performed **Shapiro-Wilk normality tests** on "uploads" and "subscribers" to assess their distribution.
    - **Key finding:** Both variables were found to be **non-normally distributed** (p-value < 0.05).
- Conducted a **Wilcoxon signed-rank test** to compare the median values of "uploads" and "subscribers."
    - **Key finding:** There is a **significant difference in the median values** between "uploads" and "subscribers" (p-value < 0.05).
- Applied **Spearman's rank correlation** to assess the monotonic relationship between "uploads" and "subscribers."
    - **Key finding:** There is **no statistically significant correlation** between "uploads" and "subscribers" (p-value > 0.05), despite a very weak positive correlation (rho = 0.052).

### 5. **Inferential Analysis - Bootstrap Simulation for Regression**
- Performed a **bootstrap simulation** (100 resamples) to estimate the relationship between "uploads" and "subscribers" using a linear regression model.
    - Calculated the mean slope, mean intercept, and mean R-squared from the simulated models.
    - **Critical finding:** The **standard deviations for slope, intercept, and R-squared were all zero**, indicating a potential issue with the simulation or data (e.g., lack of variability in resamples or an error in the bootstrapping process). This makes the current bootstrap results unreliable.
    - The **mean R-squared was very low (0.0063 or 0.63%)**, suggesting that "uploads" is a poor predictor of "subscribers" in this linear model, even if the simulation issue is resolved.

---

## Key Insights

* **Entertainment and Music** are the leading content categories by subscriber and view counts.
* **Upload volume alone does not significantly predict higher subscriber numbers** (supported by low Spearman's correlation and very low R-squared from bootstrap).
* **Countries like the United States and India dominate** in the number of top channels.
* There is **statistically significant evidence of subscriber count differences** across content categories, and also a **significant difference in median values between uploads and subscribers** (Wilcoxon test).
* **The relationship between uploads and subscribers is complex:** while their central tendencies differ, there's **no strong or significant monotonic correlation**, and linear models show very little predictive power. Further investigation is needed into the bootstrap simulation's zero standard deviations to confirm its findings.

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

While the current analysis provides valuable initial insights, especially concerning the non-normal distribution of key variables and the weak relationship between uploads and subscribers, the dataset contains **richer information** that can be utilized in future enhancements. These improvements aim to deepen our understanding and address some of the limitations encountered:

* **Address Bootstrap Simulation Issue:**
    * **Prioritize resolving the zero standard deviation issue** in the bootstrap simulation. This is crucial for obtaining reliable estimates and confidence intervals for regression coefficients.
    * Once resolved, use the bootstrap to **properly estimate the sampling distribution of regression coefficients and R-squared**, providing more robust insights into the relationship between uploads and subscribers.

* **Expand Predictive Modeling:**
    * Incorporate **`channel_type`**, **`video_views_rank`**, and **`country_rank`** to analyze performance by content specialization and channel standing.
    * Analyze **recent performance trends** using **`video_views_for_the_last_30_days`** and **`subscribers_for_last_30_days`** to understand short-term growth dynamics.
    * Add a **financial perspective** using:
        * `lowest_monthly_earnings`
        * `highest_monthly_earnings`
        * `lowest_yearly_earnings`
        * `highest_yearly_earnings`
    * Explore how **channel age** (using `created_year`, `created_month`, and `created_date`) affects growth trajectories.

* **Integrate External Factors:**
    * Integrate **country-level socioeconomic indicators**, such as:
        * `Gross tertiary education enrollment (%)`
        * `Population`
        * `Unemployment rate`
        * `Urban_population`
    * Visualize **channel locations** using **`Latitude`** and **`Longitude`** for geospatial analysis to identify regional trends or popular hubs.

These enhancements would enable **more comprehensive insights** into YouTube success factors, allow for **multivariate modeling** to identify stronger predictors, and provide a **more robust statistical foundation** by fully leveraging the bootstrap methodology.

