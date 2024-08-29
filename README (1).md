# Titanic Data Analysis

This project provides a comprehensive analysis of the Titanic dataset. The analysis includes data cleaning, exploratory data analysis (EDA), and visualization of key insights.

## Project Structure

- **Dataset**: The project uses the Titanic dataset (`train.csv`).
- **Data Cleaning**: Handling missing values and preparing the dataset for analysis.
- **Exploratory Data Analysis (EDA)**: Generating descriptive statistics and visualizing data to uncover patterns and insights.

## Dependencies

The following libraries are used in this project:

- `pandas`
- `numpy`
- `seaborn`
- `matplotlib`
- `IPython.display`

You can install these libraries using pip:

```bash
pip install pandas numpy seaborn matplotlib ipython
```

## Data Loading

The dataset is loaded using `pandas`:

```python
import pandas as pd

# Load the dataset
titanic = pd.read_csv('train.csv')

# Display the first few rows of the dataset
titanic.head()
```

## Data Cleaning

### Checking for Missing Values

The dataset is checked for missing values, and appropriate steps are taken to handle them:

```python
# Check for missing values
missing_values = titanic.isnull().sum()
```

### Filling Missing Values

- Missing values in the `Age` column are filled with the median value.
- Missing values in the `Embarked` column are filled with the most frequent value (mode).
- The `Cabin` column is dropped due to a high number of missing values.

```python
# Fill missing values
titanic['Age'].fillna(titanic['Age'].median(), inplace=True)
titanic['Embarked'].fillna(titanic['Embarked'].mode()[0], inplace=True)
titanic.drop(columns=['Cabin'], inplace=True)
```

### Verifying Missing Values

After cleaning, the dataset is checked again to ensure no missing values remain:

```python
# Verify that there are no more missing values
missing_values = titanic.isnull().sum()
```

## Exploratory Data Analysis (EDA)

### Descriptive Statistics

Summary statistics of the dataset are displayed to provide an overview of the data:

```python
titanic.describe()
```

### Visualizations

Several visualizations are created to explore the data:

1. **Age Distribution**: Visualizing the distribution of passengers' ages.

    ```python
    sns.histplot(titanic['Age'], kde=True)
    plt.title('Age Distribution')
    plt.show()
    ```

2. **Fare Distribution**: Visualizing the distribution of fares.

    ```python
    sns.histplot(titanic['Fare'], kde=True)
    plt.title('Fare Distribution')
    plt.show()
    ```

3. **Survival Count**: Counting the number of survivors vs. non-survivors.

    ```python
    sns.countplot(x='Survived', data=titanic)
    plt.title('Survival Count')
    plt.show()
    ```

4. **Survival Count by Passenger Class**: Analyzing survival rates across different passenger classes.

    ```python
    sns.countplot(x='Pclass', hue='Survived', data=titanic)
    plt.title('Survival Count by Passenger Class')
    plt.show()
    ```

5. **Survival Count by Gender**: Analyzing survival rates across genders.

    ```python
    sns.countplot(x='Sex', hue='Survived', data=titanic)
    plt.title('Survival Count by Gender')
    plt.show()
    ```

6. **Correlation Heatmap**: Displaying the correlation between numerical features.

    ```python
    plt.figure(figsize=(10, 8))
    sns.heatmap(titanic.corr(numeric_only=True), annot=True, cmap='coolwarm')
    plt.title('Correlation Heatmap')
    plt.show()
    ```

## Conclusion

This project provides a clear and insightful analysis of the Titanic dataset, from data cleaning to visualization. It serves as a solid foundation for understanding the data and uncovering patterns that may influence survival rates.
