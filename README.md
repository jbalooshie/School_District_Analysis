# School_District_Analysis
This repository was created as part of a 6 month Data Analystics Bootcamp administed by George Washington University. This is the repository for the Module 4 Challenge. This challenge served as an introduction to NumPy and pandas. Topics covered including creating data frames, cleaning data, and performing descriptive analysis. Final project work is in PyCitySchools_Challenge.ipynb. 

## Overview
For this analysis, we partnered with the chief data scientist of an unnamed school district to prepare and present the results of the latest round of standardized testing. The goal of the analysis is to provide district and school administrators with accurate and detailed breakdowns of the test results of their student body. With this, they can make informed decisions when it comes to assigning resources to best help their students. We were initially provided with two CSV files. One showed the student's name, grade, school name, math test score, and reading test score. The other showed the school name, school type, student body size, and school budget. From this we were able to provide robust analytics that broke the results down in a variety of ways and highlighted specific trends that cannot be seen by just looking at the test results.

In addition, we updated our analysis when it was discovered that the results for the 9th graders at Thomas High School had been allegedly altered. We removed these results from the analysis and provided an updated analysis. This helps administrators ensure they are working with the most accurate data possible. From this data, they can make decisions on how to allocate budgets, re-zone school districts, and target certain grade levels to ensure they are meeting their academic goals. They can also now get an idea of how the results of the testing might have been impacted by the alleged manipulations. Below we will break down how various results were affected by the alleged manipulation, and how removing the suspect data impacts certain results.

## Results
1. How is the district summary affected?
  - We had to create a new variable to update the values in the district summary. The original analysis used a variable called student_count to determine the % of students passing both tests. The updated analysis includes a variable called new_total_count to determine the total % of passing students int he district. This new variable is the total number of students in the district minus the number of 9th graders at Thomas High School.
2. How is the school summary affected?
  - For the school summary, we had to create new variables to calculate the % of Thomas High School's students who had passed the two tests. We then re-calculated the %s of Thomas HS students who passed and replaced the original values in the data with these new ones. Here are the variables: 
`thomas_do_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["grade"] != "9th")]` 
`do_count = thomas_do_count["Student ID"].count()`
3. How does replacing the ninth grader's math and reading scores affect Thomas High School's performance relative to the other schools?
  - There is no change in terms of the school's performance relative to the other schools. Overall, they are still had the second highest scores in the district. The gap between Thomas and the next highest ranked school closes by a few tenths of a percent.
4. How does replacing the ninth-grade scores affect the following:
  - Math and reading scores by grade
    - Thomas High School no longer has scores for their 9th graders. We removed all 9th grade scores, so now these values read "nan". Even if some of the Thomas High School scores for 9th graders were legitimate, all values have been removed.
  - Scores by school spending
    - There is no difference between the original or the updated values.
  - Scores by school size
    - There is no difference between the original or the updated values.
  - Scores by school type
    - There is no difference between the original or the updated values.
## Summary
Below are the original district results followed by the updated district results, with the suspect data removed. Please refer to it in the follow subsection. 
![Original District Analysis](https://github.com/jbalooshie/School_District_Analysis/blob/main/images/original_district_summary.PNG) 
![Updated District Analysis](https://github.com/jbalooshie/School_District_Analysis/blob/main/images/updated_summary.PNG)

Please read the below subsection for an analysis of four major areas where the results for the school district change due to the suspect scores. Based on this analysis - it appears a small group of 9th graders at Thomas High School manipulated their scores to ensure they were above the passing threshold. They did not do so in a very conspicuous way (I.E. changing failing grade to one that earns an "A"), and it seems like the extent of the manipulation was to slightly bump up the number of students who were considered passing.

### Summarize four major changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
  - The average math score with the suspect data is 79.0. The average math score with the suspect data removed is 78.9. Math scores were slightly inflated by the suspect values and caused a small increase across the district.
  - The passing math percentage drops from 75% to 74.8%. The suspect scores at Thomas High School made this value slightly higher than the actual value.
  - The passing reading percentage drops from 86% to 85.7%. The suspect scores at Thomas High School made this value slightly higher than the actual value.
  - The overall passing percentage drops from 65% to 64.9%. This seems small, but that means there is a group of students who manipulated their scores to ensure they met the threshold for passing.
