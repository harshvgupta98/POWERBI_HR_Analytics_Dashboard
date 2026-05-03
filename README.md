# 👥 HR Analytics Dashboard

A dynamic, interactive Power BI dashboard built to explore employee attrition trends and workforce demographics across departments, job roles, education levels, and salary bands.

---

## 📌 Short Description / Purpose

The **HR Analytics Dashboard** is a visually engaging Power BI report designed to help HR teams and business leaders analyse employee attrition across 1,480 employees. The dashboard uncovers patterns in attrition by age, salary, education, job role, and tenure — enabling data-driven decisions around retention, compensation, and workforce planning.

---

## 🛠️ Tech Stack

The dashboard was built using the following tools and technologies:

- **📊 Power BI Desktop** – Main data visualization platform used for report creation.
- **📂 Power Query** – Data transformation and cleaning layer for reshaping and preparing the HR data.
- **🧠 DAX (Data Analysis Expressions)** – Used for calculated measures such as `Attrition_Rate` and `Attrition_Count`.
- **📝 Data Modeling** – Star schema relationships established among tables (`HR_Data`, `Departments`, `Jobs`, `Education`) to enable cross-filtering and aggregation.
- **📁 File Format** – `.pbit` (Power BI Template) for portability and `.png` for dashboard preview.

---

## 🧮 DAX Measures

| Measure | Expression | Description |
|---------|-----------|-------------|
| `Attrition_Rate` | `SUM(HR_Data[Attrition_Count]) / SUM(HR_Data[EmployeeCount])` | Percentage of employees who have left |

> KPI cards for Avg Age, Avg Salary, and Avg Tenure use implicit measures (Power BI built-in aggregations) on `Age`, `MonthlyIncome`, and `YearsAtCompany` respectively.

---

## 📂 Data Source

**Source**: IBM HR Analytics Employee Attrition & Performance dataset.

Data covering **1,480 employees** with attributes including demographics, compensation, satisfaction scores, job role, education level, and attrition status. The dataset is structured across four tables — `HR_Data` (fact), `Departments`, `Jobs`, and `Education` (dimensions) — linked via a star schema.

---

## 📖 Data Dictionary

### HR_Data (Fact Table)

| Column | Type | Description |
|--------|------|-------------|
| `EmpID` | String | Unique employee identifier |
| `Age` | Int | Employee age in years |
| `AgeGroup` | String | Banded age group (e.g. 18-25, 26-35) |
| `Attrition` | String | Whether employee left — Yes / No |
| `Attrition_Count` | Int | Binary flag: 1 = left, 0 = stayed |
| `BusinessTravel` | String | Travel frequency — Non-Travel, Travel_Rarely, Travel_Frequently |
| `DailyRate` | Int | Daily pay rate |
| `Department` | Int (FK) | Links to Departments.Department_ID |
| `DistanceFromHome` | Int | Distance from home to office (km) |
| `Education` | Int (FK) | Links to Education.Education_ID (1=Below College, 2=College, 3=Bachelor, 4=Master, 5=Doctor) |
| `EmployeeCount` | Int | Always 1 — used as a counting measure |
| `EmployeeNumber` | Int | HR system employee number |
| `EnvironmentSatisfaction` | Int | Workplace environment rating (1=Low, 2=Medium, 3=High, 4=Very High) |
| `Gender` | String | Male / Female |
| `HourlyRate` | Int | Hourly pay rate |
| `JobInvolvement` | Int | Job involvement score (1=Low, 2=Medium, 3=High, 4=Very High) |
| `JobLevel` | Int | Seniority level (1-5) |
| `JobID` | Int (FK) | Links to Jobs.Job_ID |
| `JobSatisfaction` | Int | Job satisfaction score (1=Low, 2=Medium, 3=High, 4=Very High) |
| `MaritalStatus` | String | Single, Married, Divorced |
| `MonthlyIncome` | Int | Monthly salary in local currency |
| `SalarySlab` | String | Banded salary group (e.g. Under 5k, 5k-10k) |
| `MonthlyRate` | Int | Monthly rate (different from income) |
| `NumCompaniesWorked` | Int | Number of previous employers |
| `Over18` | String | Always Y — all employees are over 18 |
| `OverTime` | String | Whether employee works overtime — Yes / No |
| `PercentSalaryHike` | Int | Last salary hike percentage |
| `PerformanceRating` | Int | Last performance review rating (1-4) |
| `RelationshipSatisfaction` | Int | Satisfaction with work relationships (1=Low to 4=Very High) |
| `StandardHours` | Int | Always 80 — standard working hours |
| `StockOptionLevel` | Int | Stock option grant level (0-3) |
| `TotalWorkingYears` | Int | Total years of work experience |
| `TrainingTimesLastYear` | Int | Number of training sessions attended last year |
| `WorkLifeBalance` | Int | Work-life balance rating (1=Bad, 2=Good, 3=Better, 4=Best) |
| `YearsAtCompany` | Int | Total years at current company |
| `YearsInCurrentRole` | Int | Years in current job role |
| `YearsSinceLastPromotion` | Int | Years since last promotion |
| `YearsWithCurrManager` | Int | Years working under current manager |

### Dimension Tables

| Table | Column | Description |
|-------|--------|-------------|
| `Departments` | Department_ID, Department | Maps ID to department name (HR, R&D, Sales) |
| `Jobs` | Job_ID, JobRole | Maps ID to job role name |
| `Education` | Education_ID, Education | Maps ID to education level label |

---

## ✨ Features / Highlights

### 🔴 Business Problem

HR teams and business leaders often struggle to identify *why* employees leave and *who* is most at risk. Key questions such as:

- Which age groups and salary bands have the highest attrition?
- Are certain job roles or education backgrounds more prone to leaving?
- Does tenure or overtime status affect attrition?

…are difficult to answer quickly from raw spreadsheet data.

---

### 🎯 Goal of the Dashboard

To deliver an interactive visual tool that:

- Enables HR teams to monitor attrition trends across multiple dimensions simultaneously.
- Supports retention strategy decisions by identifying high-risk employee segments.
- Provides leadership with a clear, at-a-glance summary of workforce health metrics.

---

### 🖼️ Walkthrough of Key Visuals

- **Key KPIs (Top Row)**
  - Total Employees: **1,480**
  - Attrition Count: **238**
  - Attrition Rate: **16%**
  - Average Age: **37**
  - Average Salary: **6.50K**
  - Average Tenure: **7 years**

- **Department Slicer (Top Centre)**
  An interactive filter allowing users to drill down by *Human Resources*, *Research & Development*, or *Sales* — updating all visuals simultaneously.

- **Attrition by Education (Donut Chart)**
  Breaks down attrition by educational background. Life Sciences (37%) and Medical (26%) account for the majority of attrition.

- **Attrition by Age (Bar Chart)**
  Shows attrition count by age group. The **26–35** band has the highest attrition at **116 employees**, indicating early-career churn is the biggest risk.

- **Attrition by Job Role × Education Level (Matrix Table)**
  Cross-tabulated view showing attrition count per job role broken down by education level (1–4). Research Scientists (100 total) and HR roles (58 total) lead across education levels.

- **Attrition by Salary Slab (Bar Chart)**
  Employees earning **under 5K** account for **163 out of 238** attritions — a clear signal that lower compensation is the single strongest driver of attrition.

- **Attrition by Years at Company (Line Chart)**
  Reveals a sharp spike at **Year 1 (59 employees)**, suggesting early onboarding or expectation-setting issues. A secondary spike appears around year 10.

- **Attrition by Job Role (Horizontal Bar Chart)**
  Research Scientists (100), Human Resources (58), Sales Representatives (44), and Laboratory Technicians (31) are the most affected roles.

- **Attrition by Gender (Side-by-Side Card)**
  Male attrition: **151** | Female attrition: **87** — males represent a disproportionately higher share of total attrition.

---

### 💡 Business Impact & Insights

- **💰 Compensation Strategy**: With 68% of attrition in the under-5K salary band, targeted salary reviews for lower-pay grades could significantly reduce turnover.
- **🎓 Retention by Role**: Research Scientists and HR staff leaving at high rates suggests role-specific engagement or career-pathing issues worth investigating.
- **📅 Onboarding Focus**: The Year 1 attrition spike points to a need for stronger onboarding, mentorship, and 90-day check-in programmes.
- **👥 Demographic Planning**: Disproportionate male attrition and the 26–35 age concentration can help HR tailor retention efforts to specific employee segments.
- **🏢 Departmental Drill-Down**: The department slicer allows leadership to isolate and compare attrition patterns across Sales, R&D, and HR independently.

---

## 📸 Dashboard Preview

![HR Analytics Dashboard](https://github.com/harshvgupta98/POWERBI_HR_Analytics_Dashboard/blob/main/Snapshot%20of%20HR%20Analytics%20Dashboard.png)

---

## 📁 File Structure

```
HR_Analytics_Dashboard/
├── HR_Analytics_Dashboard.pbit              # Power BI Template file
├── HR_Data.xlsx                             # Source dataset
├── Snapshot_of_HR_Analytics_Dashboard.png  # Dashboard preview
├── LICENSE                                  # MIT License
└── README.md
```
