# CO₂ Emissions, GDP, HDI, Life Expectancy & Gender Inequality — Cross-Country Analysis

## Abstract
This project examines how countries’ **CO₂ emissions**, **Gross Domestic Product (GDP)**, **Human Development Index (HDI)**, **Life Expectancy**, and **Gender Inequality Index (GII)** are related.  
The aim is to understand whether industrial and economic growth lead to higher living standards and equality, or if they come at an environmental and social cost.  
Using open datasets and Python-based analysis, the project applies data cleaning, exploratory analysis, and correlation-based hypothesis testing to evaluate these relationships.  
After constructing a unified dataset for 2010–2019 and applying interpolation where necessary, a **clean 2019 cross-sectional dataset** is used for the analysis.

---

## Motivation
I chose this topic because I am genuinely interested in the connection between **economic growth, sustainability, and life expectancy**.  
While high-income countries often perform better in education, health, and living standards, they are also responsible for a large share of global CO₂ emissions.  
This led me to question whether **true development can occur without increasing environmental costs**, and whether sustainable countries can still achieve strong economic and social outcomes.  
This project helps me understand whether key global indicators—CO₂ emissions, GDP, HDI, life expectancy, and gender inequality—move together or diverge as countries develop.

---

## Objectives
1. Analyze the relationship between countries’ CO₂ emissions and GDP.  
2. Test whether higher GDP levels are associated with improvements in HDI and Life Expectancy.  
3. Examine if higher economic growth leads to more or less gender inequality.  
4. Compare economic, social, and environmental indicators across regions.  
5. Present findings through clear visualizations and statistical tests.

---

## Data Sources

All data are publicly available and ethically obtained.

| Dataset | Description | Source |
|----------|--------------|--------|
| CO₂ Emissions | Annual country-level CO₂ emission data |[Kaggle - CO₂ Emissions](https://www.kaggle.com/datasets/shreyanshdangi/co-emissions-across-countries-regions-and-sectors) |
| GDP (current US$) | Annual GDP values by country in current USD | [World Bank - GDP](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD)  |
| Human Development Index (HDI) | HDI, Life Expectancy, GII | [UNDP / Kaggle](https://www.kaggle.com/datasets/shreyanshdangi/co-emissions-across-countries-regions-and-sectors) |

All datasets were merged using ISO3 country codes and aligned between **2010–2019**.

---

## Methodology

### Data Collection & Cleaning
- Collected datasets from official and publicly accessible sources.  
- Converted all datasets to consistent ISO3 country codes and year formats.  
- Removed regional aggregates such as “World”, “Europe & Central Asia,” etc.  
- **Interpolated missing values across 2010–2019** to address gaps in variables such as HDI, GII, and CO₂.  
- Merged all indicators into a unified panel dataset.  
- Extracted a **clean 2019 cross-sectional dataset** for hypothesis testing.  
- Saved the consolidated dataset as `master_cross_section.csv`.

### Exploratory Data Analysis
- Generated descriptive statistics (mean, median, variance, missing values) for CO₂, GDP, HDI, Life Expectancy, and GII.  
- Inspected distributions and pairwise patterns using a seaborn pairplot (KDE on the diagonal and scatter plots off-diagonal).  
- Created a correlation heatmap for the main variables (CO₂, GDP, HDI, Life Expectancy, GII).  
- Produced country-ranked bar charts for the top 20 CO₂ emitters and top 20 countries by HDI.  
- Compared regions using continent-level boxplots for CO₂, HDI, Life Expectancy, GDP, and GII.
- Generated world choropleth maps for CO₂ emissions, HDI, GDP, and GII using Plotly.

### Statistical Testing
- Pearson and Spearman correlations were used to test the four main hypotheses.  
- Hypotheses were evaluated using the **clean 2019 cross-sectional subset** (complete cases).  
- Effect size, statistical significance, and expected directional relationships were considered.

---

## Hypotheses

| # | Hypothesis | Null Hypothesis (H₀) | Alternative Hypothesis (H₁) |
|---|-------------|-----------------------|-----------------------------|
| **1** | **CO₂–GDP Relationship** | CO₂ and GDP are not positively related. | Higher GDP is associated with higher CO₂ emissions. |
| **2** | **GDP–Life Expectancy Relationship** | GDP has no relationship with Life Expectancy. | Higher GDP increases Life Expectancy. |
| **3** | **GDP–Gender Inequality Relationship** | GDP has no effect on GII. | Higher GDP reduces GII. |
| **4** | **CO₂–HDI Relationship** | CO₂ emissions have no effect on HDI. | Higher CO₂ emissions reduce HDI. |

---

## Expected Findings
Originally, I expected:

- A clear **positive relationship** between GDP and CO₂ emissions.  
- A strong **positive link** between GDP and Life Expectancy.  
- **Lower gender inequality** (GII) in countries with higher GDP.  
- A **negative** relationship between CO₂ and HDI.

These expectations were only partially supported by the results.

---

## Hypothesis Test Results

| Hypothesis | Pearson r | Pearson p-value | Spearman r | Spearman p-value | Decision | Interpretation |
|-----------|------------|------------------|-------------|-------------------|----------|----------------|
| **H1: CO₂ → GDP** (expected +) | **0.847** | < 0.001 | **0.929** | < 0.001 | **Reject H₀** | Strong positive relationship; high-GDP countries emit more CO₂. |
| **H2: GDP → Life Expectancy** (expected +) | **0.199** | 0.0098 | **0.570** | < 0.001 | **Reject H₀** | Higher GDP is associated with longer life expectancy. |
| **H3: GDP → GII** (expected –) | **–0.191** | 0.0134 | **–0.487** | < 0.001 | **Reject H₀** | Higher GDP countries tend to have lower gender inequality. |
| **H4: CO₂ → HDI** (expected –) | **0.115** | 0.138 | **0.509** | < 0.001 | **Fail to Reject H₀** | No negative relationship; high-HDI countries often have high emissions. |

### Summary Interpretation
- **H1, H2, H3 are supported** using both Pearson and Spearman correlations.  
  GDP is positively associated with CO₂ and Life Expectancy, and negatively associated with GII.  
- **H4 is not supported**. CO₂ emissions do not decrease as HDI increases; many high-HDI countries also have high emissions.
  
---

## Visualizations Used

The analysis is supported by the following visualizations:

- **Correlation heatmap** for CO₂, GDP, HDI, Life Expectancy, and GII  
- **Pairwise scatter plots (pairplot)** showing relationships and KDE distributions  
- **Top 20 bar charts**:
  - Top 20 countries by total CO₂ emissions  
  - Top 20 countries by HDI  
- **Continent-level boxplots** for:
  - CO₂ emissions  
  - HDI  
  - Life Expectancy  
  - GDP  
  - Gender Inequality Index (GII)
- **World maps**:
  - Choropleth map of CO₂ emissions, HDI, GDP, Life Expectancy and GII (2019)
    
---
## Machine Learning Analysis

In addition to correlation-based hypothesis testing, basic machine learning models were applied to examine whether key development indicators can predict human development outcomes.

The analysis was conducted using the **clean 2019 cross-sectional dataset**, ensuring consistency with the hypothesis testing framework.

### Target Variable
**Life Expectancy** was selected as the target variable, as it represents a core outcome of human development and aligns directly with the project’s motivation.

### Features
The following variables were used as predictors:
- CO₂ emissions (total)
- GDP
- Human Development Index (HDI)
- Gender Inequality Index (GII)

### Models Applied
Two supervised regression models were implemented:
- Linear Regression
- Random Forest Regressor

### Train–Test Split
The dataset was split into:
- **80% training data**
- **20% testing data**

This split was used to evaluate model performance on unseen data.

### Evaluation Metrics
Model performance was assessed using:
- Mean Squared Error (MSE)
- R² Score (coefficient of determination)

### Model Performance Results (2019 Cross-Section)

| Model              | MSE  | R² Score |
|--------------------|------|----------|
| Linear Regression  | 7.387 | 0.892 |
| Random Forest      | 8.515 | 0.876 |

### Results Summary
- The Linear Regression model achieved a slightly higher R² score, indicating strong overall explanatory power under linear assumptions.
- The Random Forest model performed competitively and was particularly useful for capturing potential non-linear relationships between variables.
- Feature importance analysis from the Random Forest model showed that **HDI** was the most influential predictor of life expectancy, followed by **GDP**.
- CO₂ emissions and Gender Inequality Index (GII) contributed less to predictive performance compared to economic and social development indicators.

### Interpretation
The machine learning results are consistent with the earlier correlation analysis.  
Life expectancy is primarily driven by social and economic development factors, especially HDI and GDP.  
While environmental indicators such as CO₂ emissions are relevant at a macro level, they do not independently explain cross-country differences in life expectancy.

Overall, the machine learning analysis complements the hypothesis testing results by providing predictive evidence that human development outcomes are more closely associated with economic and social indicators than with environmental pressure alone.

---

## Tools & Environment
- **Language:** Python  
- **Libraries:** pandas, numpy, seaborn, matplotlib, scipy, plotly  
- **Environment:** Google Colab (Jupyter-based notebook)
- **Version Control:** GitHub  

---

## Ethical & AI Statement
All data sources are public and properly cited.  
AI tools were used only to improve clarity and structure, not for data manipulation or numerical analysis.  
All coding, cleaning, and statistical interpretation were conducted independently.

---

## Future Work
- Incorporating per-capita CO₂ and GDP variables for fairer comparisons.  
- Applying full panel-data methods (fixed effects) to use all years, not only 2019.  
- Adding renewable energy metrics, education indices, or carbon intensity variables.  
- Analyzing differences between OECD and non-OECD countries.  
