
# Marketing A/B Testing & Conversion Rate Analysis

An R-based statistical analysis of an e-commerce marketing A/B test, comparing purchase conversion rates between users shown product advertisements and users shown public service announcements (PSAs).

This academic group project explores how **permutation testing** and **centered bootstrap resampling** can help assess an observed difference in conversion rates. The analysis includes exploratory data analysis, visualizations, hypothesis tests, and discussion of limitations.

## Business Question

**Do product advertisements generate a higher purchase conversion rate than public service announcements?**

Two groups are compared:

- **Ad (`ad`):** Users shown product advertisements.
- **Control (`psa`):** Users shown public service announcements.

The primary outcome is **conversion** (`converted`), indicating whether a user made a purchase.

## Key Results

| Metric | Result |
|---|---|
| Ad-group conversion rate | **2.55%** |
| PSA-group conversion rate | **1.79%** |
| Observed absolute difference | **Approximately +0.77 percentage points** |
| Resampling iterations | **10,000 per method** |
| Statistical methods | **Permutation Test and Centered Bootstrap Test** |

The analysis found strong statistical evidence of a higher observed conversion rate in the advertisement group.

## Methodology

### 1. Data Preparation and Exploratory Data Analysis

- Load and inspect the marketing A/B testing dataset.
- Clean and standardize column names.
- Examine group distributions and conversion outcomes.
- Calculate conversion rates for the advertisement and control groups.

### 2. Conversion Rate Comparison

Compare conversion rates between the two experimental groups.

The hypotheses are:

**Null hypothesis (H0):**

The advertisement group does not have a higher conversion rate than the control group.

**Alternative hypothesis (H1):**

The advertisement group has a higher conversion rate than the control group.

### 3. Permutation Test

A permutation test is performed using **10,000 random permutations** to construct a null distribution of conversion-rate differences.

The observed difference is compared with the simulated null distribution to estimate statistical significance.

### 4. Centered Bootstrap Test

A centered bootstrap procedure is conducted with **10,000 resamples** to evaluate the observed difference under a null-centered resampling approach.

### 5. Results Interpretation

The results are interpreted in terms of:

- Statistical significance
- Observed conversion-rate difference
- Potential business implications
- Limitations of the analysis

## Tools & Technologies

- **Programming Language:** R
- **Reporting:** R Markdown
- **Data Processing:** tidyverse, janitor
- **Data Visualization:** ggplot2, RColorBrewer
- **Statistical Analysis:** Permutation Test, Bootstrap, Hypothesis Testing
- **Additional Libraries:** boot, infer

## Repository Structure

```text
Marketing-AB-Testing-Analysis/
├── README.md
├── Miniproject_ABTesting.Rmd
├── Miniproject_ABTesting.html
├── marketing_AB.csv
```

**File descriptions:**

- `README.md`: Project overview, methodology, results, and instructions.
- `marketing_ab_testing.Rmd`: R source code and statistical analysis.
- `marketing_ab_testing.html`: Rendered HTML analysis report.
-  marketing_AB.csv`: Marketing A/B testing dataset.

## How to Run

### Step 1: Install R and RStudio

Download and install:

- [R](https://cran.r-project.org/)
- [RStudio Desktop](https://posit.co/download/rstudio-desktop/)

### Step 2: Clone the Repository

```bash
git clone https://github.com/thaominh2024/Marketing-AB-Testing-Analysis.git

cd Marketing-AB-Testing-Analysis
```

### Step 3: Install Required Packages

Open RStudio and run:

```r
install.packages(c(
  "rmarkdown",
  "knitr",
  "tidyverse",
  "janitor",
  "ggplot2",
  "boot",
  "infer",
  "RColorBrewer"
))
```

### Step 4: Prepare the Dataset

Place the dataset in the following directory:

```text
data/marketing_AB.csv
```

The dataset contains the following variables:

| Variable | Description |
|---|---|
| `user_id` | Unique user identifier |
| `test_group` | Experimental group (`ad` or `psa`) |
| `converted` | Whether the user made a purchase |
| `total_ads` | Total number of advertisements viewed |
| `most_ads_day` | Day with the highest ad exposure |
| `most_ads_hour` | Hour with the highest ad exposure |

### Step 5: Execute the Analysis

Open:

```text
marketing_ab_testing.Rmd
```

Alternatively, open `analysis.html` in a web browser to view the existing report without executing the code.

## Limitations

This analysis has several limitations:

1. **Randomization:** The available data does not independently verify how users were randomly assigned to experimental groups.

2. **Group imbalance:** The experimental groups may have substantially different sample sizes.

3. **Potential confounding:** Other factors may influence conversion behavior.

4. **Monte Carlo p-values:** A simulated p-value displayed as zero does not imply that the true p-value is exactly zero. With 10,000 resamples, a result with no exceedances can be reported as approximately `p < 0.0001`.

5. **Confidence intervals:** Adding a bootstrap confidence interval for the conversion-rate difference would provide a more complete assessment of uncertainty.

6. **Business impact:** Statistical significance alone does not establish whether the advertisement campaign is economically profitable.


The primary objective is to demonstrate practical skills in statistical analysis, experimental evaluation, data visualization, and evidence-based interpretation of business outcomes.
