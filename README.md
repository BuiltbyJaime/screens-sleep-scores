# Screen Sleep Scores

## Project Overview

This project explores how smartphone usage and sleep-related behaviours are associated with digital addiction and academic outcomes. Using two datasets, the analysis will first examine relationships between screen time, smartphone addiction, notifications, academic impact, and gender. It will then investigate how sleep factors such as sleep quality, insomnia symptoms, sleep duration, and nighttime waking are associated with students' academic performance, including whether these patterns differ by gender. Together, the datasets will provide insight into how digital habits and sleep behaviours may relate to educational outcomes.

---

## Research Questions

### Main Question

1. How are digital habits, sleep patterns and insomnia associated with educational outcomes?

### Dataset 1 Questions

1. Does higher screen time relate to higher addiction levels?

2. Is screen addiction associated with negative academic impact?

3. Do users who receive more notifications spend more time on their devices?

4. What is the gender distribution of users classified as addicted?

### Dataset 2 Question

1. Which sleep factors affect academic performance the most?

2. What is the Gender most affected by sleep quality.

---

## Tools Used

- Python
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Repository Contents

- `venv` - Virtual enviroment
- `Notebooks` — Main project notebook
- `Data` — Datasets used for analysis
- `requirements.txt` — Required Python libraries
- `README.md` — Project overview and instructions
- `Database` - SQL Database and ERD

- Relative Paths

  Dataset 1 : - "../Data/smartphone_addiction.csv"
  Dataset 2 : - "../Data/student_educational_outcomes.csv"

---

## Running the Project

Install the required libraries:

```bash
pip install -r requirements.txt
```

Then launch Jupyter Notebook:

```bash
jupyter notebook
```

## Key Findings

The analysis suggests that higher screen time is associated with higher addiction levels. Users with moderate and severe addiction levels also appeared more likely to report academic impact.

Some variables within the dataset showed low variance and unusually uniform distributions, suggesting the data is likely artificially generated rather than fully representative of real-world behaviour.

-

### Acknowledgement of Tools

Throughout the project I used ChatGPT for code generation and editing support.

### Sources

Dataset 1 Source - https://www.kaggle.com/datasets/zahranusratt/smartphone-usage-and-addiction-analysis-dataset?select=Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv

Dataset 2 Source - https://data.mendeley.com/datasets/5mvrx4v62z/1

Custom Functions

Function 1:

```python
addiction_scale = {
    'None': 0,
    'Mild': 1,
    'Moderate': 2,
    'Severe': 3
}

df['addiction_level_numeric'] = df['addiction_level'].map(addiction_scale)
df[['addiction_level', 'addiction_level_numeric']].head()
```

In this function I changed the value of the addiction scales so that the values can be charted with numerical values rather than categorical ones.

Function 2:

```python

def category_summary(dataframe, column=None):

    if column is not None:
        counts = dataframe[column].value_counts(dropna=False)

        percentages = (
            dataframe[column]
            .value_counts(normalize=True, dropna=False)
            .mul(100)
            .round(1)
        )

        return pd.DataFrame({
            "count": counts,
            "percentage": percentages
        })

    else:
        summaries = {}

        for col in dataframe.columns:
            counts = dataframe[col].value_counts(dropna=False)

            percentages = (
                dataframe[col]
                .value_counts(normalize=True, dropna=False)
                .mul(100)
                .round(1)
            )

            summaries[col] = pd.DataFrame({
                "count": counts,
                "percentage": percentages
            })

        return summaries
```

In this function, if you specify a column, it summarizes only that column
if you don't specify a column, it uses a for loop to summarize every column.

Fucnti
