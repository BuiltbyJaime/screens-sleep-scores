# Screen Sleep Scores

## Project Overview

**Screen Sleep Scores** explores how smartphone usage, digital addiction, sleep behaviors, and insomnia are associated with educational outcomes.

The project uses two independent datasets. The first dataset examines smartphone usage behaviors including daily screen time, notifications, addiction level, sleep duration, and reported academic or work impact. The second dataset focuses on student sleep and insomnia, including sleep duration, sleep quality, nighttime waking, device use before bed, academic stress, and academic performance.

Because the two datasets contain different respondents, they are not matched at an individual level. Instead, standardized sleep-duration categories are used to create a shared relationship between the datasets within a relational SQLite database.

---

## Research Questions

### Main Research Question

1. How are digital habits, sleep patterns, and insomnia associated with educational outcomes?

### Smartphone Usage Dataset

1. Does higher screen time relate to higher addiction levels?
2. Is smartphone addiction associated with negative academic or work impact?
3. Do users who receive more notifications spend more time on their devices?
4. What is the gender distribution of users classified as addicted?

### Student Sleep and Educational Outcomes Dataset

1. Which sleep-related factors are associated with academic performance?
2. Does academic performance differ across sleep-duration groups?
3. Are there differences in sleep quality between genders?
4. How is device use before bed associated with academic performance?

---

## Data Sources

### Dataset 1: Smartphone Usage and Addiction Analysis

**Source:** Kaggle
**Dataset:** Smartphone Usage and Addiction Analysis Dataset

Relevant variables include:

- `daily_screen_time_hours`
- `social_media_hours`
- `gaming_hours`
- `sleep_hours`
- `notifications_per_day`
- `stress_level`
- `academic_work_impact`
- `addiction_level`
- `addicted_label`
- `gender`

Source:

https://www.kaggle.com/datasets/zahranusratt/smartphone-usage-and-addiction-analysis-dataset?select=Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv

### Dataset 2: Student Insomnia and Educational Outcomes

**Source:** Mendeley Data
**Dataset:** Student Insomnia and Educational Outcomes Dataset

Relevant variables include:

- `year_of_study`
- `gender`
- `difficulty falling asleep`
- `sleep duration`
- `nighttime waking`
- `sleep quality`
- `fatigue`
- `concentration difficulties`
- `device use before bed`
- `academic stress`
- `academic performance`

Source:

https://data.mendeley.com/datasets/5mvrx4v62z/1

---

## Data Preparation and Analysis

Python and Pandas were used to clean, transform, and analyze both datasets.

The preparation process included:

- inspecting dataset structure and data types
- identifying and handling missing values
- checking for duplicate records
- renaming columns for consistency and readability
- converting categorical variables where appropriate
- creating numerical versions of ordinal variables for analysis
- creating standardized sleep-duration categories
- performing exploratory data analysis
- creating visualizations to investigate relationships between variables

Sleep duration was standardized into three categories:

- **Under 6 hours**
- **6–8 hours**
- **Over 8 hours**

These categories were also used to establish a shared relationship between the two datasets in the relational database.

---

## Relational Database and SQL

A relational database was created using **SQLite3 and Python**.

The database contains three tables:

### `sleep_groups`

A lookup table containing standardized sleep-duration categories.

- **Primary Key:** `group_id`
- `sleep_band`

### `smartphone_usage`

Contains selected variables from the smartphone dataset.

- **Primary Key:** `user_id`
- **Foreign Key:** `group_id`

### `student_outcomes`

Contains selected variables from the student sleep dataset.

- **Primary Key:** `student_id`
- **Foreign Key:** `group_id`

The two original datasets contain different respondents and therefore cannot be directly matched by individual. Instead, both datasets connect to the `sleep_groups` table through `group_id`. This allows aggregated patterns to be compared across common sleep-duration categories without incorrectly treating respondents from the two datasets as the same individuals.

An Entity-Relationship Diagram (ERD) is included in the repository to illustrate these relationships.

The SQL analysis includes:

- joins between related tables
- grouping and aggregation
- `COUNT()` and `AVG()` calculations
- a `HAVING` clause
- `CASE` expressions
- subqueries
- cross-dataset comparison at the sleep-group level

---

## Visualizations

The notebook uses several visualization types to explore the data, including:

- box plots
- bar charts
- scatter plots
- pie charts
- heatmaps

Each visualization is accompanied by an interpretation explaining the pattern observed.

---

## Tools and Technologies

- Python
- Pandas
- Matplotlib
- Seaborn
- SQLite3
- SQL
- Jupyter Notebook

---

## Repository Structure

```text
project-folder/
│
├── Data/
│   ├── smartphone_addiction.csv
│   ├── student_educational_outcomes.csv
│   └── screens_sleep_scores.db
│
├── Notebooks/
│   └── dataset_analysis.ipynb
│
├── Database/
│   └── Entity-Relationship Diagram
│
├── requirements.txt
├── README.md
└── .gitignore
```

The notebook uses **relative paths** so that the project can run across different operating systems.

Examples:

```text
../Data/smartphone_addiction.csv
../Data/student_educational_outcomes.csv
../Data/screens_sleep_scores.db
```

---

## Project Setup

### 1. Download or Clone the Repository

Open a terminal and navigate to the project directory.

```bash
cd <project-folder>
```

### 2. Create a Virtual Environment

#### Windows

Using Command Prompt or PowerShell:

```bash
py -m venv venv
```

#### macOS / Linux

```bash
python3 -m venv venv
```

---

## Activating the Virtual Environment

### Windows — Command Prompt

```bash
venv\Scripts\activate.bat
```

### Windows — PowerShell

```powershell
.\venv\Scripts\Activate.ps1
```

### macOS / Linux

```bash
source venv/bin/activate
```

---

## Install Required Libraries

Once the virtual environment is active, install the project dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

Start Jupyter Notebook:

```bash
jupyter notebook
```

Navigate to:

```text
Notebooks/dataset_analysis.ipynb
```

Open the notebook and run the cells in order.

For final verification, restart the kernel and run all cells from beginning to end to ensure that the project executes without errors.

---

## Deactivating the Virtual Environment

When finished, deactivate the virtual environment using:

```bash
deactivate
```

This command works on Windows, macOS, and Linux once the environment is active.

---

## Key Findings

The analysis identified several patterns across the two datasets.

### Smartphone Usage and Addiction

Higher daily screen time was associated with higher smartphone addiction levels within the smartphone dataset. Users classified within higher addiction categories also frequently reported negative academic or work impact.

When smartphone behavior was compared across standardized sleep-duration groups using SQL, average daily screen time was relatively similar:

- **Under 6 hours:** 7.81 hours
- **6–8 hours:** 7.85 hours
- **Over 8 hours:** 7.97 hours

The percentage of users classified as addicted was:

- **Under 6 hours:** 77.88%
- **6–8 hours:** 79.59%
- **Over 8 hours:** 81.53%

Although the Over 8 hours group recorded the highest average screen time and addiction percentage, the differences between the sleep groups were relatively small.

### Sleep and Academic Performance

Academic performance differed across the standardized sleep groups. Using an ordinal academic performance scale in the SQL analysis, the average scores were:

- **Under 6 hours:** 2.55
- **6–8 hours:** 1.65
- **Over 8 hours:** 1.50

However, only **11 students** were included in the Under 6 hours category, compared with **447 students** in the 6–8 hours group and **333 students** in the Over 8 hours group. The higher average for the Under 6 hours group should therefore be interpreted cautiously because of the substantially smaller sample size.

### Cross-Dataset Findings

The relational database allowed aggregated smartphone and educational outcomes to be compared using standardized sleep categories.

Average smartphone screen time varied only slightly across sleep groups, while academic performance showed greater variation. Because the datasets contain different respondents, these results represent **group-level associations rather than individual-level relationships**.

The findings identify associations within the available data and should not be interpreted as evidence that smartphone use or sleep duration directly causes changes in academic performance.

---

## Limitations

Several limitations should be considered when interpreting the results:

- The datasets were collected independently and contain different respondents.
- Individuals cannot therefore be directly matched between the two datasets.
- The shared `sleep_band` variable allows comparison only at an aggregated sleep-group level.
- The Under 6 hours group in the student dataset contains substantially fewer respondents than the other sleep groups.
- Some smartphone variables showed relatively uniform distributions, which may limit how representative the observed patterns are of real-world smartphone behaviour.
- The project identifies associations rather than causal relationships.
- Self-reported sleep and academic information may be affected by reporting or recall bias.

---

## Acknowledgement of Tools and Assistance

This project was completed using Python and open-source libraries including Pandas, Matplotlib, Seaborn, Jupyter Notebook, and SQLite3.

ChatGPT was used for code generation, troubleshooting, explanations, and editing support during development of the project. The resulting code, analysis, interpretations, and project structure were reviewed as part of the development process.

---

## Sources

**Smartphone Usage and Addiction Analysis Dataset — Kaggle**

https://www.kaggle.com/datasets/zahranusratt/smartphone-usage-and-addiction-analysis-dataset?select=Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv

**Student Insomnia and Educational Outcomes Dataset — Mendeley Data**

https://data.mendeley.com/datasets/5mvrx4v62z/1
