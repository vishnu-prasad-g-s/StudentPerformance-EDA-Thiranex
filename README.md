# 🎓 Student Performance — Exploratory Data Analysis
### Personal Data Science Project — EDA & Statistical Analysis

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-1.3+-150458?style=flat-square&logo=pandas)
![SciPy](https://img.shields.io/badge/SciPy-1.7+-8CAAE6?style=flat-square&logo=scipy)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4+-11557C?style=flat-square)
![Seaborn](https://img.shields.io/badge/Seaborn-0.11+-4C72B0?style=flat-square)
![Kaggle](https://img.shields.io/badge/Notebook-Kaggle-20BEFF?style=flat-square&logo=kaggle)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)

---

## 📌 Objective

Explore a student performance dataset to uncover **patterns, correlations, and key influencing factors** behind academic scores. The goal is to move beyond simple visualization into **statistically validated insight** — identifying which behavioral and demographic factors most strongly predict student success.

---

## 📂 Dataset

| Property | Details |
|---|---|
| **Name** | Student Performance Dataset (Synthetic) |
| **Type** | Simulated / Generated |
| **Rows** | 800 students (808 raw with injected issues) |
| **Features** | 12 input features + 1 derived target |
| **Target** | `average_score` — mean of math, reading, writing scores |
| **Score Range** | 24.7 – 100 |
| **Average Score** | 68.3 |
| **Missing Values** | Yes — injected into study_hours, sleep_hours |
| **Data Types** | Mixed — int, float, object |

### Feature Description

| Feature | Type | Description |
|---|---|---|
| `gender` | object | Male / Female |
| `age` | int | Student age (15–18) |
| `parental_education` | object | High School, Bachelors, Masters, PhD |
| `lunch` | object | Standard or Free/Reduced |
| `study_group` | object | Whether the student attends a study group |
| `extracurricular` | object | Participation in extracurricular activities |
| `study_hours` | float | Weekly study hours |
| `attendance_pct` | float | Class attendance percentage |
| `sleep_hours` | float | Average nightly sleep hours |
| `math_score` | float | Math exam score |
| `reading_score` | float | Reading exam score |
| `writing_score` | float | Writing exam score |
| `average_score` | float | **Target** — mean of the three subject scores |

---

## 🔍 Project Pipeline

```
Raw Data → Inspection → Cleaning → Statistical Summary
    → Correlation Analysis → Hypothesis Testing → EDA Dashboard → Insights
```

### 1. Data Cleaning

| Issue | Count | Fix Applied |
|---|---|---|
| Duplicate rows | 8 | `drop_duplicates()` |
| Missing — `study_hours` | 15 | Median imputation |
| Missing — `sleep_hours` | 15 | Median imputation |

### 2. Statistical Summary
Generated descriptive statistics (`mean`, `std`, `min`, `25%`, `50%`, `75%`, `max`) for all numeric columns using `df.describe()`.

### 3. Correlation Analysis
Computed a full correlation matrix across numeric features, then separated **subject-score correlations** (trivially high, since math/reading/writing make up the average) from **behavioral/demographic correlations** to find genuinely actionable insights.

### 4. Hypothesis Testing
Ran an **independent t-test** comparing average scores between students who attended a study group versus those who didn't, to confirm whether the observed difference was statistically significant or due to chance.

---

## 📊 Key Findings

| Insight | Result |
|---|---|
| **Strongest behavioral factor** | Study hours (r = 0.422) |
| **Second strongest factor** | Attendance % (r = 0.225) |
| **Weakest factors** | Sleep hours (r = 0.046), Age (r = 0.061) |
| **Study group effect** | +6.0 points higher average (statistically significant, p < 0.0001) |
| **Gender score gap** | Only 0.8 points — minimal difference |
| **Top parental education group** | PhD-educated parents → 78.3 average score |
| **Subject score correlation** | Math ↔ Writing: r = 0.93 (strong cross-subject consistency) |

### Statistical Test Result

```
T-test: Study Group (Yes) vs Study Group (No)
t-statistic = 5.96
p-value     < 0.0001
→ Statistically significant difference at α = 0.05
```

> Students in a study group scored meaningfully higher — and this isn't just random noise, it's confirmed by hypothesis testing.

---

## 📊 Dashboard Visuals

| Chart | Type | Insight |
|---|---|---|
| KPI Cards | Metric tiles | Avg score, top factor, study group boost |
| Correlation Heatmap | Heatmap | All pairwise correlations across numeric features |
| Score Distribution | Histogram | Spread and central tendency of average scores |
| Study Hours vs Score | Scatter + trend line | Positive relationship, r = 0.42 |
| Attendance vs Score | Scatter + trend line | Positive relationship, r = 0.22 |
| Score by Parental Education | Box plot | Score spread across 4 education levels |
| Study Group Effect | Bar chart | Visual + statistical comparison |
| Subject Scores by Gender | Grouped bar chart | Math/Reading/Writing by gender |
| Sleep vs Score | Scatter + trend line | Weak relationship, r = 0.05 |

---

## 🗂️ Repository Structure

```
StudentPerformance-EDA/
│
├── student_eda_project.py            # Main Python script — full EDA pipeline
├── student_eda_dashboard.png          # Output — 9-panel visual dashboard
├── student_performance_dataset.csv    # Cleaned dataset (800 rows, 13 columns)
├── correlation_matrix.csv             # Exported correlation matrix
└── README.md                          # This file
```

---

## ▶️ How to Run

### On Kaggle (recommended)
1. Open a new notebook on [kaggle.com](https://kaggle.com)
2. Paste the full script into a code cell
3. Click **Run All** — all libraries (pandas, scipy, matplotlib, seaborn) are pre-installed
4. Outputs appear in the **Output** tab on the right

### Locally
```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# Run the script
python student_eda_project.py
```

---

## 📓 Script Structure

| Section | Contents |
|---|---|
| Section 1 | Generate 800-row synthetic student performance dataset |
| Section 2 | Data cleaning — duplicates, missing value imputation |
| Section 3 | Statistical summary — `describe()` on all numeric columns |
| Section 4 | Correlation analysis — full matrix + behavioral factor isolation |
| Section 5 | Key insights — top factor, study group boost, education impact |
| Section 6 | 9-panel EDA dashboard — dark-themed matplotlib + seaborn |
| Section 7 | Save outputs — dataset CSV, correlation matrix CSV |

---

## 🧠 Key Learnings

- **Correlation does not imply causation** — but isolating behavioral factors from trivially-correlated subject scores (math/reading/writing all feed into the average) gives a much more honest picture of what actually drives performance.
- **Hypothesis testing matters** — a visual difference between groups (study group vs not) can look convincing, but a t-test confirms whether it's statistically real or just sampling noise.
- **Median imputation** is a safe default for skewed numeric columns like study hours, where outliers could distort a mean-based fill.
- **Box plots reveal spread, not just averages** — parental education showed not only a rising trend in average score but also tighter score distributions at higher education levels.
- **Heatmaps need careful interpretation** — high inter-subject correlation (0.93) is structurally expected since they share a common average, not necessarily a new insight.

---

## 🛠️ Tech Stack

- **Python 3.8+**
- **Pandas** — data generation, cleaning, and manipulation
- **NumPy** — numerical operations
- **SciPy** — statistical hypothesis testing (t-test)
- **Matplotlib** — dashboard layout and dark-theme styling
- **Seaborn** — heatmap and statistical plot aesthetics
- **Kaggle Notebooks** — cloud execution environment

---

## 👤 Author

**Vishnu Prasad G S (VP)**
Data Science Learner
📍 Coimbatore, India

[![GitHub](https://img.shields.io/badge/GitHub-your--username-black?style=flat-square&logo=github)](https://github.com/your-username)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin)](https://linkedin.com/in/your-profile)

---

## 📝 Notes

> This dataset is **synthetically generated** for learning purposes. A good real-world alternative with similar structure is the [Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams) dataset on Kaggle, which uses the same gender/parental-education/lunch/test-prep schema.
