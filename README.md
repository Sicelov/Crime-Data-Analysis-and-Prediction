# Crime-Data-Analysis-and-Prediction

## Table of Contents

- [Overview](#overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Key Findings](#key-findings)
- [Conclusion](#conclusion)

### Overview

This data analysis (machine learning) project contains a comprehensive analysis of violent and sexual crime count data across multiple regions and categories over several years. The analysis includes data preprocessing, descriptive statistics, visualizations, and linear regression-based forecasting for the next 10 years.

The primary objectives of this analysis are to:

- **Clean and preprocess** the raw crime data by converting key variables (e.g., Year, Crime_Count) to numeric types and handling missing values.
- **Aggregate** the data by various dimensions such as Region, Subregion, Indicator, Dimension, Category, and Sex.
- **Generate descriptive statistics** that highlight critical summary metrics (mean, median, min, max) of crime counts across different groups.
- **Forecast future crime counts** using linear regression models applied independently for each subgroup with sufficient data.
- **Visualize** both historical trends and future predictions in clear, interpretable graphs, with the y-axis formatted to display full numbers (e.g., 1,700,000 instead of scientific notation).

  ![Predicted_Crime](https://github.com/user-attachments/assets/9d25003a-e665-4406-94c8-58a9ede4c4f5)



### Data Sources

Crime-Data-Analysis-and-Prediction data: The primary dataset used for this analysis is the "data_cts_violent_and_sexual_crime.xlsx" file, containing detailed information about crimes made in each region by dimensions, categories, etc, over time

### Tools

- Python
- Jupyter Notebook
- Excel

### Data Cleaning
- Loading and inspecting the data
- Handling missing values
- Data Cleaning and formatting

### Exploratory Data Analysis
- Prepare training data
- Fit a linear regression model
- Predict next 10 years
- Visualize actual data and predictions
- [Download code here](https://github.com/Sicelov/Crime-Data-Analysis-and-Prediction/blob/main/WorldCrime.ipynb)

### Data Analysis

```python
# Prepare training data
X = crime_by_year[['Year']].values
y = crime_by_year['Crime_Count'].values

# Fit a linear regression model
model = LinearRegression()
model.fit(X, y)

# Predict next 10 years (extrapolate from the maximum year from data)
max_year = int(crime_by_year['Year'].max())
future_years = np.arange(max_year+1, max_year+11).reshape(-1,1)
predictions = model.predict(future_years)

# Visualize actual data and predictions
plt.figure(figsize=(10,6))
plt.plot(crime_by_year['Year'], crime_by_year['Crime_Count'], label='Actual Crime Count', marker='o')
plt.plot(future_years.flatten(), predictions, label='Predicted Crime Count', marker='x', linestyle='--')
plt.xlabel('Year')
plt.ylabel('Crime Count')
plt.title('Crime Count Prediction for Next 10 Years')
plt.legend()
plt.grid(True)
plt.show()
```

### Key Findings

- **Regional Trends:**
  - **Americas:** Forecasted to have the highest crime counts, with projected values around or exceeding $$1,700,000$$ incidents annually.
  - **Africa:** Expected to see significant growth in certain subregions with predictions exceeding $$1,600,000$$ incidents.
  - **Europe:** Exhibits a more moderate trend, with projections remaining around $$1,400,000$$ incidents per year.
  
- **Other Dimensions:**
  - Disaggregations by Subregion, Dimension, Category, and Sex reveal important nuances. For example, some subcategories (e.g., certain street crimes) show steeper upward trends.
  - The forecasts indicate that specific localities and categories may require tailored policy interventions rather than a one-size-fits-all approach.

- **Methodology:**
  - **Data Preprocessing:** Conversion of data types and removal of incomplete records.
  - **Descriptive Analytics:** Aggregation of crime counts across multiple dimensions.
  - **Forecasting:** Linear regression was used to model historical trends and extend predictions over the next decade.
  - **Visualization:** Separate graphs were generated for each major grouping (Region, Subregion, Dimension, Sex, Category) to clearly present both past trends and future predictions.

### Conclusion

This analysis not only presents historical trends but also provides a forecasted outlook of crime counts, serving as a baseline for more advanced studies. The findings suggest that particularly the Americas and parts of Africa require close monitoring and potentially targeted interventions to address rising crime trends.

For further details, please refer to the code and accompanying visualizations in the repository.

---

*Feel free to contribute, open issues for discussions, or provide suggestions for further enhancements.*
