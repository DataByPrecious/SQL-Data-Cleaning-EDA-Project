# SQL-Data-Cleaning-EDA-Project
This project involves performing a comprehensive analysis based on two categories, Data cleaning and Exploratory data analysis.

## 🌍 Global Layoff Data Analysis
This repository contains a comprehensive data analysis project that explores trends, patterns, and insights from global layoff data. The analysis uses SQL for data cleaning and a series of queries to uncover key factors influencing layoffs, the industries most affected, and geographical trends.

## 🎯 Project Overview

The primary goal of this project is to analyze global layoff data to identify significant trends that occurred between March 2020 and March 2023. This period captures a time of major global economic events, including the COVID-19 pandemic and subsequent recovery phases. The analysis provides valuable insights into how different industries and regions were affected by these challenges.

---

## 📊 Data and Tools

  * **Data Source:** The project utilizes a primary dataset, `layoffs.csv`, which contains detailed information about the number of layoffs and the percentage of the workforce laid off by various companies.
  * **Tools:** The data analysis and cleaning were performed using mySQL.

-----

## Methodology

The project follows a structured data analysis workflow, from initial data cleaning to in-depth exploratory analysis.

### 1\. Data Cleaning

The raw data underwent a rigorous cleaning process to ensure accuracy and consistency. The key steps and corresponding SQL queries included:

  * **Removing Duplicates:** Identified and removed duplicate entries to ensure each record is unique.

    ```sql
    SELECT *,
    ROW_NUMBER() OVER(
    PARTITION BY company, location, industry, total_laid_off, percentage_laid_off
    ORDER BY company
    ) AS row_num
    FROM layoffs_staging
    ```

  * **Standardizing Data:** Standardized inconsistent text entries (e.g., 'Crypto', 'CryptoCurrency') into a single, uniform term.

  * **Removing Null and Blank Values:** Identified and filled null or blank values in critical columns like `location` and `industry`.

  * **Removing Unwanted Data:** Removed unnecessary columns and rows where `total_laid_off` and `percentage_laid_off` were null.

### 2\. Exploratory Data Analysis

A series of SQL queries were executed to explore the cleaned dataset and answer key questions about the layoff trends.

  * **Timeline of Layoffs:** Investigated layoff data spanning from March 2020 to March 2023.

    ```sql
    SELECT MAX(date), MIN(date)
    FROM world_layoffs.layoffs2
    ```

  * **Most Affected Companies:** Identified the companies with the highest total number of layoffs.

    ```sql
    SELECT company, SUM(total_laid_off)
    FROM world_layoffs.layoffs2
    GROUP BY company
    ORDER BY 2 DESC
    ```

  * **Most Affected Countries:** Analyzed the geographical distribution of layoffs, identifying the countries with the highest total number of layoffs.

    ```sql
    SELECT country, SUM(total_laid_off)
    FROM world_layoffs.layoffs2
    GROUP BY country
    ORDER BY 2 DESC
    ```

-----

## 📌 Key Insights

The analysis provides several key insights into the global layoff landscape:

  * Companies that laid off their entire workforce (100% layoffs) were primarily early-stage startups.
  * The countries with the highest number of layoffs included the **United States**, **Canada**, and the **United Kingdom**.
  * The **San Francisco Bay Area** was identified as a major hub for layoffs within the United States.

-----


## 🛠️ License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and share this project with proper attribution

---

## 📮 Contact

Hi there! I'm **Okoroh Precious**, also known as **DataByPrecious**, I am a Data Analyst on a mission to share knowledge and project materials.
  [GitHub Profile](https://github.com/DataByPrecious)
  

**Note:** Please be sure to adjust the specific table and column names (`layoffs_staging`, `world_layoffs.layoffs2`) to match your actual database schema.
