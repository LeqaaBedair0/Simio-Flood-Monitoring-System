## Flood & Weather Monitoring System (Digital Twin)

## 📌 Project Overview
  This project is a Digital Twin developed in Simio that simulates real-time water level monitoring and flood risk assessment.By integrating external hourly weather data, the model provides a dynamic platform to visualize sensor updates, evaluate flood thresholds, and measure key performance indicators (KPIs) for emergency response planning.

## 🚀 Key Features
  Data-Driven Simulation: Bound to a CSV WeatherTable containing hourly rainfall and water-height values for three critical monitoring points.
  Automated Logic: Implements an automated "80 cm" threshold rule to trigger alert states across the system.
  Dynamic Visuals: Objects utilize conditional animation to switch between Safe (Green) and Alert (Red) states based on real-time data.
  Integrated Analytics: A comprehensive dashboard featuring Time Plots, Rainfall Histograms, and Alert Trend Lines.
  
## 🛠️ Technical Implementation
  ## Data Infrastructure
    Table Binding: External CSV data is bound to a Simio WeatherTable.
    State Variables: Uses WaterUp, WaterCenter, and WaterDown (Real) for height tracking and AlertUp, AlertCenter, and AlertDown (Integer) for status tracking.
    Sequential Indexing: An HourIndex pointer ensures synchronized data reading for each hour of the 24-hour simulation.
  ## Process Logic
    Each monitoring station (Upstream, Center, Downstream) utilizes an Add-On Process on the Entered event:
      Assign: Update current water height from the table.
      Calculate: Evaluate Math.If(WaterHeight > 80, 1, 0) to set alert status.
      Tally: Record values for peak height statistics.
      Count: Increment alert counters if the threshold is breached.
      
## 📊 Performance Results (24-Hour Run)
  The following KPIs were captured during a 100% verified simulation run:
    Metric              ,Upstream     ,Center    ,Downstream
    Peak Water Level    ,82 cm        ,85 cm     ,90 cm
    Average Water Level ,71.28 cm     ,75.75 cm  ,79.50 cm
    Alert Triggered     ,Yes (1)      ,Yes (1)    ,Yes (1)
    Alert Duration      ,25.0%        ,25.0%      ,25.0%
  Reliability: The model successfully processed 25 hourly weather updates with 100% logic accuracy.

## 📂 Repository Contents
  Model_f.spfx: The core Simio simulation project file.
  FloodDataa.csv: The hourly dataset used to drive the simulation.
  Interactive_Report.pdf: Full statistical breakdown and pivot table results.
  
## 📖 How to Run
  Open Model_f.spfx in Simio.
  Ensure Weather_Data.csv is in the same directory (or re-bind via the Data tab if prompted).
  Go to the Run ribbon and click Reset, then Play.
  Observe the dashboard charts and station color changes as the 24-hour cycle progresses.
  






  
