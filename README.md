
# README: NYC Public School SAT Performance Analysis

## Overview
This project analyzes NYC public schools' SAT performance using the `schools.csv` dataset. The SAT, with sections in Math, Reading, and Writing (each scored out of 800), is crucial for college admissions. The analysis identifies top-performing schools and borough trends, providing insights for parents, educators, and policymakers.

## Questions Answered
1. **Top Math-Performing Schools**: Schools with an average Math SAT score ≥ 640, sorted by performance.  
2. **Top 10 Schools by Total SAT Score**: Schools with the highest total SAT scores (sum of Math, Reading, and Writing).  
3. **Borough Variability**: Borough with the highest SAT score standard deviation.

## Code Highlights
1. **Filter Top Math Schools**:
   ```python
   best_math_schools = schools[schools["average_math"] >= 640][["school_name", "average_math"]].sort_values("average_math", ascending=False)
   ```

2. **Calculate Total SAT Scores and Top Schools**:
   ```python
   schools["total_SAT"] = schools["average_math"] + schools["average_reading"] + schools["average_writing"]
   top_10_schools = schools.sort_values("total_SAT", ascending=False)[["school_name", "total_SAT"]].head(10)
   ```

3. **Borough Analysis**:
   ```python
   boroughs = schools.groupby("borough")["total_SAT"].agg(["count", "mean", "std"]).round(2)
   largest_std_dev = boroughs[boroughs["std"] == boroughs["std"].max()]
   ```

## Outputs
- **Top Math Schools**: List of schools with high Math scores.  
- **Top 10 Schools by Total SAT**: List of the best-performing schools overall.  
- **Borough Variability**: Borough with the highest SAT performance variability.

## Requirements
- Python 3.x  
- pandas library  

## Insights
The analysis helps stakeholders identify high-performing schools, address borough disparities, and prioritize educational improvements.
