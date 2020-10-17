# Comparison-of-TN-and-TX-schools

Overview
The task at hand is to evaluate the impact of YOY change in school size to performance on state tests for schools in Tennessee and Texas.

## Approach
Data is pulled from public data sources here (https://www.tn.gov/education/data/data-downloads.html) and here (https://tea.texas.gov/texas-schools/accountability/academic-accountability/performance-reporting/texas-academic-performance-reports). Data was pulled for the 3 most recent, complete school years; given the interruptions that COVID had on the 2019-2020 school year, those data were incomplete, so I pulled information from the 2016-17, 2017-18, and 2018-19 school years.

For TN - I selected state Accountability records and the Enrollment data. From the Accountability data, I selected information about performance for key subjects (ELA, Math, Social Studies, HS English, HS Math, and HS History), specifically the percent of students at each school who were on target or mastering the subject. From Enrollment data, I selected information specifically on total school population, ignoring more nuanced data about student demographic breakdowns for this analysis. This decision was made primarily due to the lack of 1:1 ethnic/race groups available for the Accountability data.

For TX - I selected Campus level data and first extracted the Accountability reports. These reports also linked to a separate table with a glossary of table column translations - I copy and pasted these into excel files and saved those to the working folder. The Accountability reports included information about total enrollment for the school year at each campus. I then selected Academic performance data, primarily data about percentage of students meeting expectation rates on the STAAR assesments. I selected data rolled up for all subject by campus, but would link in mulitple sources to break performance out across subjects if I went deeper on this analysis.

After combining enrollment data, I calculated a Year-over-Year rate of change for each campus to standardize growth. Another approach that was considered would be to simply calculate the change in the actual number of seats in each school, but for the sake of this exercise, I chose to work with proportional change.

To measure change in academic proficiency, I simply took the difference between percent of students 'on target/mastered' from the current year from the previous. Academic and enrollment data were combined - for TN, I was able to combine the change in campus size with performance on a number of subjects for each campus. For TX - I combined the performance rate on all tests with the rate of change in campus size.

Outlier data were removed. Rows with Null values or place holder values in place of critical information were dropped.

## Analysis
My thought to use rate of change in size allowed for a lagged outcome to present itself. The delta between Year 1 and Year 2 would present itself in Year 2 test scores, as the impact of the addition or loss of students was absorbed by the campus.

Because we were curious about how the change in size impacted performance, I used the mean of growth rate as a point to split my academic performance into groups (proficiency at campuses experiencing above/below average).

Once the populations were split, I conducted a Levene test to test whether variance of the populations were equal. If variance were equal, I conducted independent Students t-test; if they did not have equal variance, I substituted Welch's t-test.

With the t-test, I was testing the following null hypothesis:

H0: Mean(group1) = Mean(group2)
H1: Mean(group1) != Mean(group2)

If I uncovered a p-value < 0.05 (my alpha level of significance), I had enough evidence to reject the null hypothesis, allowing me to conclude there was a statistically significant difference in group means, where the groups were split by the rate of change in school population size (and by test subject in the case of TN data).

## Findings
In TN, performance in HS English and ELA showed statistically significant differences in the change in student performance levels as a result of school growth.

In TX, campuses that shrank (those with negative growth rates) saw greater gains in proficiency levels than those campuses that grew over the same time period.
