
# Food Claims Process Analysis

## Overview
This project analyzes food poisoning claims filed against Vivendo, a fast-food chain in Brazil. The goal is to understand how different locations handle claims and identify trends in claim processing times.

## Dataset
The dataset contains 2000 rows, each representing a claim. Key columns include:
- **Claim ID**: Unique identifier.
- **Time to Close**: Days taken to close the claim.
- **Claim Amount**: Initial claim value (BRL).
- **Amount Paid**: Final amount paid (BRL).
- **Location**: Claim location (RECIFE, SAO LUIS, FORTALEZA, NATAL).
- **Individuals on Claim**: Number of individuals involved.
- **Linked Cases**: Whether the claim is linked to other cases (True/False).
- **Cause**: Cause of food poisoning (vegetable, meat, unknown).

## Steps

### 1. **Data Inspection**
- Checked for missing values, duplicates, and data types.
- Identified issues:
  - `claim_amount` had unwanted characters (e.g., "R$").
  - `amount_paid` and `linked_cases` had missing values.

### 2. **Data Cleaning**
- Removed "R$" from `claim_amount` and converted it to numeric.
- Filled missing values:
  - `amount_paid` and `claim_amount` with their medians.
  - `linked_cases` with "False".
  - `cause` with "unknown".
- Created new columns:
  - `months_to_close`: Categorized `time_to_close` into months.

### 3. **Sanity Check**
- Verified no missing values or duplicates remained.
- Ensured data types matched descriptions.

### 4. **Data Exploration**
#### a. **Claims by Location**
- Created a pie chart to visualize claim distribution across locations.
- **Insights**:
  - RECIFE had the most claims (44.25%).
  - NATAL had the fewest claims (14.35%).

#### b. **Time to Close Distribution**
- Plotted a histogram and bar chart to analyze claim closure times.
- **Insights**:
  - Most claims (81.55%) were closed within 8 months.
  - 946 claims were closed within 6 months.

#### c. **Time to Close vs. Location**
- Used a box plot to compare closure times across locations.
- **Insights**:
  - SAO LUIS had the most outliers, indicating complex claims.
  - NATAL had the fastest closure times.

## Conclusion
- **RECIFE** handles the most claims, while **NATAL** processes them the fastest.
- Most claims are resolved within 8 months, suggesting efficient handling.
- Further analysis could explore the impact of claim causes and linked cases on processing times.

---

### Visualizations
1. **Claims by Location (Pie Chart)**  
   ![Claims by Location](images/claims_by_location.png)

2. **Time to Close Distribution (Histogram)**  
   ![Time to Close Distribution](images/time_to_close_distribution.png)

3. **Time to Close vs. Location (Box Plot)**  
   ![Time to Close vs. Location](images/time_to_close_vs_location.png)
