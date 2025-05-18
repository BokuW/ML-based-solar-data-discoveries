
# Git and Virtual Environment Setup
## Task 1: 

This task focuses on setting up version control using Git and preparing a Virtual Python environment for the project.

Repository Setup

1. Create a GitHub repository (`ML-based-solar-data-discoveries`)
2. Clone it locally:
   
   git clone https://github.com/BokuW/ML-based-solar-data-discoveries.git
   cd ML-based-solar-data-discoveries

3. Create a virtual environment:
    python -m venv .venv 
    Activating it:
    .venv\Scripts\activate

4. Install dependencies:
    pip install -r requirements.txt
    Dependencies Used:
    seaborn 
    matplotlib
    pandas
    numpy
    scikit-learn
    jupyter

5.  Branching: Created a setup-task branch
6.  Commit:
    init: add .gitignore
    add: Requirements
    Create python package.yml

#  Data Profilling, Cleaning and EDA
## Task 2: Exploratory Data Analysis (EDA)
For all three countries (Benin, Togo, and Sierra Leone):
The datasets were successfully loaded and inspected.
Missing values were identified and handled appropriately, 
with a median imputation strategy for key variables and removal of columns with over 5% missingness.
Outliers were detected and flagged using Z-scores.
The cleaned datasets were exported to country-specific files.
Various time series plots, distribution analyses, and correlation analyses were performed, 
providing insights into the data's temporal patterns, variable distributions, and relationships.
The impact of data cleaning on key sensor readings was visualized.


