# Week_0 Challenges

## Task 1: Git and Virtual Environment Setup

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

7. Folder Structure
Project Folder Structure was initialized as follows
ML-baed-solar-data-discoveries/
├── .github/workflows/python-package.yml     # CI/CD or GitHub Actions workflows 
├── .venv/                   # Virtual environment (excluded in .gitignore)
 ├── data/                    # Raw datasets 
 ├── notebooks/               # Jupyter notebooks for EDA, cleaning ...
 ├── scripts/                 # Reusable Python scripts 
├── src/                     # Source code for processing 
 ├── tests/                   # Unit tests
 ├── requirements.txt         # Environment dependencies
├── .gitignore               # Ignore virtual env, cache files, etc.  ├── LICENSE
    └── README.md
9. Final Merge setup-task into main via a Pull Request.
