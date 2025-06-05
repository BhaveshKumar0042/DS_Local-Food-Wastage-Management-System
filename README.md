# Food Donation Platform: Exploratory Data Analysis

This project performs an in-depth Exploratory Data Analysis (EDA) on a dataset from a food sharing platform. The goal is to uncover patterns and insights into food donation activities, including listing statuses, popular food categories, top providers and receivers, and the time it takes for food to be claimed.

## Table of Contents
1.  [Project Overview](#project-overview)
2.  [Datasets](#datasets)
3.  [Workflow](#workflow)
4.  [Key Analysis Questions](#key-analysis-questions)
5.  [Key Insights](#key-insights)
6.  [Setup and Installation](#setup-and-installation)
7.  [How to Run](#how-to-run)
8.  [Files in this Repository](#files-in-this-repository)
9.  [Future Work](#future-work)

## Project Overview
Food waste is a significant global issue. This project analyzes data from a platform designed to connect food providers (like restaurants and grocery stores) with receivers (charities and individuals) to facilitate the donation of surplus food. Through data merging, cleaning, and visualization, this analysis aims to understand the platform's dynamics, identify areas for improvement, and highlight successful patterns of food redistribution.

## Datasets
The analysis is based on four separate CSV files which are merged to create a comprehensive dataset:

* **`food_listings_data.csv`**: Contains information about each food item listed for donation.
    * Key columns: `listing_id`, `provider_id`, `category`, `description`, `quantity`, `status`, `created_date`, `updated_date`.
* **`providers_data.csv`**: Contains details about the food providers.
    * Key columns: `provider_id`, `provider_name`, `address`, `provider_latitude`, `provider_longitude`.
* **`claims_data.csv`**: Records which food listings were claimed by which receivers.
    * Key columns: `claim_id`, `listing_id`, `receiver_id`, `claimed_date`.
* **`receivers_data.csv`**: Contains details about the food receivers.
    * Key columns: `receiver_id`, `name`, `address`, `receiver_latitude`, `receiver_longitude`.

## Workflow
1.  **Data Loading:** The four CSV files are loaded into individual pandas DataFrames.
2.  **Data Merging:** The separate DataFrames are merged into a single analytical dataset (`merged_df`) using common keys (`provider_id`, `listing_id`, `receiver_id`).
3.  **Data Cleaning:**
    * Missing values are checked and handled.
    * Date-related columns (`created_date`, `claimed_date`, `updated_date`) are converted to the proper datetime format for time-series analysis.
4.  **Feature Engineering:**
    * A new feature, `time_to_claim`, is created by calculating the difference between `claimed_date` and `created_date`. This helps in understanding the efficiency of the platform.
5.  **Exploratory Data Analysis (EDA):**
    * Descriptive statistics are generated to get a summary of the data.
    * Data visualizations are created using Matplotlib, Seaborn, and Plotly to explore relationships and answer key business questions.

## Key Analysis Questions
The notebook explores the following questions:

* What is the overall status of food listings (e.g., Claimed, Unclaimed, Expired)?
* Who are the top food providers based on the number of listings?
* Who are the top food receivers based on the number of claims?
* Which food categories are most frequently listed for donation?
* Are there trends in the number of claims over time (e.g., month-over-month)?
* What is the typical time it takes for a food listing to be claimed?

## Key Insights
* **High Claim Rate:** A significant majority of the food listings on the platform are successfully claimed, indicating an effective matching system.
* **Top Contributors & Receivers:** The analysis identifies the top 5 providers and receivers, highlighting key players in the ecosystem.
* **Popular Food Category:** "Packaged Meals & Processed Foods" is the most commonly donated category, suggesting a focus on ready-to-eat or easy-to-prepare items.
* **Rapid Claim Times:** Most claimed items are picked up very quickly, with a large number being claimed within the first day of being listed.
* **Temporal Trends:** A line chart of claims over time shows fluctuations, which could correspond to seasonal changes, holidays, or platform growth.

## Setup and Installation
1.  **Prerequisites:**
    * Python 3.x
    * Jupyter Notebook or Google Colab
2.  **Libraries:**
    This project uses standard data science libraries. You can install them using pip:
    ```bash
    pip install pandas numpy matplotlib seaborn plotly
    ```

## How to Run
1.  **Download the repository files.**
2.  **Ensure all required libraries are installed.**
3.  **Place the four CSV files** (`providers_data.csv`, `receivers_data.csv`, `food_listings_data.csv`, `claims_data.csv`) in the same directory as the Jupyter Notebook.
4.  **Open and run the `Bhavesh_project_1.ipynb` notebook** in a Jupyter or Colab environment. The cells can be executed sequentially to replicate the analysis.

## Files in this Repository
* `Bhavesh_project_1.ipynb`: The main Jupyter Notebook with the Python code and analysis.
* `providers_data.csv`: Dataset of food providers.
* `receivers_data.csv`: Dataset of food receivers.
* `food_listings_data.csv`: Dataset of food listings.
* `claims_data.csv`: Dataset of claim transactions.
* `README.md`: This file.

## Future Work
* **Geospatial Analysis:** Use the latitude and longitude data to map provider and receiver locations, analyze delivery distances, and identify underserved areas.
* **Predictive Modeling:** Build a machine learning model to predict whether a new listing will be claimed or expire, which could help providers optimize their listings.
* **Time-Series Forecasting:** Forecast future claim volumes to help the platform manage resources and logistics more effectively.
* **Text Analysis:** Apply Natural Language Processing (NLP) to the `description` field to extract more detailed insights about the types of food being donated.
