# Hunar-Intern_Task_1

# Data Cleaning and Preprocessing Documentation

## Overview
This Python script performs comprehensive data cleaning and preprocessing on a dataset related to food preferences and behaviors. The script handles missing values, duplicates, outliers, and prepares the data for analysis while maintaining data integrity.

## Dataset Information
- **Source File**: `food_coded.csv`
- **Original Shape**: [rows, columns] from `df.shape`
- **Data Types**: Mix of numerical (integer, float) and categorical (object) variables

## Cleaning Steps

### 1. Initial Data Inspection
- Loaded the dataset and examined:
  - First 5 rows (`df.head()`)
  - Data types of each column (`df.dtypes`)
  - Summary statistics for numerical columns (`df.describe()`)

### 2. Missing Value Analysis
- Calculated missing values count and percentage for each column
- Visualized missing values using a heatmap
- **Missing Value Strategy**:
  - For numerical columns:
    - Created mean-imputed and median-imputed versions
    - Used median imputation for final version (more robust to outliers)
  - For categorical columns:
    - Used mode imputation (most frequent value)

### 3. Duplicate Handling
- Identified and removed exact duplicate rows
- Checked for potentially duplicate columns using correlation analysis (threshold > 0.95)

### 4. Outlier Detection
- Generated boxplots for numerical columns to visually identify outliers
- Note: Outlier treatment was not applied in this script, but visualizations help identify columns that may need further processing

### 5. Data Distribution Comparison
- Created comparison histograms showing original vs. cleaned distributions for key numerical columns
- This helps validate that cleaning operations didn't significantly distort the data

### 6. Final Output
- Saved cleaned dataset as `cleaned_dataset.csv`
- Generated a summary report of all cleaning operations performed

## Key Decisions and Rationale

1. **Median Imputation for Numerical Data**:
   - Chosen over mean imputation because it's less sensitive to outliers
   - Created additional columns with both imputation methods for comparison

2. **Mode Imputation for Categorical Data**:
   - Most appropriate method for categorical variables
   - Preserves the most common category while maintaining data structure

3. **Duplicate Handling**:
   - Removed exact row duplicates completely
   - Identified but didn't automatically remove highly correlated columns (left for analyst decision)

4. **Visual Validation**:
   - Multiple visualizations ensure cleaning operations don't introduce artifacts
   - Helps maintain data integrity throughout the process

## Usage Instructions

1. Ensure required packages are installed:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

2. Update the file path in the script to point to your dataset:
   ```python
   file_path = "D:/Hunar Intern/food_coded.csv"
   ```

3. Run the script to:
   - Perform all cleaning operations
   - Generate visualizations
   - Save cleaned data
   - Produce cleaning summary

## Output Files

1. `cleaned_dataset.csv`: Final cleaned dataset
2. Multiple visualization plots displayed during execution:
   - Missing values heatmap
   - Boxplots for outlier detection
   - Distribution comparison plots

## Dependencies

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Limitations

1. **Outlier Treatment**: Only detects but doesn't automatically handle outliers
2. **High Cardinality Categorical**: Doesn't specifically handle high-cardinality categorical variables
3. **Feature Engineering**: No new features are created in this cleaning process

## Future Enhancements

1. Add automated outlier treatment options
2. Include more sophisticated categorical encoding
3. Add feature selection capabilities
4. Implement pipeline for automated processing of new data

This documentation provides a comprehensive overview of the data cleaning process, helping users understand and potentially modify the script for their specific needs.
