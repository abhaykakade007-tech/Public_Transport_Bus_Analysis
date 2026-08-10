# 🚌 Public Transport Bus Analysis

## 📌 Project Overview

Public transportation is an important part of daily life because many people depend on buses for travelling from one place to another.

This project focuses on analyzing a **Public Transport Bus dataset** using Python and Jupyter Notebook.

The dataset contains information related to buses, passengers, routes, cities, bus types, revenue, ticket prices, delays, traffic, weather, occupancy, distance and fuel consumption.

The dataset contains **2,000 rows and 25 columns**, which provides enough information for performing different types of data analysis.

The main purpose of this project is to understand passenger demand, bus performance, route performance, revenue and delays.

The complete analysis follows:

**Data → Data Cleaning → Data Manipulation → Analysis → Visualization → Findings → Conclusion**

---

# 🎯 Objectives

The main objectives of this project are:

* To understand the public transport dataset.
* To inspect the structure of the data.
* To check missing values.
* To check duplicate records.
* To clean the dataset.
* To perform data manipulation.
* To analyze passenger demand.
* To identify high-demand routes.
* To analyze bus types.
* To analyze revenue.
* To study delays.
* To analyze traffic and weather.
* To study fuel consumption.
* To analyze occupancy.
* To create different visualizations.
* To find useful insights from the data.

---

# 🚌 Why I Chose This Dataset

I chose the Public Transport Bus dataset because public transportation is a common real-world service used by many people.

Bus performance depends on several factors such as passenger demand, route distance, traffic, weather, bus type, ticket price and delays.

The dataset contains **2,000 records and 25 columns**, which gives enough information for detailed analysis.

Using this dataset, I can find which cities have the highest number of passengers, which routes have higher demand, which bus types generate more revenue and which routes may need additional buses.

I can also study delays and understand the effect of traffic and weather conditions on bus services.

This dataset helped me understand how data analysis can be used to study and improve public transportation services.

---

# 📂 Dataset Information

| Property             | Details                       |
| -------------------- | ----------------------------- |
| Dataset Name         | Public Transport Bus Analysis |
| Number of Rows       | 2,000                         |
| Number of Columns    | 25                            |
| File Format          | CSV                           |
| Programming Language | Python                        |
| Platform             | Jupyter Notebook              |
| Main Library         | Pandas                        |
| Numerical Library    | NumPy                         |
| Visualization        | Matplotlib                    |

---

# 🔎 Dataset Inspection

The dataset is first inspected to understand its structure.

```python
df.head()
```

```python
df.tail()
```

```python
df.shape
```

```python
df.columns
```

```python
df.info()
```

```python
df.describe()
```

These commands help in understanding the dataset before performing analysis.

---

# 🧹 Data Cleaning

The dataset is checked for possible data-quality problems.

The following operations are performed:

* Checking missing values.
* Checking duplicate records.
* Checking data types.
* Checking incorrect values.
* Converting the date column.
* Removing duplicate records if required.
* Sorting data.
* Filtering required data.

Example:

```python
df.isnull().sum()
```

```python
df.duplicated().sum()
```

```python
df.drop_duplicates()
```

---

# 📊 Data Manipulation

Pandas is used to manipulate the public transport data.

The following operations are performed:

* Filtering buses.
* Sorting passengers.
* Sorting revenue.
* Grouping cities.
* Grouping routes.
* Grouping bus types.
* Finding average passengers.
* Finding total passengers.
* Finding total revenue.
* Finding average delay.
* Finding maximum delay.
* Comparing bus types.

Examples:

```python
df.sort_values("Passengers", ascending=False)
```

```python
df.groupby("City")["Passengers"].sum()
```

```python
df.groupby("Route_Name")["Revenue"].sum()
```

---

# ❓ Analysis Questions

The following questions are analyzed in this project:

1. What is the total number of passengers?
2. What is the average number of passengers?
3. Which city has the highest number of passengers?
4. Which city has the lowest number of passengers?
5. Which route has the highest passenger demand?
6. Which routes may need more buses?
7. Which bus type carries the most passengers?
8. Which city generates the highest revenue?
9. Which route generates the highest revenue?
10. Which bus type generates the highest revenue?
11. What is the average ticket price?
12. Which bus type has the highest occupancy?
13. Which bus type has the highest customer rating?
14. Which city has the highest average delay?
15. Which route has the highest average delay?
16. Which traffic level causes more delay?
17. Which weather condition has more delay?
18. What is the total fuel consumption?
19. Which bus type uses more fuel?
20. What is the relationship between distance and passengers?
21. What is the relationship between passengers and revenue?
22. Which routes have high passenger demand?
23. How does passenger demand change over time?
24. How does revenue change over time?
25. How does bus delay change over time?

---

# 📈 Data Visualization

Matplotlib is used for creating different charts.

---

## 📊 1. Bar Chart — Passengers by City

```python
city_passengers = df.groupby("City")["Passengers"].sum().sort_values(ascending=False)

plt.figure(figsize=(10,5), facecolor="lightyellow")

plt.bar(city_passengers.index,
        city_passengers.values,
        color="teal")

plt.title("Total Passengers by City")
plt.xlabel("City")
plt.ylabel("Total Passengers")

plt.xticks(rotation=45)
plt.grid(axis="y", linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
```

---

## 🚌 2. Bar Chart — Top Routes by Passenger Demand

```python
route_passengers = df.groupby("Route_Name")["Passengers"].mean()

top_routes = route_passengers.sort_values(ascending=False).head(10)

plt.figure(figsize=(10,5), facecolor="lightblue")

plt.bar(top_routes.index,
        top_routes.values,
        color=["red","orange","green","blue","purple",
               "pink","teal","gold","brown","cyan"])

plt.title("Top 10 Routes Based on Passenger Demand")
plt.xlabel("Route")
plt.ylabel("Average Passengers")

plt.xticks(rotation=45)
plt.grid(axis="y", linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
```

---

## 📈 3. Line Chart — Passenger Trend

```python
df["Date"] = pd.to_datetime(df["Date"])

passenger_trend = df.groupby("Date")["Passengers"].sum()

plt.figure(figsize=(10,5), facecolor="honeydew")

plt.plot(passenger_trend.index,
         passenger_trend.values,
         color="green",
         marker="o")

plt.title("Passenger Trend Over Time")
plt.xlabel("Date")
plt.ylabel("Total Passengers")

plt.grid(True, linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
```

---

## 💰 4. Line Chart — Revenue Trend

```python
revenue_trend = df.groupby("Date")["Revenue"].sum()

plt.figure(figsize=(10,5), facecolor="lavender")

plt.plot(revenue_trend.index,
         revenue_trend.values,
         color="blue",
         marker="o")

plt.title("Revenue Trend Over Time")
plt.xlabel("Date")
plt.ylabel("Total Revenue")

plt.grid(True, linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
```

---

## ⏱️ 5. Line Chart — Delay Trend

```python
delay_trend = df.groupby("Date")["Delay_Minutes"].mean()

plt.figure(figsize=(10,5), facecolor="mistyrose")

plt.plot(delay_trend.index,
         delay_trend.values,
         color="red",
         marker="s")

plt.title("Average Bus Delay Over Time")
plt.xlabel("Date")
plt.ylabel("Average Delay (Minutes)")

plt.grid(True, linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
```

---

## 🥧 6. Pie Chart — Bus Type Distribution

```python
bus_type = df["Bus_Type"].value_counts()

plt.figure(figsize=(7,7), facecolor="lightcyan")

plt.pie(bus_type.values,
        labels=bus_type.index,
        autopct="%1.1f%%",
        startangle=90)

plt.title("Bus Type Distribution")

plt.show()
```

---

## 🥧 7. Pie Chart — Trip Status

```python
status = df["Trip_Status"].value_counts()

plt.figure(figsize=(7,7), facecolor="lavender")

plt.pie(status.values,
        labels=status.index,
        autopct="%1.1f%%",
        startangle=90)

plt.title("Trip Status Distribution")

plt.show()
```

---

## 📊 8. Histogram — Passenger Distribution

```python
plt.figure(figsize=(9,5), facecolor="beige")

plt.hist(df["Passengers"],
         bins=15,
         color="orange",
         edgecolor="black")

plt.title("Passenger Distribution")
plt.xlabel("Number of Passengers")
plt.ylabel("Frequency")

plt.show()
```

---

## 🔵 9. Scatter Plot — Distance vs Passengers

```python
plt.figure(figsize=(9,5), facecolor="lightcyan")

plt.scatter(df["Distance_km"],
            df["Passengers"],
            color="blue",
            alpha=0.6)

plt.title("Distance vs Passengers")
plt.xlabel("Distance (km)")
plt.ylabel("Passengers")

plt.grid(True, linestyle="--", alpha=0.5)

plt.show()
```

---

## 🔴 10. Scatter Plot — Distance vs Revenue

```python
plt.figure(figsize=(9,5), facecolor="mistyrose")

plt.scatter(df["Distance_km"],
            df["Revenue"],
            color="crimson",
            alpha=0.6)

plt.title("Distance vs Revenue")
plt.xlabel("Distance (km)")
plt.ylabel("Revenue")

plt.grid(True, linestyle="--", alpha=0.5)

plt.show()
```

---

# 💡 Key Findings

The analysis helps to identify:

* The city with the highest passenger demand.
* The most popular routes.
* Routes that may require additional buses.
* Bus types carrying more passengers.
* Cities generating higher revenue.
* Routes generating higher revenue.
* Bus types generating higher revenue.
* Cities with higher delays.
* Routes with higher delays.
* The effect of traffic on delays.
* The effect of weather on delays.
* Bus occupancy levels.
* Fuel consumption.
* Passenger trends over time.
* Revenue trends over time.

The exact findings are obtained from the calculations and visualizations in the Jupyter Notebook.

---

# 🚌 Route Demand Analysis

One important part of the project is identifying routes that may need more buses.

The average passenger demand of each route is calculated.

```python
route_passengers = df.groupby("Route_Name")["Passengers"].mean()

print(route_passengers.sort_values(ascending=False))
```

The routes with consistently high passenger demand can be considered high-demand routes.

These routes may need additional buses, especially during busy periods.

---

# 🏙️ City Passenger Analysis

The total passengers are calculated for each city.

```python
city_passengers = df.groupby("City")["Passengers"].sum()

print(city_passengers.sort_values(ascending=False))
```

The city with the highest passenger count represents the city with the highest passenger demand in the dataset.

---

# ⏱️ Delay Analysis

Delay is an important part of public transportation.

The project analyzes:

* Average delay.
* Maximum delay.
* Delay by city.
* Delay by route.
* Delay by traffic level.
* Delay by weather condition.

Example:

```python
traffic_delay = df.groupby("Traffic_Level")["Delay_Minutes"].mean()

print(traffic_delay)
```

---

# ⛽ Fuel Analysis

Fuel consumption is also analyzed to understand bus operating performance.

```python
fuel = df.groupby("Bus_Type")["Fuel_Consumption_Liters"].mean()

print(fuel)
```

This helps compare the average fuel consumption of different bus types.

---

# 💡 Important Insights

The project helps convert raw public transport data into useful information.

For example:

* High passenger demand indicates a popular route.
* High-demand routes may require additional buses.
* High delays may indicate traffic or operational problems.
* Higher occupancy may indicate that buses are being used efficiently.
* Revenue analysis helps identify financially successful routes.
* Fuel analysis helps compare operating requirements of different buses.

---

# 🧠 What I Learned

Through this project, I learned:

* How to load CSV files.
* How to inspect datasets.
* How to check missing values.
* How to identify duplicates.
* How to clean data.
* How to filter records.
* How to sort data.
* How to use GroupBy.
* How to calculate averages.
* How to calculate totals.
* How to find maximum and minimum values.
* How to analyze transportation data.
* How to create different charts.
* How to interpret graphs.
* How to write observations.

---

# 🛠️ Technologies Used

### Python

Used as the main programming language.

### Pandas

Used for data cleaning, manipulation and analysis.

### NumPy

Used for numerical operations.

### Matplotlib

Used for data visualization.

### Jupyter Notebook

Used for performing and documenting the analysis.

---

# 📁 Project Structure

```text
Public-Transport-Bus-Analysis/
│
├── Public_Transport_Bus_Analysis.csv
├── Public_Transport_Analysis.ipynb
└── README.md
```

---

# 🔄 Data Analysis Workflow

```text
Raw Dataset
     ↓
Load Dataset
     ↓
Inspect Dataset
     ↓
Data Cleaning
     ↓
Data Manipulation
     ↓
Exploratory Data Analysis
     ↓
Data Visualization
     ↓
Observations
     ↓
Insights
     ↓
Conclusion
```

---

# 📊 Charts Used

The following charts are used in this project:

| Chart        | Purpose                             |
| ------------ | ----------------------------------- |
| Bar Chart    | City and route comparison           |
| Line Chart   | Passenger, revenue and delay trends |
| Pie Chart    | Bus and trip distribution           |
| Histogram    | Passenger distribution              |
| Scatter Plot | Distance and passenger relationship |
| Scatter Plot | Distance and revenue relationship   |

---

# 🎓 Skills Demonstrated

### Python

* Basic Python
* Data handling
* Calculations

### Pandas

* DataFrame
* CSV handling
* Filtering
* Sorting
* GroupBy
* Aggregation

### NumPy

* Numerical operations
* Mathematical calculations

### Matplotlib

* Bar charts
* Line charts
* Pie charts
* Histograms
* Scatter plots

### Data Analytics

* Data cleaning
* Data manipulation
* Exploratory Data Analysis
* Trend analysis
* Comparison
* Visualization
* Interpretation

---

# 🚀 How to Run

### 1. Install Python

Make sure Python is installed.

### 2. Install Required Libraries

```bash
pip install pandas numpy matplotlib jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open the Notebook

Open:

```text
Public_Transport_Analysis.ipynb
```

### 5. Keep the Dataset in the Same Folder

Make sure:

```text
Public_Transport_Bus_Analysis.csv
```

and the Jupyter Notebook are in the correct folder.

### 6. Run the Cells

Run the notebook cells from beginning to end.

---

# 📌 Dataset Details

**Rows:** 2,000

**Columns:** 25

**File Format:** CSV

**Project Type:** Data Analytics Mini Project

**Analysis Platform:** Jupyter Notebook

---

# 🏁 Conclusion

The Public Transport Bus Analysis project helped me understand how Python can be used to analyze transportation data.

By using Pandas, NumPy and Matplotlib, I was able to clean and manipulate the dataset and perform different types of analysis.

The project provides information about passenger demand, cities, routes, bus types, revenue, delays, occupancy, traffic, weather and fuel consumption.

The analysis can help identify high-demand routes and understand areas where public transport services may need improvement.

Overall, this project gave me practical experience in the complete data analytics process, from loading raw data to creating visualizations and drawing conclusions.

The visualizations make the analyzed information easier to understand and help in identifying important differences and trends in the transportation system.

The insights obtained from the analysis can be useful for understanding passenger requirements and evaluating bus route usage

---

# 👨‍💻 Author

**Abhay Kakade**

Aspiring Data Analyst | Python | Pandas | NumPy | Matplotlib

This project demonstrates practical skills in Python-based data analysis and visualization.

# 🏁 Project Status
Completed ✅

Project Type: Data Analysis

Environment: Jupyter Notebook
