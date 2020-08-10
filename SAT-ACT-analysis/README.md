# How to increase SAT participation rate?

## Introduction

In the U.S., the SAT and ACT are the two most well-known standardised tests used for admission into colleges or universities. The SAT was introduced to the U.S. in 1926 whereas the ACT was introduced in 1959 as a competitor to the SAT.

The SAT has traditionally been the most popular college admissions test in the U.S., but in the past decade, the ACT had gained significant ground and between 2012 and 2017, it overtook the SAT as the most widely used college admissions test.

To win back its market share, the College Board implemented major changes to the format of the SAT and aggressively bade for statewide contracts to administer the SAT tests amongst high school students. In 2018, the College Board's efforts finally paid off and the SAT surpassed the ACT to become the dominant college admissions test once more.


## Problem Statement
In this project, we examine the ACT and SAT scores and participation rates by state in 2017 and 2018 to identify a specific state that the College Board can target to drive higher SAT participation rates going forward.


## Findings

- Although there is higher number of SAT test-takers in 2018, ACT still has a higher average participation rate. This is possible because 1/3 of all U.S. states have a 100% ACT participation rate, but these states may have a smaller population, resulting in a lower absolute number of ACT test-takers.


- There is an inverse relationship between test scores and participation rates. In other words, average scores are higher when less students take a test. This is due to selection bias, as the students who choose to take the test when it is not mandatory are the students who are motivated to achieve a high score in order to enter a good college


- The data clearly shows that there is intense competition between the SAT and ACT and that state regulations have a big influence on test participation rates. In the past few years, the College Board had aggressively underbid the ACT to win state contracts and they were successful in capturing market share from ACT in these 3 previously long-standing ACT states: Colorado, Illinois, and Michigan.


- SAT participation rates are also determined by whether the test is free for students to take. In the case of Colorado, Illinois, and Michigan, the SAT is funded by the state. If we postulate that states that fund college admission tests do so because they believe in improving their students' access to higher education, then the College Board would do well to target states that are already funding the ACT (or both the ACT and SAT) as they will have an easier time persuading them to increase their adoption of the SAT.



## Recommendations

I would recommend targeting states with the following criteria:
- **low current SAT participation rates** (in order to maximise increase in participation rate)
- **high ACT participation rates**
- **large population** (to maximise number of new test-takers)
- **high state debts** (the College Board can underbid ACT like it did in Illinois and Colorado, and states with debts would be more incentivised to switch over to the SAT as that would allow them to save on cost)

Based on the above criteria, I would recommend the College Board to target Ohio.

In Ohio, students are mandated to take either the SAT or ACT, although the ACT is the overwhelmingly popular choice (100% participation for ACT 2018 vs 18% for SAT 2018). Ohio is the 7th largest state in the U.S., so there is a sizeable number of test-takers that the College Board can win over if the College Board can convince the Ohio Department of Education to encourage students to take the SAT.

Furthermore, in 2017, Ohio had the 10th highest amount of state debt. If the College Board employs the same strategy of underbidding ACT, Inc. and make the cost of implementing the SAT lower compared to the ACT, they would significantly increase their chances of persuading the Ohio Department of Education to adopt the SAT statewide.

The ACT and SAT are already free for public school students to take. Thus, the main task left for College Board is to explain to the Department of Education why it would be more advantageous for students to take the SAT instead of the ACT.

## Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|ACT/SAT|Name of U.S. state|
|sat_17_participation|float|2017 SAT|Participation rate in SAT for each state|
|sat_17_read_write|int|2017 SAT|Average score for the Evidence-based Reading and Writing (EBRW) section of SAT, between 200 and 800|
|sat_17_math|int|2017 SAT|Average score for the Math section of SAT, between 200 and 800|
|sat_17_total|int|2017 SAT|Total SAT score, combining EBRW and Math sections, between 400 and 1600|
|act_17_participation|float|2017 ACT|Participation rate in ACT for each state|
|act_17_english|float|2017 ACT|Average score for the English section of ACT, between 1 and 36|
|act_17_math|float|2017 ACT|Average score for the Math section of ACT, between 1 and 36|
|act_17_reading|float|2017 ACT|Average score for the Reading section of ACT, between 1 and 36|
|act_17_science|float|2017 ACT|Average score for the Science section of ACT, between 1 and 36|
|act_17_composite|float|2017 ACT|Composite score of ACT, averaging scores from four sections, between 1 and 36|
