# NYC Traffic Accidents (Jan-Aug 2020)

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?logo=microsoftexcel&logoColor=white)

The project was developed to practice end-to-end data analysis using real-world open data. It applies Excel-based analytics to identify trends, patterns, and potential risk factors in NYC motor vehicle collisions reported  between January and August 2020.


## Skills Demonstrated
- **Data cleaning and wrangling** in Excel (formatting, handling missing values).  
- Feature engineering using **formulas** and **helper columns**.  
- Aggregation and analysis with **Pivot Tables** and **conditional formatting**.  
- **Visualization** with combo charts, bar charts, and heatmaps.  
- Analytical storytelling and insight communication through data.  

## Dataset

**Source**: [NYC OpenData](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95) - Motor Vehicle Collisions  
**Format**: CSV  
**Rows:** 74,881  
**Columns:** 29  
**Time Period:** January - August 2020  
**Features include:** date/time, location (borough, zip code, lat/lon), street names, vehicles involved, injuries/fatalities, contributing factors

## Data Cleaning & Preparation
1. Used `=ROWS()` and `=COLUMNS()` to check dataset size.
2. Used `Filter` to identify and `=COUNTBLANK()` to measure missing values.
3. Removed columns with 90%+ missing values (Vehicle Type 3–5, Contributing factor 3-5).
4. Standardized column formats:
  - Dates → `Date` format
  - Times → `Time` format
  - Borough, ZIP codes, street names, collision IDs, contributing factors, vehicle types → `Text`
  - Lat/Lon → `Number (6 decimals)`
  - Number of kills/injures  → `Number (no decimals)`.
5. Created **helper columns**:
  - Month, Month Name, Day of Week, Is Fatal (True/False) : `Text`
  - Hour: `Number`
6. Verified completeness and ensured date range: January – August 2020.

## Analysis & Insights

### 1. Monthly Trends

#### Approach

Created a **Combo Chart (Column + Line)** using a **Pivot Table** to display both **total collisions** (absolute counts) and **percentages of total and fatal accidents** (proportional trends on a secondary axis), aggregated by month. Visualized the relationship between accident **volume** and **severity** over time.

<img src="./visuals/total_by_month.jpg" width="600" />

#### Analysis

- Accident frequency was highest in **January** and **February**, then dropped sharply to its lowest point in **April** - aligning with NYC's early COVID-19 lockdown period.
- Collisions began rising again from **May** onward, reaching a secondary peak in **July** and stabilizing in **August** as mobility resumed.
- The percentage of **total accidents** mirrored this pattern, showing a significant dip in **April** before recovering mid-year.
- The percentage of **fatal accidents** increased notably in **June**, even though total crash volume remained moderate - suggesting that fewer **collisions during this period were more severe**.

#### Insights
- Traffic volume declined during lockdown months, but the higher fatality rate in early summer indicates riskier driving behavior during periods of lighter traffic.

### 2. Day-Hour Patterns

#### Approach

Summarized collision frequency and severity by day and hour.  
Visualized overall volume trends across 24 hours.  
Combined **line and radar charts** to effectively capture both **trend shape** and **circular daily rhythm**.

#### Analysis


##### Heatmap: Accidents Hotspots by Day × Hour
<img src="./visuals/total_by_day_of_week_heatmap.jpg" />

- Collision activity is **lowest overnight (1-5 AM)** across all days.
- A strong **morning peak at 8 AM** appears Monday-Friday, weekends don't exhibit the same 8 AM spike.
- The **highest sustained activity** occurs during **2–5 PM** on all days.
- **Friday** shows the **highest afternoon/evening counts**.
- **Weekend early mornings (12–3 AM)** show significantly higher collisions than weekdays.
- **Weekday mornings (7–9 AM)** are markedly busier than weekends.
- All days show a consistent **afternoon rise starting at 11 AM** that **peaks between 2–5 PM**.

##### Accidents Hourly

<img src="./visuals/total_by_hour.jpg" width="50%" />
<div>
  <img src="./visuals/avg_by_hour.jpg" width="50%" />
  <img src="./visuals/avg_by_hour_radar.jpg" width="40%" />
</div>

- **Collisions are lowest at 2–5 AM**, with the absolute minimum around 4 AM.
- **Sharp increase after 6 AM**, leading to a **strong 8 AM peak** on weekdays, but not weekends.
- Midday: consistently active (9 AM - 1 PM).
- Highest overall collisions occur between **2–5 PM**, with **4 PM** peak hour.
- Evenings: steady decline after **6 PM**.
- Weekends exceed weekdays only during the evening-night hours **(8 PM–5 AM)**; for all other hours of the day, weekday collisions are consistently higher.


##### Total Accidents by Day of Week
<img src="./visuals/total_by_day_of_week.jpg" width="600" />

- **Friday has the highest number of collisions**.
- **Sunday has the lowest total collisions**.
- The **% of fatal accidents** line diverges from total volume, indicating that severity is not purely a function of how many crashes occur.
- **Sunday, Tuesday, and Saturday** all show **higher share of fatal crashes** than their total collision share would suggest.
- **Friday**, despite having the most collisions, shows a more moderate fatal-share.

#### Insights
- The city's collision "heartbeat" is classic urban: low at night, sharp morning spike, sustained afternoon peak, tapering into the evening.
- Nightlife and late-night travel make weekend early mornings riskier than weekday early mornings.
- Weekday afternoon/early evening, especially Thursday and Friday, is the most collision-dense period of the week.
- **Volume risk** is highest on Fridays - more crashes happen.
- **Severity risk** is higher on Sunday, Tuesday, and Saturday - crashes are more likely to be fatal.

### 3. High-Risk Locations

#### Approach

Used a **PivotTable** to group collisions by **ON STREET NAME**.  
Calculated **total collisions** and **% of all collisions** for each street.  
Sorted in descending order and extracted the Top 10 streets for visualization.  
Created a **horizontal bar chart** to highlight the share each location contributes to the citywide total.  

A second PivotTable with a filter `IS FATAL = TRUE` was also created; however, fatal collisions are rare and highly dispersed across locations, resulting in an uninformative Top 10 (mostly 1 fatal crash per street).  
For this reason, **severity patterns are not meaningful by street**.

<div>
  <img src="./visuals/by_location_pivottable.jpg" width="33%" />
  <img src="./visuals/top10_by_location.jpg" width="65%;" />
</div>

#### Analysis

- **Van Wyck Expressway** is the clear **outlier**, responsible for **3.77%** of all citywide collisions - nearly twice as much as the next street.  
- The remaining top streets form a tighter **cluster** around **1.3%-2.0%**.  


#### Insights

- **Van Wyck Expressway dominates collision activity**, accounting for nearly 4% of all crashes on its own. As one of NYC’s busiest expressways feeding JFK Airport, heavy traffic flow, high speeds, and constant merging create a perfect environment for frequent collisions.
- **Queens Boulevard** - often referred to historically as the “Boulevard of Death” - appears near the top of the list. Despite years of safety redesigns, its length, complex intersections, and multi-lane structure continue to generate a high collision load.
- **Rockaway Boulevard and Utica Avenue** serve as major commercial and transit corridors in dense neighborhoods. Their elevated collision percentages reflect constant mixed-use activity: buses, delivery trucks, pedestrians, local traffic, and limited protected infrastructure.
- The pattern across all streets makes one theme clear:  
**Collisions concentrate on long, fast, heavily traveled corridors where driver pressure, lane complexity, and traffic intensity overlap.**
- **Fatal** crashes, on the other hand, are **too dispersed** geographically to identify a clear pattern. This suggests that **severity is more influenced by behavior (speed, impairment, distraction)** than by specific street geometry.

### 4. Contributing factors

#### Approach

Analyzed **why collisions occur, what makes them fatal, and who is most affected**, using **treemaps** for the top causes, a comparison of vehicle types involved in all vs. fatal crashes, and **pie charts** showing the distribution of injuries and fatalities among motorists, pedestrians, and cyclists. 

#### Analysis

##### Causes of All Collisions

<img src="./visuals/top10_causes_of_all.jpg" width="600" />

- **Driver Inattention/Distraction (34.7%)** is the dominant cause of collisions, far outweighing all others.
- **Following Too Closely (9.4%)** and **Failure to Yield Right-of-Way (8.7%)** reflect congestion-driven, everyday driving mistakes.
- Improper maneuvers - **Passing Improperly, Unsafe Lane Changes, Backing Unsafely** - collectively form a significant share of crashes.
- Overall, most collisions stem from **routine driving behavior errors**, not extreme driving.

##### Causes of Fatal Collisions

<img src="./visuals/top10_causes_of_fatal.jpg" width="600" />

- **Unsafe Speed (32%)** becomes the leading cause of fatal crashes, despite its small share of total crashes.
- **Traffic Control Disregarded (14.6%)** and **Failure to Yield (9.7%)** highlight the danger of violations at intersections.
- **Driver Inattention (12.6%)** remains a major contributor, but is overshadowed by speed-driven severity.
- Fatal causes shift from **common errors** to **high-risk behaviors** like speeding and signal violations.

##### Vehicles Most Involved

<img src="./visuals/most_involved_vehicle_types.jpg" width="600" />

- **Sedans and SUVs** dominate crash involvement due to road presence, but their fatal shares are **lower** than their total shares.
- **Pick-up trucks, box trucks, and buses** show **higher fatal involvement relative to their total share**, linked to size and impact force.

##### Injured/Killed

<div>
  <img src="./visuals/injured_pie.jpg" width="49%" />
  <img src="./visuals/killed_pie.jpg" width="49%;" />
</div>

- Motorists are the majority of road users, so they accumulate most injuries.
- Pedestrians' fatality share is more than 2.5× their injury share.
- Cyclists are frequently injured but less represented in fatalities.

#### Insights

- The factors driving collision **frequency** differ from those driving collision **severity**. Everyday mistakes create most crashes, but speed and traffic violations create the deadliest ones.
- **Vehicle mass/size amplifies severity** - heavier vehicles (buses) produce more fatal outcomes relative to their low crash frequency, while common smaller vehicles (sedans, SUVs) dominate volume but not severity.
- **Pedestrians are the most at-risk group**, with a fatality share far exceeding their injury share - crashes involving pedestrians are significantly more lethal.
- **Cyclists' lower fatality share compared to injuries** suggests that lower-speed conditions or protected infrastructure help prevent fatal outcomes.
