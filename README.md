# 📊 HR Analytics Dashboard — Power BI Portfolio Project

An interactive, end-to-end **HR Analytics Dashboard** built in **Power BI** to monitor workforce headcount, examine turnover dynamics, and isolate key drivers of employee attrition across departments, age demographics, salary tiers, and job roles.

## 📌 Executive Summary

Employee turnover creates significant operational costs and impacts productivity. This project delivers an interactive executive dashboard analyzing demographic, organizational, and experience factors across **1,480 employees** to empower HR leadership with data-driven retention strategies.

### Key Metrics Overview

* **Total Employees:** 1,478
* **Active Employees:** 1,239
* **Attrition Count:** 239
* **Attrition Rate:** 16.2%
* **Average Age:** 36.95 Years
* **Average Experience:** 7.01 Years

## 📸 Dashboard Preview

![HR Analytics Dashboard](<img width="1452" height="822" alt="dashboard_screenshot" src="https://github.com/user-attachments/assets/9003d388-71c7-4be2-bb96-5471f80f95c6" />
)

## 🔑 Key Insights & Business Findings

1. **Age Group Vulnerability:**
   * Staff in the **26–35 age band** show the highest absolute count of turnover, followed by the **36–45 group**. Early-to-mid career retention strategies are critical.

2. **Role & Satisfaction Impact:**
   * Turnover is heavily concentrated in frontline and operational positions like **Laboratory Technician**, **Sales Executive**, and **Research Scientist**.
   * Cross-analyzing job roles against **Job Satisfaction Levels (1–4)** reveals high dissatisfaction among turnover cases in entry-level and technical positions.

3. **Compensation & Experience Trends:**
   * Attrition spikes within lower-to-mid salary brackets (`0-3 LPA` and `3-6 LPA`) and during the initial **0 to 5 years** of company tenure.

## 📐 Data Model & Measures (DAX)

Key business calculations created using Explicit DAX Measures:

```dax
// 1. Total Employees
Total Employees = COUNT(HR_Analytics[EmpID])

// 2. Active Headcount
Active Employees = CALCULATE(
    COUNT(HR_Analytics[EmpID]),
    HR_Analytics[Attrition] = "No"
)

// 3. Attrition Count
Attrition Count = CALCULATE(
    COUNT(HR_Analytics[EmpID]),
    HR_Analytics[Attrition] = "Yes"
)

// 4. Attrition Rate %
Attrition Rate % = DIVIDE([Attrition Count], [Total Employees], 0)

// 5. Average Age
Average Age = AVERAGE(HR_Analytics[Age])

// 6. Average Experience
Avg Experience = AVERAGE(HR_Analytics[TotalExperienceYears])
