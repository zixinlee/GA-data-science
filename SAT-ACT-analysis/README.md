# How to increase SAT participation rate?

## Introduction

In the U.S., the SAT and ACT are the two most well-known standardised tests used for admission into colleges or universities. The SAT was introduced to the U.S. in 1926 whereas the ACT was introduced in 1959 as a competitor to the SAT.

The SAT has traditionally been the most popular college admissions test in the U.S., but in the past decade, the ACT had gained significant ground and between 2012 and 2017, it overtook the SAT as the most widely used college admissions test.

To win back its market share, the College Board implemented major changes to the format of the SAT and aggressively bade for statewide contracts to administer the SAT tests amongst high school students. In 2018, the College Board's efforts finally paid off and the SAT surpassed the ACT to become the dominant college admissions test once more.


## Problem Statement
In this project, we examine the ACT and SAT scores and participation rates by state in 2017 and 2018 to identify a specific state that the College Board can target to drive higher SAT participation rates going forward.


## Key Takeaways

- **Inverse relationship between SAT vs. ACT participation rates**<BR>
SAT and ACT participation rates have an inverse relationship, as seen from the general downward sloping trend below. This is expected as the two tests are usually substitutes of one another, thus a higher participation in one test would see a lower participation in the other.


- **There were more SAT than ACT test-takers in 2018, but ACT still enjoys greater popularity in more states.** <BR>This is possible because 1/3 of all U.S. states have a 100% ACT participation rate. These states may have a smaller population, resulting in a lower absolute number of ACT test-takers. Still, what's important to note here is that the ACT is dominant in more states than the SAT.


- **State regulations have a big influence on test participation rates.** <BR>In the past few years, the College Board had aggressively underbid the ACT to win state contracts and they were successful in capturing market share from ACT in Colorado and Illinois, which were previously longstanding ACT-taking states. SAT participation rates shot up in both states after the SAT became a requirement. As part of high school accountability, the SAT was state-funded for students to take for free.


- **Free testing significantly boosts participation rate.** <BR>As seen, state-funding dramatically boosted SAT participation in Illinois and Colorado as students were more likely to take the free SAT than the paid ACT. The College Board would do well to target states that are already funding the ACT or other college admission tests and convince them to adopt (and fund) the SAT instead. This would allow the SAT to be taken by a wider group of students, e.g. students from lower-income families who would not have taken the SAT if it were not free and state-required.


### Final recommendation: Target Ohio


- **Large population:** Ohio is the 7th largest state in the U.S., so there is a sizeable number of new test-takers that the College Board can acquire.


- **Relatively low current SAT participation rates:** From 2017 to 2018, Ohio increased both its ACT and SAT participation after it became compulsory to take either test. However, the increase was larger for the ACT, i.e. from 75% to 100%, whereas for SAT it was from 12% to 18%. Thus, there is still considerable room for growth for the SAT.


- **High state debts:** In 2017, Ohio had the 10th highest amount of state debt. If the College Board employs the same strategy of underbidding ACT, Inc. and make the cost of implementing the SAT lower compared to the ACT, they would increase their chances of persuading the Ohio Department of Education to adopt the SAT statewide.


- **Free to take the ACT or SAT:** The ACT and SAT are already free for public school students to take. Thus, the main task left for College Board is to explain to the Department of Education why it would be more beneficial for students to take the SAT instead of the ACT.


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
