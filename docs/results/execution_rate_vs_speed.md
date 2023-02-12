# 1. It is said that orders from HFTs are more likely to be deleted, instead of getting matched with another order. Do faster orders get deleted more often?
Each scatter plot points represents a probability of an order within a specific range to have the variable `fully_executed` to be true.

To visualize how the likeliness of an order changes under different cirumstances, I have plotted out different variables/subset in different color.

*I'm going to call the probability of order to be `fully_executed` as `Execution Rate`*

Each data point is;

$P(X,A) = n(A_n)/n(S(X)_n)$

Where,  
- $S(X)_n$ = Every order whose value of variable $X$ is between n and n+1 percentile of $X$
- $A_n$ = Number of executed orders within $S_n$
- $n(S_n)$ = Number of observations in $S_n$
- $n(A_n)$ = Number of observations in $A_n$
- $1 \leq n \lt 100$

I have considered some alterantives;
1. Cumulative Probability with line plot  
   I concluded that this would not be ideal when you want to figure out how it is like on different intervals.
2. Lineplot of KDE  
   There are few ways to pick the smoothing and this will greatly affect how the data will be presente; While, I thought that I could just put multiple plots with different smoothing values, it would be pretty messy 

Each color represents different variables;  

- Orange
  Orange is based on the variable `time_passed_since_last_event_max`.  
- Red
  Red is baed on the variable `min_reaction_time`.
- Blue
  Blue is based on the variable `existed_for`.

So, why should we look at these variables?  
Here is my reason for picking these variables:

- Red: `min_reaction_time`  
  This should help us difference between high speed orders and the rest.  
  There is a restriction as explained (here)[TODO!].
  
- Orange: `time_passed_since_last_event_max`  
  HFT won't always traded at the fastest possible speed.   
  If an order that exhibits slower trading speed makes some difference, then that should be interesting.  

- Blue: `existed_for`  
  This should help us how the length of stay affect the execution rate.  
  This variable is the easiest to measure; If this varialbe happens to be useful at predicting the execution rate, I believe that it would be a nice variable that would help building a prediction machine. 


## Result 1: execution rate of all order
While *many* academic literature suggests that HFTs get canceled all the time, the our result shows that execution rate of faster orders are just as high as the slower orders.  

That's interesting!

!["result1"](../images/execution_rate_result1.png)

## Result2: Nikkei 225 and Nikkei 225 Mini Futures
Let's take a look at orders from NK225/NK225M.
Nikkei futures are the most actively traded rroducts on Osaka Exchange.

Execution rate is noticably higher and while you can see higher execution rate on the slower end of the distribution, execution rate is somewhat higher on faster end.

Additionally, excution rate of the orange (`time_passed_since_last_event_max`) is more dynamic; Since we can't see the same on the red, I think we can attribute this to variable, and not `modify_count`.

!["result2"](../images/execution_rate_result2.png)

## Result3: Future Only

Result is similar to that of the NK225/NK225M.  

Around 17% of orders are from NK225/NK225M; I think it is possible that it was not able to capture the features that other instrument has got.

!["result3"](../images/execution_rate_result3.png)

## Result 4: Options Only
While execution rate of options are lower compare to futures in most group, somehow the fastest pint of Red shows the highest execution rate.

Slower/faster orders shows a higher execution rate just like other orders, but execution rate of slower orders are lower compared to futures.

Additionally, we see a slight increase in execution rate for orange around 10^9 ~ 10^10 nano seconds.

!["result4"](../images/execution_rate_result4.png)

## Result 5: Comparing instrument at nearest expiry; JGBL/NK225 Mini/NK225/TOPIX/TOPIX Mini

I picked futures of JGBL/NK225 Mini/NK225/TOPIX/TOPIX Mini traded at nearest expiry date.

JGBL has a mini variant but I decided to exclude it since the volume is very small.

Ornage for TOPIX Mini is scattered across the plot though we can't see that on Red; So the difference should be coming from the difference in measurement, and not from the fact that orders are modified at least once.   

Execution rate for JGBL is higher for all colors; Interestingly the execution rate is the higest around 10^11.

!["result5"](../images/execution_rate_result5.png)

## Discussion
We have seen that how difference in speed, products result in different execution rate.  
While, the method we used here is trivieal, I think it says something.

Additionally, 


### High Execution Rate For Orange: Is it what Flash Boys were talking about?
I read on Flash Boys that HFTs submit order just to keep it in the order book so that they can get the priority when they actually want to have it executed.

I think this can be the reason that the orange is showing high execution rate in some cases.

### differecent execution rate among different instruments
We observed different execution rate among different instrument.
Trend of execution rate for TOPIX mini was noticably different from others. 

I believe that  part of the reason that they exhibit different trend is because of the difference in the people who are trading them.

It is known that TOPIX Mini is popular among retail traders while JGBL is very difficult to trade if you are retail, since popular retail brokers like Rakuten or SBI doesn't offer them.

It should be interesting because this would help us identify the order flow; It could be coming from retail, institutionals, or someone else.

### Future Direction

I believe that this can be useful at predicting the market direction and predicting the future volume, as well as analyzing the activities of market participant such as retail volume ... etc.

I believe that order analysis gives an interesting insight into market.
Here are few things that I believe that I can do to get a better insight;

- Event Processing
  
    We used an aggregate of order events (update, creation, deletion). While this approach simplfies the analysis, you are missing a lot of pieces of information.  

    I would formulate the data into 
    

-  Order flow prediction
  
    As I discussed on [execution rate differecence between instrument](#execution-rate-differecence-between-instrument), I believe that analysis of individual orders helps us understand the order flow.

    I think we can use compare different instruments to extract trends, and draw a conclusion based on when and where these trend appears.

    For example, we know that Game Stop was very very popular among retails especially around the great short squeeze. But we cannot say the same for things like SOFR futures or Euro dollars futures.

    So, we can look at instruments like GME or SOFT futures, figure out whether  find out if there are certain trends that we can only find it on certain group of dataset.

    We've already seen different product exhibits different trend in execution rate, so I think this is a good way to move forward.
  
- Better plotting

  I used scatter plot believing that this is better than other methods that I could come up with.

  I'm pretty sure that there are better ways to do this, so I think
  
  
