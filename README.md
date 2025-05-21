ML-based-Solar-Data-Discoveries
Solar Data Analysis for MoonLight Energy Solutions: Strategic Investment Insights
This repository contains the code and analysis for a project aimed at providing data-driven insights to MoonLight Energy Solutions for strategic solar investments. As an Analytics Engineer, the primary goal was to analyze environmental measurement data to identify key trends, derive actionable insights, and recommend high-potential regions for solar installation, aligning with the company's long-term sustainability objectives.

The project encompasses data profiling, cleaning, exploratory data analysis (EDA), cross-country comparison, and the development of an interactive Streamlit dashboard.

Dataset Overview
The dataset, "Solar Radiation Measurement Data," provides comprehensive hourly environmental measurements. Each row includes:

Timestamp (yyyy-mm-dd hh:mm): Date and time of each observation.

GHI (W/m²): Global Horizontal Irradiance (total solar radiation on a horizontal surface).

DNI (W/m²): Direct Normal Irradiance (solar radiation perpendicular to sun's rays).

DHI (W/m²): Diffuse Horizontal Irradiance (solar radiation not direct from the sun).

ModA (W/m²): Measurements from Module A sensor.

ModB (W/m²): Measurements from Module B sensor.

Tamb (°C): Ambient Temperature.

RH (%): Relative Humidity.

WS (m/s): Wind Speed.

WSgust (m/s): Maximum Wind Gust Speed.

WSstdev (m/s): Standard Deviation of Wind Speed.

WD (°N (to east)): Wind Direction in degrees from north.

WDstdev: Standard Deviation of Wind Direction.

BP (hPa): Barometric Pressure.

Cleaning (1 or 0): Indicates if cleaning occurred.

Precipitation (mm/min): Precipitation rate.

TModA (°C): Temperature of Module A.

TModB (°C): Temperature of Module B.

Comments: Additional notes.

Project Structure
The repository is organized as follows:

ML-based-solar-data-discoveries/
├── app/                      # Streamlit application scripts
│   ├── __init__.py           # Makes 'app' a Python package
│   ├── main.py               # Main Streamlit dashboard script
│   └── utils.py              # Utility functions for data processing and visualization
├── data/                     # Raw and cleaned CSV datasets (ignored by Git)
│   ├── benin-malanville.csv
│   ├── sierra-bumbuna.csv
│   ├── togo-dapaong_qc.csv
│   ├── benin-malanville_clean.csv
│   ├── sierra-bumbuna_clean.csv
│   └── togo-dapaong_qc_clean.csv
├── notebooks/                # Jupyter notebooks for EDA and comparison
│   ├── benin_eda.ipynb
│   ├── sierraleone_eda.ipynb
│   ├── togo_eda.ipynb
│   └── compare_countries.ipynb
├── tests/                    # Unit tests for core functions
│   ├── __init__.py
│   ├── test_solar_data.py    # Tests for solar_data_analysis.py functions
│   └── solar_data_analysis.py # Modularized core data analysis functions (for testing)
├── .github/                  # GitHub Actions CI/CD workflows
│   └── workflows/
│       └── python-package.yml
├── .gitignore                # Specifies files/directories to ignore in Git
├── requirements.txt          # Project dependencies
└── README.md                 # This README file

Getting Started
Follow these steps to set up the project locally and run the analyses.

1. Git and Virtual Environment Setup (Task 1)
This task focuses on establishing a robust development environment and adhering to best practices in version control.

Repository Initialization:

Clone the GitHub repository to your local machine:

git clone https://github.com/BokuW/ML-based-solar-data-discoveries.git

Navigate into the project directory:

cd ML-based-solar-data-discoveries

Virtual Environment Setup:

Create a virtual environment to manage project dependencies in isolation. This prevents conflicts with other Python projects on your system.

python -m venv .venv

Activate the virtual environment:

On Windows:

.venv\Scripts\activate

On macOS/Linux:

source .venv/bin/activate

Install Dependencies:

Install all required Python packages listed in requirements.txt. This ensures your environment has all necessary libraries for the project.

pip install -r requirements.txt

Key Dependencies: pandas, numpy, scipy, matplotlib, seaborn, jupyter, pytest, streamlit.

Git Hygiene & Branching:

The .gitignore file is configured to exclude unnecessary files (like data/ contents, .csv files, virtual environment files, and Jupyter checkpoints) from version control, keeping the repository clean and focused on code.

Initial commits were made to set up the repository structure and add basic configurations.

A dedicated branch (setup-task) was used for initial setup work and later merged into main via a Pull Request, demonstrating a standard Git workflow.

Basic CI/CD with GitHub Actions:

A GitHub Actions workflow (.github/workflows/python-package.yml) is configured to automate basic quality checks.

On every push and pull_request to the main branch, this workflow automatically:

Installs Python dependencies from requirements.txt.

Runs flake8 for code linting (style and basic error checks).

Executes pytest to run unit tests.

This ensures continuous integration, maintaining code quality and catching issues early in the development cycle.

2. Data Profiling, Cleaning & EDA (Task 2)
This task involved a comprehensive analysis of individual country datasets (Benin, Togo, and Sierra Leone) to prepare them for robust comparison. The core data processing logic is modularized into reusable Python functions within solar_data_analysis.py (located in the tests/ directory for testability, but conceptually part of the main logic).

Execution:

Navigate to the notebooks/ directory.

Open and run the individual EDA notebooks: benin_eda.ipynb, sierraleone_eda.ipynb, and togo_eda.ipynb.

Key Steps Performed:

Data Loading & Initial Inspection: Datasets were loaded, and df.info(), df.describe(), and df.head() were used for initial understanding.

Missing Value Report: df.isnull().sum() and percentage calculations identified columns with missing data, specifically flagging those with over 5% nulls.

Outlier Detection & Basic Cleaning:

Negative values in GHI, DNI, DHI, ModA, ModB were systematically replaced with NaN.

Z-scores were computed for GHI, DNI, DHI, ModA, ModB, WS, WSgust. Rows with |Z| > 3 were flagged as outliers, and a Cleaning_Flag column was created.

Missing values in key columns were imputed using their respective medians to maintain data distribution.

Columns with more than 5% missing values were dropped to ensure data quality.

Data Export: The cleaned DataFrame for each country was exported to a dedicated CSV file (e.g., data/benin-malanville_clean.csv), ready for subsequent comparative analysis.

Exploratory Visualizations:

Time Series Analysis: Line plots of GHI, DNI, DHI, and Tamb against Timestamp revealed daily and seasonal patterns. Monthly and hourly trends were also visualized.

Cleaning Impact: Bar charts showed the average ModA and ModB values before and after cleaning, demonstrating the effect of outlier removal and imputation.

Correlation & Relationship Analysis: Heatmaps illustrated correlations between irradiance and module temperature. Scatter plots explored relationships between wind data, humidity, temperature, and GHI.

Wind & Distribution Analysis: Wind rose plots provided insights into wind speed and direction, complemented by histograms for GHI and WS.

Temperature Analysis: Scatter plots examined how RH influences Tamb and GHI.

Bubble Chart: A bubble chart visualized GHI vs. Tamb with bubble size representing RH, offering a multi-dimensional view.

3. Cross-Country Comparison (Task 3)
This task synthesized the cleaned datasets from Task 2 to identify relative solar potential and key differences across Benin, Sierra Leone, and Togo.

Execution:

Navigate to the notebooks/ directory.

Open and run the compare_countries.ipynb notebook.

Methodology & Key Findings:

Data Loading: The cleaned CSV files (e.g., data/benin-malanville_clean.csv) for all three countries were loaded, ensuring consistency in the comparison.

Metric Comparison (Boxplots): Side-by-side boxplots for GHI, DNI, and DHI were generated.

Insight: Benin consistently showed higher median GHI and DNI, indicating stronger direct solar potential. Togo exhibited notably low median DNI and DHI, suggesting a more challenging solar resource.

Summary Table: A comprehensive table compared the mean, median, and standard deviation of GHI, DNI, and DHI across countries, providing a quantitative overview.

Statistical Testing:

One-way ANOVA for GHI: (F=22833.40,p<0.001) indicated a highly statistically significant difference in mean GHI across the countries.

Kruskal-Wallis H-test for GHI: (H=168588.78,p<0.001) further confirmed a highly statistically significant difference in GHI distributions/medians.

Key Observations (Summary):

Overall Solar Potential (GHI): Benin consistently shows the highest median GHI, indicating a generally stronger overall solar resource. Statistical tests confirm these differences are significant.

Direct vs. Diffuse Irradiance: Benin has significantly higher DNI (direct sunlight). Togo exhibits very low median DNI and DHI, suggesting limited direct and diffuse radiation.

Variability: All countries show considerable variability in solar metrics, highlighting the dynamic nature of solar resources.

Visual Summary: A bar chart ranked countries by their average GHI, visually confirming Benin's leading position.

4. Interactive Dashboard (Streamlit)
An interactive Streamlit application was developed to visualize the insights gained from the EDA and cross-country comparison in an accessible web interface.

Execution:

Ensure your virtual environment is activated.

From the root of the project directory (ML-based-solar-data-discoveries/), run:

streamlit run app/main.py

This will open the dashboard in your web browser, typically at http://localhost:8501.

Architecture:

The app is organized within the app/ directory: main.py handles the UI layout and interactivity, while utils.py contains all the data loading, cleaning, processing, and plotting functions. This modularity enhances readability and maintainability.

Docstrings: All functions in app/utils.py and tests/solar_data_analysis.py include comprehensive docstrings explaining their purpose, arguments, and return values, improving code clarity and maintainability.

Data Handling & Performance:

Functions for data loading and processing in app/utils.py are designed to read the cleaned CSVs from the data/ directory.

Streamlit's @st.cache_data decorator is extensively used to cache the results of data loading and heavy processing steps. This is crucial for performance, as Streamlit reruns the entire script on every user interaction; caching prevents redundant computations, making the dashboard highly responsive.

Interactive Features:

A sidebar dropdown allows users to select a specific country for detailed EDA (viewing summary statistics, time series, monthly/hourly patterns, cleaning impact, correlations, wind analysis, temperature analysis, and bubble charts).

Users can also select "Cross-Country Comparison" to view the comparative boxplots, summary table, statistical test results, and key observations.

Visual Appeal: The dashboard is designed for clarity and usability, using Streamlit widgets (st.selectbox, st.dataframe, st.pyplot, st.markdown) to present insights effectively.

Challenges & Solutions
Throughout the project, several technical and methodological challenges were encountered and successfully resolved:

Git & GitHub Actions Setup: Initial difficulties arose in configuring the GitHub Actions workflow and ensuring all dependencies were correctly installed for CI checks.

Solution: Meticulous review and modification of python-package.yml to ensure pip install -r requirements.txt executed correctly. Debugging involved inspecting workflow logs to identify missing packages or incorrect commands.

NameError: name 'df' is not defined in Notebooks: This common issue occurred when Jupyter notebook cells were executed out of order, leading to variables not being initialized.

Solution: Ensured sequential execution of notebook cells. For the Streamlit application, all data loading and processing logic was encapsulated within functions in app/utils.py, making variable scope explicit and preventing such errors.

AttributeError: module 'scipy.stats' has no attribute 'zscore': This indicated that the scipy library was either not installed or was an outdated version in the active environment.

Solution: Ensured scipy was correctly installed and up-to-date within the virtual environment using pip install --upgrade scipy. Restarting the Jupyter kernel or VS Code helped in recognizing the newly installed package.

Empty Test Folder / Failing CI Checks: The GitHub Actions workflow failed because no tests were found by pytest, or existing tests failed due to unresolved imports.

Solution: Created a tests/ directory and populated it with test_solar_data.py. This test file was designed to import and test functions from solar_data_analysis.py (which contains the modularized EDA logic), ensuring the CI pipeline had valid tests to run.

Pylance Import Warnings (Import "pytest" could not be resolved): VS Code's Pylance language server sometimes failed to resolve imports, leading to warnings.

Solution: The primary fix involved ensuring the correct Python interpreter (specifically the project's virtual environment) was selected in VS Code. Additionally, verifying correct relative import paths (e.g., from solar_data_analysis import ... when files are in the same directory) resolved these warnings.

Long Hardcoded File Paths: Using absolute file paths made the code less portable and harder to read.

Solution: Introduced a base_data_path variable at the top of scripts and used os.path.join and f-strings to construct relative and concise file paths, improving maintainability.

Transitioning from Notebooks to Streamlit: Adapting iterative notebook-based analysis code for a continuous-running web application, especially concerning plot rendering and data reloading.

Solution: Refactored all data processing and plotting logic from notebooks into modular functions in app/utils.py. Crucially, plotting functions were modified to return Matplotlib Figure objects instead of calling plt.show(). Streamlit's @st.cache_data decorator was strategically applied to data loading and processing functions to optimize performance by preventing redundant computations on app reruns.

Recommendations
To further enhance this project and provide more comprehensive value to MoonLight Energy Solutions, consider the following recommendations:

Advanced Data Validation & Anomaly Detection: Implement more sophisticated techniques beyond Z-scores, such as time-series specific anomaly detection algorithms (e.g., Isolation Forest, ARIMA-based detection) or statistical process control (SPC) charts, to identify subtle or contextual data quality issues.

Predictive Modeling for Solar Output: Develop machine learning models (e.g., recurrent neural networks for time series, gradient boosting models) to forecast GHI, DNI, or actual energy production. This would enable proactive energy planning, optimize grid integration, and inform future investment sizing.

Refined Region Prioritization Metrics: Incorporate additional criteria for ranking regions beyond just solar irradiance, such as:

Economic Factors: Local electricity prices, potential for subsidies, cost of land, labor availability.

Infrastructure: Proximity to existing grid infrastructure, transmission capacity.

Environmental Factors: Dust accumulation rates, extreme weather events (beyond just wind), local topography.

Social & Regulatory Landscape: Local community acceptance, government policies, permitting processes.

Conclusion
The project  delivers data-driven insights for MoonLight Energy Solutions' solar investment strategy by establishing a robust environment, performing comprehensive EDA on multi-country solar data, and developing an interactive Streamlit dashboard. The analysis revealed statistically significant differences in solar potential across Benin, Sierra Leone, and Togo, with Benin showing the highest GHI and DNI, while Togo presented unique challenges, providing a clear foundation for targeted investments. Despite encountering and resolving various technical challenges, the project's outcome is a valuable analytical framework and visualization tool that will support informed decision-making and advance the company's sustainability goals.
