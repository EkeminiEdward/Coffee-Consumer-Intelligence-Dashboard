# Coffee Consumer Intelligence Dashboard

---

## ⚙️ Project Type Flags

-  Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
-  Dashboard / Data Visualization
-  Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
-  Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Data Model & Schema](#6-data-model--schema)
7. [Analysis & Metrics](#7-analysis--metrics)
8. [Key Insights](#8-key-insights)
9. [Recommendations](#9-recommendations)
10. [Assumptions & Limitations](#10-assumptions--limitations)
11. [Future Enhancements](#11-future-enhancements)
12. [Deliverables](#12-deliverables)
13. [Author](#13-author)

---

## 1. Project Overview


**Context:** Coffee has evolved beyond a daily beverage into a lifestyle product shaped by consumer preferences, purchasing behaviour, brewing habits, and perceived value. As the specialty coffee industry becomes increasingly, competitive, business require more than just sales report - they need actionable consumer intelligence to understand what drives preferences, spending, and long-term engagement.
The Coffee Consumer Intelligence Dashboard was developed to transform more than 4000 coffee taste survey responses into an executive decision-support solution. Rather than presenting descriptive statistics alone, the dashboard identifies the behavioural patterns that influence coffee consumption and purchasing decisions. Interactive filtering enables stakeholders to explore trends across different consumer segments with dynamic KPIs and narrative insights provide immediate interpretation of the findings.

**Problem Statement:** Coffee businesses collect significant amounts of consumer feedback through surveys and testing events. However, this information often exits in isolated datasets that provide limited business value without structured analysis.
As a result, stakeholders struggle to answer strategic questions such as;
-  Which coffee characteristics drive consumer preference?
-  Which brewing methods dominate current consumer preference?
-  How much are consumers willing to spend on coffee and brewing equipment?
-  Do blind taste results align with stated coffee preferences?
-  Which demographic groups represent the highest-value customer segments?

**Approach:** A structured Business Intelligence methodology was adopted to transform raw survey responses into actionable insights. Rather than focusing solely on visualization, the project followed a systematic analytical process that aligned business objectives with technical implementation. Processes such as, business understanding, data understanding, data preparation, data modelling, Exploratory Data Analysis (EDA), KPI development, dashboard development, business insight generation, and strategic recommendation development.
This structured methodology ensured that the project progressed logically from business understanding to actionable recommendations, resulting in an analytical solution that is both technically robust and strategically relevant.

**Outcome:** The completed dashboard delivers a centralized executive reporting solution that transforms complex survey data into clear, interactive, and actionable business insights. By integrating consumer preferences, blind taste evaluations, spending behaviour, and demographic segmentation into a single analytical platform, the solution enables stakeholders to quickly identify emerging trends, evaluate consumer value perception, and make informed strategic decisions based on data rather than assumptions.

---

## 2. Objectives


The primary objective of this project is to deliver an executive dashboard that converts survey responses into meaningful business insights for decision-makers. Also, the project aims to:
- Analyze consumer coffee preferences across coffee styles, roast levels, brewing methods, strength, and caffeine choices.
- Evaluate blind taste test outcomes to identify products with the strongest sensory appeal.
- Examine consumer purchasing behaviour, spending patterns, and willingness to pay.
- Understand how demographics influence coffee preferences and purchasing decision.
- Measure consumer perceptions of cafe experiences and home brewing equipment.
- Build an interactive dashboard that enables executive to monitor key consumer trends through dynamic filtering and visualization.
- Deliver actionable recommendations that support product development, pricing strategies, and customer engagement initiatives.


---

## 3. Project Scope & Tools

### Scope


| Dimension | Details |
|-----------|---------|
| **In Scope** |  Consumer demographic analysis, coffee consumption frequency and drinking locations, coffee style, roast level, strength, and caffeine preferences.  Brewing method analysis, consumer motivations for drinking coffee, spending behaviour and willingness to pay.  Coffee equipment spending and perceived equipment value.  Cafe value perception.  Blind taste test evaluation, including preference, bitterness, and acidity analysis, customer segmentation based on demographic and behavioural attributes, interactive Power BI dashboard development, and business insight generation and strategic recommendations. |
| **Out of Scope** | The dataset does not support the following analyses and they are intentionally excluded from the project:  Sales revenue analysis, profitability analysis, inventory management, customer lifetime value analysis, geographic sales performance, market share analysis, seasonal or time-series trend analysis, predictive forecasting, and customer churn analysis. |

### Tools & Technologies


| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | CSV files |
| Data Processing | Excel, Power Query |
| Analysis | DAX |
| Visualization | Power BI |
| Version Control | Git / GitHub |
| Documentation | Markdown |

---

## 4. Repository Structure

```
Coffee-Consumer-Intelligence-Dashboard/
│
├── README.md
│
├── reports/ 
│      ├──Coffee_Consumer_Intelligence_Dashboard.pbix
│
├── data
│   ├── raw/                  
│         ├── 24_Coffee_Taste_Test.csv            
│
├── visuals/                  
│      ├── Executive_Overview.png
│      ├── Coffee_Preference_Insights.png
│      ├── Blind_Taste_Insights.png
│      ├── Consumer_Behaviour.png
│      ├── Consumer_Segmentation.png
│
|___ assets
      └── Dashboard_video.mp4
      └── Data_Modelling_Architectural_Design-Coffee.png          
```
---

## 5. Data Workflow

```
[Data Source(s)]
      ↓
[Ingestion / Collection Method]
      ↓
[Cleaning & Transformation]
      ↓
[Analysis / Modelling / Querying]
      ↓
[Output / Visualisation / Reporting]
```

1. **Source:** The dataset contains a CSV file, which is a Coffee Taste testing survey dataset consisting of over 4,000 responses and 57 attributes, covering consumer demographics, coffee preferences, purchasing behaviour, blind taste evaluations, and spending patterns.
2. **Ingestion:** Loaded into Power Query. File contained approx. 4,042 rows and 57 columns.
3. **Cleaning:** Several data quality improvements were performed to ensure reliable analysis and accurate reporting, such as; data type validation, handling of missing values (such as NA, Blank, Other), standardizing categories, and removing redundancies (such as, '_other, _specify' columns). 
4. **Transformation:** Several analytical fields were created to improve reporting capabilities and enable meaningful business metrics. These fields include; Numeric spending columns - survey spending categories were originally stored as text ranges ($20-$40, $40-$60, etc.). These categories were converted into representative midpoint values to support numerical calculations such as; average monthly spend, average equipment spend, average price paid, and average willingness to pay. Cafe Value Rate originally came in as a binary Yes/No field and was transformed into a measurable KPI representing the percentage of respondents who believe cafe purchases provide good value. Same approach was applied to Equipment Value Rate. Finally, Blind Taste Comparison dataset contained two separate preference columns (preferred_abc and preferred_ad), but to support comparative analysis, these columns were unpivoted into two new fields (comparison - Blind tasting scenario, and Preferred Coffee - winning coffee selection), this transformation enabled the construction of the 100% Stacked Bar Chart that dynamically compares consumer preferences across blind tasting scenarios. 
6. **Analysis:** Descriptive statistics, Blind taste comparative analysis, Average monthly spend value, Average equipment spend value, Cafe value rating, Equipment value rating, Preferred coffee analysis, Brewing method analysis, Preferred roast level analysis, Preferred strength analysis, Coffee style preference analysis, etc.
7. **Output:** Summary report (PDF)

---

## 6. Data Model & Schema

### Dataset / Table: `Coffee_Survey_Facts`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `submission_id` | string | Unique identifier for each survey response. | EPbo6r |
| `age` | string | Respondent's age range | 25-34 years old |
| `gender` | string | Respondent's gender. | Male |
| `education_level` | string | Highest education level reported by respondent. | Bachelor's degree |
| `ethnicity_race` | string | Respondent's reported ethnicity/race category. | Asian |
| `employment_status` | string | Respondent's employment situation. | Full-time |
| `number_children` | int | Number of children reported by respondent. | 2 |
| `political_affiliation` | string | Political affiliation reported in the survey. | Independent |
| `work_from_home` | string | Work-From-Home status or frequency. | I do a mix of both |
| `cups` | int | Number of cups of coffee consumed per day. | 2 |
| `brew` | string | Primary coffee brewing method used. | Pour over |
| `primary_drinking_location` | string | Primary location where coffee is consumed. | At home |
| `strength` | string | Preferred coffee strength. | Somewhat strong |
| `style` | string | Preferred coffee style/profile. | Pourover |
| `roast_level` | string | Preferred coffee roast level. | Light |
| `caffeine` | string | Preferred caffeine level/type. | Full caffeine |
| `overall_favourite_coffee` | string | Overall preferred coffee from the blind tasting | Coffee D |
| `preferred_abc` | string | Coffee selected as preferred in the A/B/C blind comparison. | Coffee B |
| `preferred_ad` | string | Preferred coffee in the A/D blind comparison | Coffee D |
| `purchase` | string | Primary location/channel where coffee is purchased. | Local cafe |


### Dataset / Table: `Dim_Education`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `education_id` | int | Unique identifier for each education level. | 2 |
| `education_level` | string | Highest education level reported by respondent. | Bachelor's degree |


### Dataset / Table: `Dim_Age`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `age_id` | int | Unique identifier for the age range. | 1 |
| `age` | string | Respondent's age range | 25-34 years old |


### Dataset / Table: `Dim_Brewing_Method`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `brew_id` | int | Unique identifier for the particular brewing method. | 1 |
| `brew` | string | Primary coffee brewing method used. | Pour over |


### Dataset / Table: `Dim_Caffeine`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `caffeine_id` | int | Unique identifier for the particular caffeine type. | 3 |
| `caffeine` | string | Preferred caffeine level/type. | Full caffeine |


### Dataset / Table: `Dim_Coffee_Style`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `stytle_id` | int | Unique identifier for the coffee style. | 3 |
| `style` | string | Preferred coffee style/profile. | Pourover |


### Dataset / Table: `Dim_Drinking_Location`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `primary_drinking_location_id` | int | Unique identifier for the drinking location. | 7 |
| `primary_drinking_location` | string | Primary location where coffee is consumed. | At home |


### Dataset / Table: `Dim_Employment`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `employment_id` | int | Unique identifier for the each of the employment status. | 5 |
| `employment_status` | string | Respondent's employment situation. | Full-time |


### Dataset / Table: `Dim_Favourite_Coffee`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `overall_favourite_coffee_id` | int | Unique identifier for the preferred favourite coffee. | 5 |
| `overall_favourite_coffee` | string | Overall preferred coffee from the blind tasting | Coffee D |


### Dataset / Table: `Dim_Gender`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `gender_id` | int | Unique identifier for gender status. | 4 |
| `gender` | string | Respondent's gender. | Male |


### Dataset / Table: `Dim_Purchase`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `purchase_id` | int | Unique identifier for the purchase channel/location . | 4 |
| `purchase` | string | Primary location/channel where coffee is purchased. | Local cafe |


### Dataset / Table: `Dim_Roast_Level`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `roast_level_id` | int | Unique identifier for roast level type. | 2 |
| `roast_level` | string | Preferred coffee roast level. | Light |


### Dataset / Table: `Dim_Work_From_Home`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `work_from_home_id` | int | Unique identifier for Work-From-Home status. | 2 |
| `work_from_home` | string | Work-From-Home status or frequency. | I do a mix of both |


> **Row count (approx.):** 4,042 rows
> **Key join / relationship:**  `Dim_Education.education_id` → `Coffee_Survey_Facts.education_id`, `Dim_Age.age_id` → `Coffee_Survey_Facts.age_id`, `Dim_Brewing_Method.brew_id` → `Coffee_Survey_Facts.brew_id`, `Dim_Caffeine.caffeine_id` → `Coffee_Survey_Facts.caffeine_id`, `Dim_Coffee_Style.style_id` → `Coffee_Survey_Facts.style_id`, `Dim_Drinking_Location.primary_drinking_location_id` → `Coffee_Survey_Facts.primary_drinking_location_id`, `Dim_Employment.employment_id` → `Coffee_Survey_Facts.employment_id`, `Dim_Favourite_Coffee.overall_favourite_coffee_id` → `Coffee_Survey_Facts.overall_favourite_coffee_id`, `Dim_Gender.gender_id` → `Coffee_Survey_Facts.gender_id`, `Dim_Purchase.purchase_id` → `Coffee_Survey_Facts.purchase_id`, `Dim_Roast_Level.roast_level_id` → `Coffee_Survey_Facts.roast_level_id`, `Dim_Work_From_Home.work_from_home_id` → `Coffee_Survey_Facts.work_from_home_id`
(All: One-to-Many single direct relationships)

---

## 7. Analysis & Metrics


### Analytical Approach

The project followed a structured Business Intelligence workflow designed to transform raw survey responses into actionable insights. The analytical process consisted of six key stages: Business understanding, Data preparation, Data modelling, Feature engineering, Data visualization, and Business insight generation. The findings were translated into practical recommendations to support product strategy, pricing decisions, and customer engagement.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `Total Respondents` | Total number of survey participants included in the analysis. | Establishes the population represented in the analysis. |
| `Avg Cups Per Day` | Average number of coffee cups consumed daily by respondents. | Measures consumption intensity and identifies the scale of daily coffee demand. |
| `Avg Monthly Spend` | Estimated average monthly expenditure on coffee. | Provides benchmark for consumer spending and potential market value. |
| `Avg Equipment Spend` | Estimated average investment in home coffee equipment. | Measures consumers' financial commitment to home brewing. |
| `Cafe Value Rate` | Percentage of respondents answering 'Yes' to whether cafe purchases provide good value | Measures perceived value of the cafe experience and identifies potential pricing/value gaps. |
| `Equipment Value Rate` | Percentage of respondents answering 'Yes' to whether coffee equipment provides good value | Measures satisfaction with home brewing investments. |
| `Most Preferred Coffee` | Coffee style with the highest number of respondents selecting it as their favourite. | Identifies the strongest overall product preference. |
| `Most Preferred Roast` | Roast level with the highest number of selections. | Helps identify the roast profile with the strongest consumer demand. |
| `Most Preferred Brew Method` | Brewing method receiving the highest number of selections. | Identifies the dominant preparation method and potential equipment demand. |
| `Most Preferred Strength` | Coffee strength category receiving the highest number of selections. | Supports product formulation and strength positioning. |
| `Blind Taste Preference` | Coffee sample receiving the highest overall preference in the blind tasting. | Identifies the strongest product based on sensory preference rather than brand identity. |
| `Average Bitterness` | Mean bitterness rating across coffee samples. | Helps assess how bitterness relates to consumer acceptance. |
| `Average Acidity` | Mean acidity rating across coffee samples. | Helps identify acidity profiles associated with consumer preference. |

### Methods Used

- [e.g., Descriptive statistics - distribution, central tendency, outlier detection]
- [e.g., Trend analysis across [time period]]
- [e.g., Segmentation / group comparison by [dimension]]
- [e.g., Correlation analysis between [variable A] and [variable B]]
- [e.g., SQL window functions for [specific aggregation]]
- [e.g., Custom aggregation or transformation logic in [tool]]

---

## 9. Key Insights

<!--
  Findings + implications. Not just what happened - what it means.

  WHAT GOOD LOOKS LIKE:
  ✅ "Return rates, not sales volume, explain Region A's underperformance.
      Region A's return rate on home goods was 34% - more than double the
      company average. Revenue was not lost at the point of sale; it was
      lost post-sale through refunds. This points to a fulfilment or
      product quality issue specific to that region, not a demand problem."

  WHAT TO AVOID:
  ❌ "Region A had lower revenue than other regions in Q4."
     (That's an observation. It describes what happened.
      An insight says what it means and where to look next.)

  Aim for 3–6 insights. Quality over quantity.
-->

**Insight 1: [Short descriptive headline]**
[What you found + what it suggests. One short paragraph.]

**Insight 2: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 3: [Short descriptive headline]**
[What you found + what it suggests.]

**Insight 4 (if applicable): [Short descriptive headline]**
[What you found + what it suggests.]

---

## 10. Recommendations

<!--
  Action-oriented. Addressed to a real audience.
  Tied explicitly to the insight that supports each one.

  WHAT GOOD LOOKS LIKE:
  Priority: High
  Recommendation: "Conduct a fulfilment audit for home goods deliveries
                   in Region A - specifically investigating whether returns
                   correlate with a particular warehouse, carrier, or SKU batch."
  Based On: Insight 1 - return rate anomaly in Region A
  Owner: Operations / Supply Chain team

  WHAT TO AVOID:
  ❌ "Improve the return rate."
     (Not actionable. Doesn't say who, how, or where to start.)
  ❌ "Further analysis is needed."
     (This is a placeholder, not a recommendation.)
-->

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Medium | [Specific, actionable step] | [Insight it comes from] | [Who should act] |
| Low | [Exploratory or longer-term suggestion] | [Insight it comes from] | [Who should act] |

---

## 11. Assumptions & Limitations

<!--
  WHAT GOOD LOOKS LIKE:
  Assumption: "Transaction records were assumed to be complete for all five regions.
               No validation was performed against source system record counts."
  Limitation: "The analysis cannot distinguish between returns initiated by
               the customer vs. returns initiated by the business (e.g., recalls).
               If business-initiated returns are concentrated in Region A, the
               return rate finding may reflect a policy decision, not a quality issue."

  WHAT TO AVOID:
  ❌ Leaving this section blank or writing "None known."
     Every project has limitations. Documenting them is a sign of
     analytical maturity - not a confession of failure.
-->

### Assumptions
- [What did you treat as true without being able to verify?]
- [What simplifications did you make for scope or feasibility?]
- [What domain rules or definitions did you accept as given?]

### Limitations
- [What gaps exist in the data?]
- [What analysis was out of scope but could affect interpretation?]
- [What would a more rigorous version of this project include?]
- [Are there known biases in the data source or collection method?]

> *The goal here is pre-emptive Q&A. What would a thoughtful skeptic push back on? Document the answer here, before they ask.*

---

## 12. Future Enhancements

<!--
  WHAT GOOD LOOKS LIKE:
  ✅ "Automate the monthly data pull from the POS export folder using
      a scheduled Python script, replacing the current manual process."
  ✅ "Expand the return rate analysis to include carrier-level data,
      which was unavailable in this dataset but exists in the logistics system."

  WHAT TO AVOID:
  ❌ "Add a machine learning model."
     (Vague, and disconnected from the actual findings of this project.)
  ❌ Listing aspirational features that don't follow logically from the work.
-->

- [ ] [Enhancement 1 - specific and traceable to a real gap in this project]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]
- [ ] [Enhancement 4]

---

## 13. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |
| [Name] | [What it contains] | [`/path/to/file`] |

---

## 14. Author

**[Your Name]**
[Your role or title - current or target]

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 [Email - optional]

---

*Last updated: [Month YYYY]*
*If this template helped you, consider starring the repository.*
