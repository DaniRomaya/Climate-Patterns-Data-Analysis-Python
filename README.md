# Climate Change Patterns: Analyzing Temperature Trends in Michigan and the United States

## Project Overview

This project explores historical temperature patterns using NOAA (National Oceanic and Atmospheric Administration) daily weather data. The main focus is on five weather stations across Michigan to examine how temperatures have changed over time.

Using Python and data analysis techniques, this project investigates annual and seasonal temperature patterns, extreme heat days, and differences between maximum and minimum temperatures. The goal is to identify trends in the data and better understand how temperature patterns vary across different locations in Michigan.

## Research Questions

This project focuses on the following questions:

1. How have average annual temperatures changed over time?
2. Have extremely hot days become more frequent?
3. Do different locations in Michigan show different warming patterns?
4. How do average temperatures differ across the four seasons?
5. Are minimum temperatures increasing at a different rate than maximum temperatures?

## Dataset

The data comes from NOAA's Global Historical Climatology Network Daily (GHCN-Daily) dataset.

Five Michigan weather stations were selected for this analysis:

| Location | NOAA Station ID |
|---|---|
| Detroit Metro Airport | USW00094847 |
| Flint | USW00014826 |
| Grand Rapids Airport | USW00094860 |
| Lansing Airport | USW00014836 |
| Traverse City Airport | USW00014850 |

The analysis primarily uses two temperature measurements:

- **TMAX:** Daily maximum temperature.
- **TMIN:** Daily minimum temperature.

NOAA records temperature values in tenths of degrees Celsius. These values are converted to degrees Celsius during data preparation.

The original NOAA files are filtered to include only the five selected stations and the TMAX and TMIN measurements. The filtered files are then combined into one dataset for analysis.

## Tools and Technologies

- **Python:** Main programming language.
- **Pandas:** Data cleaning, transformation, and analysis.
- **NumPy:** Numerical calculations and data processing.
- **Matplotlib:** Data visualization.
- **Scikit-learn:** Linear regression modeling and evaluation.
- **Jupyter Notebook / Google Colab:** Development and analysis environment.

## Project Workflow

1. **Data Collection:** Download daily temperature records from NOAA.
2. **Data Filtering:** Select the five Michigan weather stations and TMAX/TMIN measurements.
3. **Data Cleaning:** Handle missing or invalid values, convert dates, and transform temperature measurements into degrees Celsius.
4. **Exploratory Data Analysis:** Examine annual temperatures, seasonal differences, hot days, and location-based patterns.
5. **Data Visualization:** Create charts to identify and compare temperature trends.
6. **Modeling:** Explore linear regression to measure temperature trends and compare maximum and minimum temperature changes.

## Modeling Approach

Linear regression is used to examine the relationship between year and average temperature. Separate models are explored for maximum and minimum temperatures to compare their rates of change.

Additional modeling approaches, such as polynomial regression, may be explored to determine whether temperature trends follow nonlinear patterns.

Model evaluation can include:

- **R-squared (R²):** Measures how well the model explains variation in temperature.
- **Mean Squared Error (MSE):** Measures the average squared difference between actual and predicted temperatures.
- **Regression Coefficient:** Represents the estimated temperature change per year.

## Running the Project

You can run this project using Jupyter Notebook or Google Colab.

### Option 1: If You Already Have the Filtered CSV Files

If you have already downloaded the filtered CSV files, you do not need to run the original NOAA data-filtering cells.

1. Clone or download this repository.
2. Download or obtain the filtered CSV files.
3. Place all filtered CSV files inside a folder on your computer.
4. Open the Jupyter Notebook.
5. Locate the filtered-data loading cell.
6. Update the `output_folder` variable to point to the folder containing your filtered CSV files.
7. Run the remaining notebook cells.

Example:

```python
output_folder = "C:/Users/YourName/Desktop/ClimateProject/filtered"

filtered_files = sorted(
    glob.glob(os.path.join(output_folder, "*.csv"))
)

if not filtered_files:
    raise FileNotFoundError(
        "No filtered CSV files found. Check your folder path."
    )

climate = pd.concat(
    [pd.read_csv(file) for file in filtered_files],
    ignore_index=True
)

print("Dataset shape:", climate.shape)
display(climate.head())
```

Make sure to update the folder path based on where you saved your files.

### Option 2: If You Only Have the Original NOAA Files

If you have not downloaded the filtered CSV files, you will need to:

1. Download the original NOAA yearly `.csv.gz` files.
2. Place them inside the appropriate input data directory.
3. Update the input and output folder paths in the notebook.
4. Run the data-filtering cells to generate the filtered CSV files.
5. Continue with the remaining notebook cells.

**Important:** The original NOAA data-filtering process can take some time because the yearly files contain a large amount of weather data.

## Project Structure

The project is organized approximately as follows:

```text
ClimateChangeProject/
│
├── data/
│   ├── noaa/
│   │   └── Original NOAA compressed files
│   │
│   └── filtered/
│       └── Filtered yearly CSV files
│
├── Climate_Change_Analysis.ipynb
│
└── README.md
```

Your actual folder and notebook names may differ.

## Future Improvements

Potential improvements for this project include:

- Comparing temperature trends across all five Michigan weather stations.
- Investigating whether minimum temperatures are increasing faster than maximum temperatures.
- Exploring polynomial regression to identify nonlinear temperature patterns.
- Testing models using separate training and testing periods.
- Expanding the dataset to include more historical years for a better understanding of long-term temperature changes.

## Data Source

NOAA National Centers for Environmental Information (NCEI)

[Global Historical Climatology Network Daily (GHCN-Daily)](https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily)

---

*This project was developed for educational and data analysis purposes.*
