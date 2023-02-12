# Overview 


# Table of Contents

## [Order Activity and Market Movement](./results/order-activity-and-market-movement.md)  

   Can you observe higher market volume or market movement when the order book is more active?

   We are going to measure the active-ness of the order book by order deletion, creation and updates.


## [Are they more likely to get executed?](./result/execution_rate_vs_speed.md)  
  
  It is said that orders from HFTs are more likely to be deleted, instead of getting executed.  
  We are going to call the probability of order to be executed as `execution rate`

  Let's check how difference in order speed affects the execution rate. 
  
  We discover that hile slower order shows higher execution rate, execution rate increases on the faster orders as well; Additionally, we observe that execusion rate differs depending on order.

## [Order book modeling and market prediction](./results/prediction.md)  
  
  Based on what we learned above, we will create a order book model and feed that to the machine learning algorithm to try to predict the market movement.

  We are going to take advantage of Amazon Web Service to process large volume of data.


## [Things that didn't work](./result/things-that-didnt-work.md)  

## [Conclusion](./result/conclusion.md)


