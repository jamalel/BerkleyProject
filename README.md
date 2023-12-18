# Module 5 Report: Will they accept the coupon


## Data Review and cleaning

We started the analysis with reviewing the data set, at first looking at the fields that had missing the values. We noted the following :

- car: 12576
- CoffeeHouse: 217
- Restaurant20To50: 189
- CarryAway: 151
- RestaurantLessThan20: 130
- Bar: 107

To better understand what to do with the rows with missing data, I needed to better understand what those columns represented, so I looked at the value distribution across any of those columns.

First, what immediately stood out was the car column with 99% of the rows missing values in that column. Moreover, the rows with the car column set, had a very small distribution of values: 
- Scooter and motorcycle                     
- Mazda5                                      
- do not drive                                
- crossover
- Car that is too old to install Onstar :D

So, the data that was included was not usable. Hence, I decided to eliminate that column from the data set instead of eliminating the rows. If all the data was present, I probably would’ve had to categorize the cars instead of using the raw values present in the data set.

For the remaining columns, **CoffeeHouse**, **CarryAway**, **Bar**, **Restaurant20To50** and **RestaurantLessThan20**, they all indicated the number of times those establishments are frequented (I’ll refer to those columns as the **“establishment”** columns). 
The **coupon** field indicates the type of establishment the coupon applies to. 

There's two ways to think about this:
1. It’s okay to have a null **“establishment”** column as long as the **coupon** type was not the same. This approach assumes that the rest of the **"establishment"** columns are independent of each other.
2. If we wanted to analyze any correlation between establishment columns, then we can't have any null values to draw  conclusions on that correlation...

We found that there are rows with a blank establishment type that correspond to the coupon type (164 rows to be exact). Plus, and more importantly, we cannot confirm that establishment types are independent, so we decided to purge all rows with null data. 

## Data Analysis

Looking at the overall data set, we found that **57% of all coupons** across all types of establishments were accepted.

Moreover, the coupon types were broken down as follows:
 - Coffee House:  3816
 - Restaurant<20: 2653
 - Carry Out:     2280
 - Bar:           1913
 - Restaurant (2-50): 1417

In this particular analysis, we investigated the acceptance criteria of the Bar coupon and the Coffee House coupon.

### Investigating the bar coupons

We found that overall, only 41% of the coupons were accepted. However, if we focused on those who went to a bar more than 3 times per month, the acceptance ratio was staggering is: 76%.

If we dig deeper into the data, we find that there seems to be a correlation between factors like visit frequency, age, social status, occupation and the acceptance rate. Some of those factors are independent influencers in a positive way, some are independent in a negative way.
In other cases, a combination of factors is required to determine the probablity of acceptance. For example:

#### Independent factors
- **Frequency of visit:** the more a driver visits a bar, the more likely they are to accept the coupon
- **Age and Occupation:** Younger drivers (less than 25) and occupation (farming, fishing, or forestry) are independently less likely to accept bar coupons
- **Passenger:** Drivers whith a child passenger are less likely to accept a coupon

#### Combined factors
- **Frequency, passengers, and status**: Drivers who visit bars more than once a month, had passengers that were not a kid, and were not widowed are more likely to accept coupons
- **Economics**: Drivers that frequent cheap restaurants with an income below 50K/year are less likely to accept a bar Coupon

### Investigating the Coffee House coupon

We found that overall, only 49.6% of the coupons were accepted. 

#### Effect of passenger type on Acceptance
Further analysis shows that those who have non-child passenger in the car are more likely to accept the coupon, but only at a rate of 59.14%. 

But if we focus on the more frequent coffee house goers (even just one more times per month), we find that acceptance rate goes up to: 67.26% and that is for the whole population that received Coffee House coupons.

The acceptance ratio of frequent Coffee House goers and with non-child passenger goes up even further to 75.08%. This is one case where the "passenger" criteria is not very relevant in the general population (slight increase in probability) but much more relevant for those who more often frequented the coffee house.

#### Effect of Weather on Acceptance

We found that the weather has no effect on the general population (split ~50/50 acceptance). 
However, it appears that if solely focus on those who more often frequent a coffee house, the weather is very relevant, and the the acceptance rate drops significantly with rainy and snowy weather. The data showed the following: 
Those who often frequents a Coffee House accept the coupons at a rate of: 
  * 55.00% when the weather is bad
  * 69.0% when the weather is good
  
#### Effect of Expiry date on Acceptance

It appears that, for the general population of those who received coffee coupons, the coupons that expired in 1d were more likely to be accepted than those that expired in 2h.

However, those who less frequently went to Coffee houses, were overall less likely to accept a coupon regardless of whether the coupon expired in 2 hours or 1 day

For those who more frequently went to a coffee house, were still more likely to accept a coupon. However,when we consider the coupon expiration they had  a much higher probability to accept a coupon that expired in 1 day.
