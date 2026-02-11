
# Societal Challenges Datathon – Data Cleaning & Modeling Pipeline

**Author:** Vasu Hiteshi  
**Notebook:** `main.ipynb`

This project builds a **clean, reproducible, and evaluation-ready pipeline** for working with real-world public health datasets (smoking behavior + diabetes indicators). The notebook contains exploration and debugging first, followed by a **final consolidated pipeline at the end**.

---

##  What This Project Does

- Cleans multiple real-world datasets with inconsistent schemas
- Standardizes smoking-related indicators across files
- Merges datasets into a unified analysis table
- Performs exploratory data analysis (EDA)
- Produces a **final submission-ready pipeline** (clearly separated)

---

##  Repository Structure

```text
.
├── main.ipynb                 # Full notebook (exploration + final pipeline)
├── data/
│   ├── diabetes.csv
│   ├── smoking_cigarette_use.csv
│   ├── smoking_household_smokers.csv
│   ├── smoking_recent_tobacco_use.csv
│   └── ...
└── Project_Explanation.md     # (This file)
```

>  **Important:** Only the **last section of `main.ipynb`** represents the final submission-ready pipeline. Earlier sections contain experiments and reasoning used while understanding the datasets.

---

##  Dependencies

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn
```

### Libraries Used

- **pandas** – Data loading, cleaning, merging, transformation
- **numpy** – Numerical operations and NaN handling
- **matplotlib** – Core plotting
- **seaborn** – Statistical visualization
- **pathlib** – Robust file path handling


---

##  Key Design Decisions (and Why)

### 1) Single Notebook Workflow

**Decision:** Keep everything inside `main.ipynb`.

**Why:**
- Datathon/exam settings favor a single inspectable artifact
- Makes evaluation easier (everything is in one place)
- Preserves reasoning, not just the final output

---

### 2) Explicit Cleaning (No Black-Box Utilities)

**Decision:** Perform cleaning step-by-step, column-by-column.

**Why:**
- Public health datasets contain **semantic encodings** (e.g., `1 = Yes`, `2 = No`)
- Missing/invalid values require **context-aware handling**
- Makes assumptions transparent and auditable

---

### 3) Smoking Dataset Harmonization Strategy

Across multiple smoking-related CSVs:

- Convert values using `pd.to_numeric(..., errors='coerce')`
- Handle missing values only when logically valid
- Normalize binary indicators into consistent numerical formats

**Why:**
- Smoking datasets often differ in encoding and schema
- Standardization is required before merging and analysis

---

### 4) Diabetes Dataset Cleaning Strategy

Key steps include:
- Detecting and fixing malformed/empty column names
- Normalizing types across numeric fields
- Preserving original structure to avoid information loss

**Why:**
- Medical datasets frequently contain schema/export issues
- Early renaming prevents silent downstream bugs

---

### 5) EDA Before Final Feature Decisions

**Decision:** Perform EDA after cleaning but before final feature selection.

**Why:**
- Confirms the cleaning logic is correct
- Reveals distributional anomalies early
- Provides interpretable evidence of relationships

---

##  Final Output

The final output of this project is:

- A **fully cleaned and merged dataset** combining smoking behavior + diabetes indicators
- A **repeatable pipeline** that can be re-run from raw CSVs
- A clear separation between exploration and final solution

The final pipeline is:

- Linear
- Minimal
- Free of trial code
- Ready for submission/evaluation

---

##  Final Pipeline (Submission-Ready)

The **final pipeline**, located at the end of `main.ipynb`, follows this order:

1. Load all raw datasets
2. Clean each dataset independently
   - Type coercion
   - Missing value handling
   - Semantic correction of invalid values
3. Standardize shared variables
4. Merge datasets into a unified dataframe
5. Run final EDA + validation checks
6. Produce analysis-ready output

---

## ▶ How to Run

1. Put all CSV files inside the `data/` directory
2. Open `main.ipynb`
3. Scroll to the final section marked as the **final pipeline**
4. Run the notebook top-to-bottom (or run only the final section)

---

##  Notes for Evaluators

- Earlier notebook sections are included intentionally to show reasoning
- Only the final pipeline should be used for evaluation
- All assumptions are explicitly encoded in the cleaning logic

---

##  Conclusion

This project prioritizes **clarity, correctness, and reproducibility** over aggressive optimization. The approach reflects real-world data science workflows, where understanding messy data is as important as modeling it.