-> COVID-19 Early Case Trend Analysis & Recovery Insights

This repository has my Machine Learning minor project.  
The project is about analyzing early COVID‑19 case data and trying a small ML model on it.

The main idea is to see who is getting infected, which regions are more impacted, and how many days patients are taking to recover.  
It is a simple project, more focused on data analysis and a basic Linear Regression model.

-> Project Objective

- Work with a real COVID‑19 patient‑level dataset.
- Try to answer:
  - Who is getting infected (age, sex, region)?
  - Which regions have more cases?
  - What does the recovery time look like for released patients?
- Build a very simple ML model to see if age can help to predict recovery time (in days).

This is not a very advanced ML work. The goal is to understand basic steps: load data, clean it, do EDA, and train one regression model.

-> Dataset

- Source: Public COVID‑19 patient dataset (given in college problem statement / PDF).
- Important columns:
  - `sex`, `birth_year`, `country`, `region`
  - `infection_reason`, `infection_order`, `infected_by`
  - `contact_number`
  - `confirmed_date`, `released_date`, `deceased_date`
  - `state` (released / isolated / deceased)

In the notebook, the dataset is loaded directly from an online CSV link using pandas.

-> Tech Stack

- Language: Python
- Libraries used:
  - `pandas` for data handling
  - `matplotlib` and `seaborn` for graphs
  - `scikit-learn` for Linear Regression and train‑test split

These are common tools for basic data analysis and ML.

-> What the notebook does

1. "Data loading & cleaning"

   - Reads the CSV file into a pandas DataFrame.
   - Converts `confirmed_date`, `released_date`, and `deceased_date` to datetime.
   - Creates an `age` column from `birth_year` (approx using year 2020).
   - Shows some basic info about the dataset.

2. "Exploratory Data Analysis (EDA)"

   - Plot of "gender distribution" of cases.
   - Plot of "age distribution" of cases.
   - Bar chart of "top 10 regions" by number of confirmed cases.
   - Basic observations written from the graphs.

3. "Recovery analysis"

   - Filters only those patients whose `state` is `released` and who have both `confirmed_date` and `released_date`.
   - Calculates a new column:

     `days_to_recovery = released_date - confirmed_date` (in days)

   - Plots the distribution of `days_to_recovery`.
   - Shows summary statistics (mean, min, max, etc.) for recovery days.

4. "Simple Machine Learning model"

   - Uses "Linear Regression" with:
     - Input feature: `age`
     - Target variable: `days_to_recovery`
   - Splits the data into training set and test set (80% / 20%).
   - Trains the model on the training set.
   - Evaluates on the test set using:
     - R² score
     - Mean Absolute Error (MAE)
   - Prints the coefficient for `age` and intercept, and small explanation is given in the report.

The model is very basic and is mainly for learning the process, not for perfect accuracy.

-> How to run

1. Download the notebook (`.ipynb`) from this repo or open it directly in Google Colab.
2. Make sure Python and these packages are available:
   - `pandas`
   - `matplotlib`
   - `seaborn`
   - `scikit-learn`
3. Run all cells in order (from top to bottom).
4. The code will:
   - Load the dataset from the URL.
   - Do cleaning and create new columns.
   - Generate all EDA plots.
   - Train and evaluate the Linear Regression model.

-> Results (short summary)

- EDA shows which gender and age groups have more confirmed cases and which regions are on top by case count.
- Recovery analysis gives an idea about average and range of recovery days for released patients.
- The Linear Regression model with only `age` as input gives a basic R² score and shows how much recovery days change when age increases by 1 year (based on the age coefficient).

-> Acknowledgements

- Problem statement and dataset idea are based on an academic COVID‑19 infectious disease case analysis task.
- This work is done as part of a Machine Learning minor project in college.

