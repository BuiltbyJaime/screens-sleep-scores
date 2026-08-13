# Screen Sleep Scores

## Project Overview

This project explores patterns in screen time habits and their relationship with stress, sleep, academic impact, and digital addiction.

The dataset contains information about users' daily screen time, social media usage, gaming habits, sleep duration, stress levels, academic impact, and addiction levels.

The aim of this project is to clean, analyse, and visualise the data to identify trends and relationships between technology usage and wellbeing.

---

## Research Questions

### Main Question

1. How are digital habits, sleep patterns and insomnia associated with educational outcomes?

### Dataset 1 Questions

1. Does higher screen time relate to higher addiction levels?

2. Is screen addiction associated with negative academic impact?

3. Do users who receive more notifications spend more time on their devices?

4. What is the gender distribution of users classified as addicted?

### Dataset 2 Questions

---

## Tools Used

- Python
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Repository Contents

- `venv` - virtual enviroment
- `Notebooks` — main project notebook
- `Data` — datasets used for analysis
- `requirements.txt` — required Python libraries
- `README.md` — project overview and instructions
- `Database` - SQL Database and ERD

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

In my next anaylis I want to explore :

- Does age influence screen addiction levels?
- Which digital activity contributes most to total screen time?
- Do users with severe addiction levels open apps more frequently?

Stretch Goals:

- include a second dataset.
- plot further data to explore more questions.

Dataset 1 Source - https://www.kaggle.com/datasets/zahranusratt/smartphone-usage-and-addiction-analysis-dataset?select=Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv

Dataset 2 Source - https://data.mendeley.com/datasets/5mvrx4v62z/1
