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
> **Key join / relationship:**  `Dim_Education.education_id` → `Coffee_Survey_Facts.education_id`, `Dim_Age.age_id` → `Coffee_Survey_Facts.age_id`, `Dim_Brewing_Method.brew_id` → `Coffee_Survey_Facts.brew_id`, `Dim_Caffeine.caffeine_id` → `Coffee_Survey_Facts.caffeine_id`, `Dim_Coffee_Style.style_id` → `Coffee_Survey_Facts.style_id`, `Dim_Drinking_Location.primary_drinking_location_id` → `Coffee_Survey_Facts.primary_drinking_location_id`, `Dim_Employment.employment_id` → `Coffee_Survey_Facts.employment_id`, `Dim_Favourite_Coffee.overall_favourite_coffee_id` → `Coffee_Survey_Facts.overall_favourite_coffee_id`, `Dim_Gender.gender_id` → `Coffee_Survey_Facts.gender_id`, `Dim_Purchase.purchase_id` → `Coffee_Survey_Facts.purchase_id`, `Dim_Roast_Level.roast_level_id` → `Coffee_Survey_Facts.roast_level_id`, `Dim_Work_From_Home.work_from_home_id` → `Coffee_Survey_Facts.work_from_home_id` (All: One-to-Many Single Direction Relationships)

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

- Data Cleaning and Transformation (Power Query ETL).
- Created a Dimensional Data Model (Star Schema).
- Interactive Data Visualization and Executive Dashboard Design
- Descriptive statistics - distribution analysis, comparative data analysis.
- DAX Measure Development.

---

## 8. Key Insights


**Insight 1: The consumer base is dominated by young adults.**
The 25-34-year age group represents the largest share of respondents, indicating that young professionals form the core audience within the survey population.

**Insight 2: Coffee consumption is part of the daily routine.**
Respondents consume an average of 3 cups of coffee per day, demonstrating that coffee is integrated into everyday lifestyles rather than being an occasional purchase.

**Insight 3: Coffee is primarily consumed at home.**
Home remains the dominant drinking location, reflecting the continued importance of home brewing equipment, convenience, and flexible working arrangements.

**Insight 4: Coffee D achieved the strongest overall blind preference.**
Without brand influence, Coffee D received the highest number of consumer selections, demonstrating superior sensory appeal.

**Insight 5: Blind tasting reveals differences between stated preference and actual experience.**
The blind taste experiment shows that consumers may choose different products when branding and prior expectations are removed, reinforcing the importance of sensory testing during product development.

**Insight 6: Most consumers spend between $20 - $60 per month on coffee.**
The largest respondent segments fall within moderate monthly spending ranges, suggesting a stable consumer market with predictable purchasing behaviour.

**Insight 7: Local cafes remain an important purchasing channel.**
Despite the growth of homebrewing, consumers continue purchasing coffee from cafes, supporting the importance of physical retail experiences.

**Insight 8: Hybrid work has influenced coffee consumption habits.**
A considerable proportion of the respondents combine home and office work, creating demand for products suited to both environments.

**Insight 9: Bachelor's degree holders represent the largest educational segment.**
The survey population is largely composed of university-educated consumers, suggesting relatively high levels of product awareness and purchasing confidence.

**Insight 10: The survey reflects a diverse consumer population.**
Variation across ethnicity, education, employment, and household characteristics demonstrates that coffee consumption spans multiple demographic segments, reinforcing the need for broad yet targeted marketing strategies.

**Insight 11: Pourover is the most preferred coffee style.**
Pourover emerged as the leading coffee style, indicating growing consumer appreciation for specialty brewing methods that emphasize flavour clarity and quality.

---

## 9. Recommendations

| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Prioritize the young professional market: Develop products, loyalty programs, and digital marketing campaigns that resonate with consumers aged 25-34, who represent the largest segment of the survey. | From Insight 1 - The consumer base is dominated by young adults. | Executives |
| High | Continue Blind Taste Validation: Incorporate regular blind taste testing into product development to ensure new products succeed based on flaour quality rather than brand perception alone | from Insight 5 - Blind tasting reveals differences between stated preference and actual experience. | Executives |
| Medium | Develop Segment-Specific Marketing: Use demographic insights such as age, education, employment status, and household composition to personalize marketing messages and product recommendations. | From Insight 10 - The survey reflects a diverse consumer population. | Executives |
| Medium | Promote Everyday Coffee Rituals: Since coffee is primarily consumed at home and forms part of consumers' daily routines, position products around convenience, consistency, and quality to strengthen long-term customer engagement. | From Insights 2 & 3 - Coffee consumption is part of the daily routine, and Coffee is primarily consumed at home. | Executives |
| Medium | Align Pricing with Consumer Expectations: Introduce tiered pricing strategies that accommodates both valued-conscious consumers and those willing to pay premium prices for higher-quality coffee experiences, | From Insight 6 - Most consumers spend between $20 - $60 per month on coffee. | Executives |
| High | Expand Specialty Coffee Offerings: Increase investment in Pourover products and the light roast selections, as these align closely with current consumer  preferences. | From Insight 11 - Pourover is the most preferred coffee style. | Executives |

---

## 10. Assumptions & Limitations

### Assumptions
- Survey responses accurately represent each participant's coffee consumption behaviour, purchasing habits, and personal preferences.
- Respondents answered all survey questions honestly without intentional bias or misrepresentation.
- The numerical midpoint values assigned to spending ranges (e.g., $20-$40 'n $30) reasonably represent average consumer expenditure for analytical puposes.
- Blind taste evaluations reflect genuine sensory preferences since respondents were unaware of the coffee identities during assessment.
- Survey responses are independent observations, with each  submission representing a unique participant.
- Consumer preferences captured in the survey remain sufficiently stable to support strategic business decision-making within the reporting period.

### Limitations
- Geographic Representation: The survey does not necessarily represent coffee consumers across all countries or regions. Consumer behaviour may vary significantly between different markets.
- Self-Reported Responses: Behavioural data is based on participant self-reporting and may be influenced by recall bias or personal perception.
- Spending Estimates: Monthly spending, willingness to pay, and equipment investment were converted from categorical ranges into representative midpoint values. While this enables numerical analysis, the resulting averages are estimates rather than exact monetary values.
- Cross-Sectional Dataset: The survey represents a single period in time and therefore cannot measure changes in consumer behaviour over multiple years.
- Brand Availability: Blind taste results evaluate sensory preference only and do not account for product availability, pricing, marketing influence, or brand loyalty.


---

## 11. Future Enhancements

-  Predictive Analysis: Develop machine learning models to predict; consumer spending behaviour, product preference, purchase likelihood, and customer lifetime value.
-  Customer Segmentation: Apply clustering algorithms to identify distinct consumer personas based on purchasing behaviour, demographics, and coffee preferences.
-  Geographic Intelligence: Integrate geographic data to visualize regional coffee preferences using interactive maps.
-  Time-Series Analysis: Incorporate historical survey data to monitor changes in consumer behaviour over time.
-  Sentiment Analysis: Analyze open-ended survey responses using Natural Language Processing (NLP) to uncover additional consumer insights.
-  Real-Time Reporting: Connect the dashboard to live survey platforms or cloud databases to enable continuous monitoring of consumer preferences.

---

## 12. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| Executive Overview Page | High-level KPIs insights and consumer snapshot. | `/visuals/executive_Overview.png` |
| Coffee Preference Insights Page | Preferences for coffee style, roast, brew method, and strength. | `/visuals/Coffee_Preference_Insights.png` |
| Blind Taste Insights Page | Comparative analysis of blind tasting results and sensory scores. | `/visuals/Blind_Taste_Insights.png` |
| Consumer Behaviour Page | Spending patterns, purchasing habits, expertise, and value perception. | `/visuals/Consumer_Behaviour.png` |
| Consumer Segmentation Page | Demographic profiling and market segmentation. | `/visuals/Consumer_Sementation.png` |
| Dashboard Short Video | A short video on the interactive state of the dashboard. | `/assets/Dashboard_video.mp4` |
| Data Modelling Architectural Design | A Star Schema model | `/assets/Data_Modelling_Architectural_Design-coffee.png` |

---

## 13. Author

**Ekemini Edward**
Data Analyst

- 🔗 [LinkedIn URL]
- 💼 [Portfolio or GitHub profile URL]
- 📧 edyswagg@gmail.com

---

*Last updated: August, 2026*

