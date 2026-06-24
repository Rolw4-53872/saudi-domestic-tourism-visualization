# Saudi Arabia Domestic Tourism Analysis & Visualization (2018-2023)

> A comprehensive data visualization project analyzing domestic tourism patterns across Saudi Arabia's provinces, exploring the factors that influence trip volume, spending behavior, and seasonal trends.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-150458?logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.0+-3F4F75?logo=plotly&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7+-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12+-4C72B0)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Project Overview

This project investigates the key factors influencing the volume of domestic tourism in Saudi Arabia from 2018 to 2023. Using a multi-dimensional visual analysis approach, the study examines temporal trends, seasonal patterns, regional distributions, travel purposes, and the relationship between spending and trip duration.

The dataset was sourced from [Kaggle](https://www.kaggle.com/) and contains monthly records of domestic tourism movements between Saudi provinces, including trip counts, tourism expenditure (SAR), nights stayed, visit purposes, and average temperatures for origin and destination regions.

Five distinct visualization types were designed following the principles of data abstraction, task abstraction, and visual encoding justification to answer the central research question:

> **What factors influence the volume of domestic tourism in Saudi Arabia from 2018 to 2023?**

---

## Business Problem

Saudi Arabia's tourism sector is a cornerstone of the **Vision 2030** economic diversification strategy. Understanding domestic travel patterns is essential for:

- **Tourism boards** to allocate marketing budgets by season and region
- **Hospitality operators** to forecast demand across provinces
- **Policy makers** to identify underserved regions and develop infrastructure
- **Airlines and transport** companies to optimize routes and capacity

This project transforms raw tourism records into actionable visual insights that reveal *when*, *where*, *why*, and *how much* Saudis travel domestically.

---

## Dataset Description

| Attribute | Type | Description |
|-----------|------|-------------|
| `year` | Temporal | Year of record (2018-2023) |
| `month` | Temporal | Month of record (1-12) |
| `trips` | Quantitative | Number of domestic trips |
| `spendSAR` | Quantitative | Tourism spending in Saudi Riyals |
| `nights` | Quantitative | Total nights stayed |
| `origin_temp` | Quantitative | Average temperature at origin province |
| `destination_temp` | Quantitative | Average temperature at destination province |
| `originProvinceNameEn` | Geographical | Name of the origin province |
| `destinationProvinceNameEn` | Geographical | Name of the destination province |
| `visitPurposeEn` | Categorical | Purpose of visit (Leisure, VFR, Religious, Business, Other) |

**Derived Attributes:**

| Field | Description |
|-------|-------------|
| `trip_volume` | Aggregated trip count per group |
| `avg_nights_per_trip` | Average nights per trip (`nights / trips`) |
| `season` | Season derived from month (Winter, Spring, Summer, Autumn) |
| `avg_destination_temp` | Mean destination temperature per region |

**Records:** Monthly tourism movement records between origin-destination province pairs

---

## Data Preprocessing

1. **Duplicate Check** - The dataset was verified for duplicate rows; none were found.
2. **Missing Value Imputation** - Missing temperature values were handled using hierarchical mean imputation:
   - Step 1: Mean by (region + month)
   - Step 2: Mean by region alone
   - Step 3: Overall mean
   
   This approach preserves regional and seasonal temperature patterns without removing any records.

---

## Methodology

The analysis follows the **Tamara Munzner visualization framework** with three layers:

### 1. Data Abstraction
- Identified attribute types (quantitative, categorical, temporal, geographical)
- Mapped data relationships (origin-destination flows, purpose-spending links)
- Defined hierarchies (Year > Month, Season > Months)

### 2. Task Abstraction
Each visualization targets a specific analytical task:
- **Analyze trends** over time
- **Identify seasonal patterns** within regions
- **Correlate** spending with trip duration
- **Compare spatial patterns** across provinces
- **Rank categories** by visit purpose

### 3. Visual Encoding Design
Each chart was designed with justified encoding choices (position, color, size, shape) and evaluated against alternative designs.

---

## Exploratory Data Analysis

### Key Analyses Performed

- **Temporal trend analysis** of total trip volume across years (2018-2023)
- **Seasonal decomposition** of trips within top regions
- **Purpose-based segmentation** of travel behavior
- **Spending vs. stay duration** correlation by visit purpose
- **Geospatial distribution** of trips with temperature overlay

---

## Visualizations

### 1. Line Chart - Annual Trip Volume Trend (2018-2023)

**Task:** Analyze change over time

Shows the total number of domestic trips per year, revealing a significant post-2020 recovery and growth trend.

| Encoding | Channel | Justification |
|----------|---------|---------------|
| Year | X-axis position | Natural temporal ordering |
| Total trips | Y-axis position | Enables year-over-year comparison |
| Trend | Continuous line | Shows progression and change direction |

**Insight:** Trip volume dropped sharply in 2020 (COVID-19 impact) then recovered strongly, exceeding pre-pandemic levels by 2023.

---

### 2. Tree Map - Seasonal Trip Distribution (Top 3 Regions)

**Task:** Identify seasonal patterns

Displays the hierarchical structure (Region > Season) with rectangle size and color encoding trip volume.

| Encoding | Channel | Justification |
|----------|---------|---------------|
| Trip volume | Rectangle size | Larger = more trips |
| Activity level | Color gradient | Darker = higher trip count |
| Hierarchy | Nested layout | Region > Season grouping |

**Insight:** Spring and Summer dominate trip activity across the top three regions, confirming seasonality as a key tourism driver.

---

### 3. Bubble Scatter Plot - Spending vs. Stay Duration

**Task:** Correlate spending with trip duration

Multi-variable analysis showing the relationship between spending (SAR) and average nights per trip, segmented by visit purpose.

| Encoding | Channel | Justification |
|----------|---------|---------------|
| Spend SAR | X-axis position | Primary quantitative variable |
| Avg nights/trip | Y-axis position | Secondary quantitative variable |
| Visit purpose | Color (Orange/Green/Blue) | Category distinction |
| Trip volume | Bubble size | Magnitude without extra space |

**Insight:** Each visit purpose exhibits a distinct spending-duration profile. Leisure trips show higher spending with moderate stays; Religious visits show concentrated patterns near holy cities.

---

### 4. Choropleth Map - Regional Trip Distribution & Temperature

**Task:** Identify spatial patterns

Geographic visualization using province polygons with color encoding for average temperature and labels for trip counts.

| Encoding | Channel | Justification |
|----------|---------|---------------|
| Location | Geographic coordinates | Real spatial positioning |
| Avg temperature | Color gradient | Climate comparison |
| Trip count | Text labels | Precise values on map |
| Province shape | Geographic polygons | Familiar regional recognition |

**Insight:** Warmer southern and western regions (Makkah, Riyadh) attract significantly more domestic trips than cooler northern provinces, suggesting climate as a contributing factor.

---

### 5. Bar Chart - Trips by Visit Purpose

**Task:** Compare and rank categories

Categorical comparison of trip volume across five visit purposes.

| Encoding | Channel | Justification |
|----------|---------|---------------|
| Visit purpose | X-axis categories | Clear categorical separation |
| Trip count | Bar height | Proportional comparison |
| Percentage | Labels | Precise share of total |

**Insight:** Leisure and VFR (Visiting Friends & Relatives) are the dominant travel purposes, collectively driving the majority of domestic tourism activity.

---

## Key Findings

1. **Post-pandemic surge** - Domestic trip volume recovered strongly after 2020, surpassing pre-pandemic levels by 2023, reflecting successful government tourism initiatives.

2. **Seasonality matters** - Spring and Summer are peak travel seasons, with trip volumes 2-3x higher than Winter and Autumn across top regions.

3. **Leisure dominates** - Leisure travel is the primary purpose, followed by VFR (social visits), together accounting for the majority of all domestic trips.

4. **Spending-duration patterns vary by purpose** - Religious tourists show shorter, more concentrated stays; Leisure travelers exhibit higher spending with moderate duration.

5. **Geographic and climate influence** - Warmer regions (Makkah, Riyadh, Eastern Province) consistently attract more domestic tourists than cooler northern provinces.

6. **Regional tourism identity** - Each province exhibits a distinctive tourism profile based on its combination of climate, attractions, and purpose-driven demand.

---

## Recommendations

1. **Seasonal marketing campaigns** - Focus tourism promotions during Spring and Summer peaks; develop off-season incentives for Winter/Autumn.

2. **Regional development** - Invest in tourism infrastructure for underperforming northern provinces to distribute demand more evenly.

3. **Purpose-targeted packages** - Design differentiated tourism products for Leisure, Religious, and VFR segments based on their distinct spending and duration profiles.

4. **Climate-adaptive tourism** - Develop indoor and climate-controlled attractions in extreme-heat regions to extend the tourism season.

5. **Data-driven forecasting** - Use the temporal and seasonal patterns identified to build predictive models for demand planning.

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Python 3.10+ | Core programming language |
| Pandas | Data manipulation and preprocessing |
| NumPy | Numerical computations |
| Matplotlib | Static visualizations |
| Seaborn | Statistical plots and heatmaps |
| Plotly Express | Interactive charts and choropleth maps |
| Folium | Geographic map rendering |
| Squarify | Tree map visualization |
| Google Colab | Development environment |

---

## Project Structure

```
saudi-domestic-tourism-visualization/
│
├── README.md                          # Project documentation
├── requirements.txt                   # Python dependencies
├── LICENSE                            # MIT License
│
├── notebooks/
│   └── saudi_tourism_analysis.ipynb   # Main analysis notebook
│
├── data/
│   └── README.md                      # Dataset source and download instructions
│
├── reports/
│   └── Data_Visualization_Final_Report.pdf   # Final project report
│
└── images/
    ├── line_chart_annual_trends.png
    ├── treemap_seasonal_patterns.png
    ├── bubble_scatter_spending.png
    ├── choropleth_map_regions.png
    └── bar_chart_visit_purpose.png
```

---

## How to Run

### Option 1: Google Colab (Recommended)
1. Open the notebook directly in Google Colab:
   
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1O9JtR55L-NAfZNJxrSV4hVX1N0ycCRWa?usp=sharing)

2. The notebook will install all required packages automatically.
3. Upload the dataset when prompted, or follow the data download instructions in `data/README.md`.

### Option 2: Local Setup
```bash
# Clone the repository
git clone https://github.com/Rolw4-53872/saudi-domestic-tourism-visualization.git
cd saudi-domestic-tourism-visualization

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook notebooks/saudi_tourism_analysis.ipynb
```

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgments

- Dataset sourced from [Kaggle](https://www.kaggle.com/)
- Visualization framework based on Tamara Munzner's *Visualization Analysis and Design*
- Built as part of a Data Visualization course project
