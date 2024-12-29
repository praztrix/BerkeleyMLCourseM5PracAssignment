### Required Assignment 5.1: Will the Customer Accept the Coupon?

**Context**

Imagine driving through town and a coupon is delivered to your cell phone for a restaurant near where you are driving. Would you accept that coupon and take a short detour to the restaurant? Would you accept the coupon but use it on a subsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaurant? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?

Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

**Overview**

The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

**Data**

This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then ask the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’.  There are five different types of coupons -- less expensive restaurants (under \$20), coffee houses, carry out & take away, bar, and more expensive restaurants (\$20 - $50).

**Deliverables**

Your final product should be a brief report that highlights the differences between customers who did and did not accept the coupons.  To explore the data you will utilize your knowledge of plotting, statistical summaries, and visualization using Python. You will publish your findings in a public facing github repository as your first portfolio piece.


### Files:
1. READ.md
2. prompt.ipynb
3. data/coupons.csv



### 2. Investigate the dataset for misssing or problematic 

1. Remove duplicate rows
2. Fix spelling mistake for the passangar column by renaming it to passenger.
3. Remove the column toCoupon_GEQ5min as its  values remain the same for all rows.
4. Drop the column direction_opp as it is the inverse of the column direction_same.


### 3. Decide what to do about your missing data -- drop, replace, other...

#### Check for null values 

1. Drop the 'car' column as 99.14% of the column values are null.
2. We can drop rows with null values for  columns (Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, Restaurant20To50 ) as they contribute to contribute to only 4.78% of the total row count.


### 4. What proportion of the total observations chose to accept the coupon?
57% of the customers decided to accept the coupon

### 5. Use a bar plot to visualize the coupon column.
#### Observations:

  Box plot gives the statistical estimate of the 'Y' column. Since the default estimator is mean and  column Y has only 0 and 1 as values, this plot shows the acceptance rate for each coupon category

1. Carry out and Take away & Restaurant (<20)  coupons have excellent acceptance rates of over 70%.
2. Bar coupons have the lowest acceptance rate of about 41%.
3. CoffeeHouse and Restaurant(20-50) have coupon acceptance rates of 49.56% and 44.65% respectively.


### 6. Use a histogram to visualize the temperature column.
#### Histrogram for temperature columns and acceptance rate
1. The temperature column has only 3 values - 30F, 55F and 80F
2. On relative terms, more coupons were offerred at higher temperatures - 51.3%  at 80F, 30.3% at 55F and 18.2% at 30F
3. About 53% of coupons were accepted in Winter (temperature=30F, 55F) and about 60% of coupons were accepted in Summer (temperature=80F)
#### Histrogram for temperature columns and coupon types
1. Maximum number of Carry and Takeaway coupons were offerred in Winter (30F)
2. Maximum number of Coffee House coupons were offerred when the temperature was 55F and 80F

## Investigating Bar Coupons
### 2. What proportion of bar coupons were accepted?
41% of bar coupons were accepted.
### 3. Compare the acceptance rate between those who went to a bar 3 or fewer times a month to those who went more.
1. The acceptance rate for those who go to the bar 3 or fewer times is 37%
2. The acceptance rate for those who go to the bar more than 3 times is 76%

### 4. Compare the acceptance rate between drivers who go to a bar more than once a month and are over the age of 25 to the all others.  Is there a difference?
1. Acceptance rate for those driver who go to the bar more than once a month and is over 25 years of age is 69%
2. Acceptance rate for others is 34%.
### 5. Use the same process to compare the acceptance rate between drivers who go to bars more than once a month and had passengers that were not a kid and had occupations other than farming, fishing, or forestry.
1. Acceptance rate for drivers who go to bars more than once a month and had passengers that were not a kid and had occupations other than farming, fishing, or forestry is 70.94%
### 6. Compare the acceptance rates between those drivers who:

- go to bars more than once a month, had passengers that were not a kid, and were not widowed *OR*
- go to bars more than once a month and are under the age of 30 *OR*
- go to cheap restaurants more than 4 times a month and income is less than 50K.

1. The acceptance rate for drivers who goes to bars more than once a month, had passengers that were not a kid, and were not widowed is 70.94%
2. The acceptance rate for drivers who goes to bars more than once a month and are under the age of 30 is 71.95%
3. The acceptance rate for drivers who goes to cheap restaurants more than 4 times a month and income is less than 50K is 46.83%
### 7.  Based on these observations, what do you hypothesize about drivers who accepted the bar coupons?

1.  Based on these observations, I see that drivers who go to bars more than once a month has an acceptance rate of 68.5%.
2. In order to better understand how bar visit frequency correlate to  other features , I am going to call corr() func on the bar coupon dataframe. In order to use the function, I need to convert categorical column into a numerical column by using one hot encoding method.

### The heat map shows the following for those who received the Bar coupon.
1. Going to Bar more than once has a positive coorelation to acceptance
2. The correlation to acceptance for someone going to the bar 1-3 times is more than someone going to bar 4-8 times is more than someone going to the bat more than 8 times.
3. temperature and same_direction also correlate positively the acceptance decision.

## Independent Investigation

Using the bar coupon example as motivation, you are to explore one of the other coupon groups and try to determine the characteristics of passengers who accept the coupons.  

### Analyze the 'Restaurant(<20)' coupons

1. 71% of offerred Restaurant(<20) coupons were accepted

### 1. How many drivers accepted the Restaurant(<20) when the weather was Sunny and the passenger was Alone ?
1. Acceptance rate for Restaurant(<20) coupons when the weather was Sunny and the passenger was Alone is 75%

### 2. How many drivers accepted the Restaurant(<20)  when the weather was not Sunny and the passenger was Alone ?
1. Acceptance rate for Restaurant(<20) coupons  when the weather was not Sunny and the passenger was Alone is 35%

### 3. How many drivers accepted the Restaurant(<20)  when the weather was Sunny and coupon expiration was 1d?
1. Acceptance rate for Restaurant(<20) coupons  when the weather was Sunny and the expiration is 1d is 85%

### 4. How many drivers accepted the Restaurant(<20)  when the weather was Sunny and coupon expiration was 2h?
1. Acceptance rate for Restaurant(<20) coupons  when the weather was Sunny and the expiration is 2h is 68%

### 5. How many drivers accepted the Restaurant(<20)  when the  distance to the restaurant was 25 mins and coupon expiration was 2h?
1. Acceptance rate for Restaurant(<20) coupons  when the distance to the restaurant is 25 mins and the coupon is 2h is 27%




#### Let's look at the distribution of acceptance for all categorical features using count plots.<br>
#### Based on the distribution, we can observe that they are more likely to accept 'Restaurant < 20' Coupon when

1. The weather is sunny. Higher number of coupons were offerred in sunny weather and acceptance rate is also high as compared to snowy & rainy weathers.
2. The destination is 'No Urgent Place'
3. Coupon expiration time is 1 day

**I am not sure why I am seeing '0' near the first label for all distribution plots. I would appreciate the grader's help in figuring out what I need to change in the annotate function for fixing it.** 

#### Heatmap for Restaurant < 20' Coupons

We can draw a heatmap for correlating acceptance for integer features using the dataframe corr function. We can  use one hot encoding to split up some of the categorical variables so that they can be represented in the heatmap for correlation.

##### Observations from Heatmap for Restaurant < 20' Coupons

1. We see higher correlation to acceptance when the weather is Sunny, destination is 'No Urgent Place' and the coupon expiration is 1 day
2. Temperature  has good coorelation with the acceptance rate.
3. The coupon has negative correlation when the restaurant is 25 mins away and the coupon expiry time is 2 hours.


### Finding Correlation between Categorical Variables using Chi-Square Test
We can also use Chi-Square test to find correlation between categorical variables. In this test, we estimate the probability of null hypotheses. The null hypothesis assumes that two categorical variables are not correlated. When the probability of the null hypothesis is < 0.05 then the two categorical variables are correlated to each other.

In order to find which features are contributing to acceptance, we need to figure out features that correlate to the acceptance column Y. Since we have a lot of categorical features and the acceptance column can be considered a binary categorical column, we can use the chi-square test to find correlation between two categorical variables.


