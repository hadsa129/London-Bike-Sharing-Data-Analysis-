# London Bike Sharing Data Analysis

## Project Overview
The **London Bike Sharing Analysis** project explores patterns, seasonality, and the impact of weather conditions on bike ride demand in London.  
This end-to-end data analytics project combines **Python for data preprocessing** and **Tableau for visualization**, providing actionable insights into how external factors influence bike-sharing trends.

**Objective:**  
To uncover trends and correlations between weather, time, and ride activity, enabling better operational planning and service optimization.

**Tools Used:**
- **Python:** Data cleaning, exploration, and transformation  
- **Pandas, NumPy, Matplotlib:** Data analysis and manipulation  
- **Tableau:** Dashboard creation and data visualization  
- **Kaggle API:** Dataset acquisition  

---

## Data Collection

**Source:** [Kaggle - London Bike Sharing Dataset](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)  
**Format:** CSV  

The dataset was downloaded via the Kaggle API and contains over **17,000 rows** and **10 columns**, providing detailed information on bike rides and weather conditions in London.

**Variables:**
| Column | Description |
|--------|--------------|
| `timestamp` | Date and time of record |
| `cnt` | Count of new bike shares |
| `t1` | Real temperature (°C) |
| `t2` | Feels-like temperature (°C) |
| `hum` | Humidity (%) |
| `wind_speed` | Wind speed (km/h) |
| `weather_code` | Weather category code |
| `is_holiday` | 1 if holiday, 0 otherwise |
| `is_weekend` | 1 if weekend, 0 otherwise |
| `season` | Meteorological season (0–3: Spring–Winter) |

**Weather Code Reference:**
1 = Clear / mostly clear  
2 = Scattered or few clouds  
3 = Broken clouds  
4 = Cloudy  
7 = Light rain / showers  
10 = Rain with thunderstorm  
26 = Snowfall  
94 = Freezing fog  

---

## Data Preprocessing (Python)

Performed with **Pandas** and **NumPy** for effective data cleaning and feature enhancement.

**Steps:**

1. **Data Loading**
   - Imported data using Pandas (`pd.read_csv()`).
   - Checked for null values and data types using `df.info()` and `df.describe()`.

2. **Feature Mapping**
   - Converted categorical numeric codes to meaningful labels:
     ```python
     season_map = {0: 'Spring', 1: 'Summer', 2: 'Fall', 3: 'Winter'}
     weather_map = {
         1: 'Clear', 2: 'Scattered Clouds', 3: 'Broken Clouds', 4: 'Cloudy',
         7: 'Light Rain', 10: 'Rain/Thunderstorm', 26: 'Snowfall', 94: 'Freezing Fog'
     }
     df['season'] = df['season'].map(season_map)
     df['weather_code'] = df['weather_code'].map(weather_map)
     ```
   - Converted humidity from numeric to percentage format.

3. **Handling Missing Data**
   - Checked for missing or inconsistent entries.
   - Replaced or dropped rows where appropriate.

4. **Data Type Conversion**
   - Converted timestamp to datetime format.
   - Ensured numeric columns were correctly typed for computation.

5. **Export for Tableau**
   - Exported the cleaned dataset to Excel for visualization:
     ```python
     df.to_excel('london_bikes_final.xlsx', index=False)
     ```

---

## Data Visualization (Tableau)

**Dashboard Components:**

- **Total Bike Rides**
  - Displays total rides over time with interactive filters.
  - Added a dynamic **moving average** to smooth fluctuations.

- **Moving Average Trends**
  - Includes user-selectable filters for:
    - Duration (e.g., 7-day, 30-day)
    - Time period (day, week, month)
  - Tooltip enriched with **temperature** and **wind speed** data.

- **Heatmap**
  - Explores the relationship between **temperature**, **wind speed**, and **total rides**.
  - Shows that the **highest ride frequency** occurs at **14.6°C** and **13.7 km/h wind**.

- **Seasonal Patterns**
  - Most rides occur in **summer months (June–August)**.
  - Lowest activity is observed during **late December**.

- **User Interaction**
  - Connected filters and slicers allow users to dynamically explore:
    - Weather impacts  
    - Seasonal trends  
    - Demand peaks by time and day  

---

##  Key Insights

- Bike rides peak during **summer** and drop significantly in **winter**.
- Most rides happen when **temperature ranges between 10–20°C** and **wind < 25 km/h**.
- **Peak hours:** 8 AM, 12 PM, and 6 PM.
- **Ride count decreases** with temperatures below 0°C or above 30°C.
- Wind speeds above 45 km/h greatly reduce ride frequency.
- Dynamic moving average and heatmap reveal **strong correlations** between weather and ride patterns.

---

## Author

**Hadil Sahraoui**  


