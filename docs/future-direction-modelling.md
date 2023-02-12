# Future Direction: Modelling
## Better insight into order activities

I discovered that speed difference leads to difference in execution rate.

If you could more accurately predict the order life-cycle, you should be able to improve your model in one way or another.

I'm thinking of implementing a LSTM-based model which predicts how likely the order's going to end up getting executed.

## Order Flow Analysis

We have seen how different products shown a some-what different result on the execution rate section.

As far as I'm concerned, no one on 2ch.net or wall street bets is talking about Japanese Government Bonds futures but planety of them are talking about about Nikkei contracts.

I think the difference in investor profile is one of the factor contributing to the difference in execution rate; I believe that I will be able to identify the investor profile behind the order-flow by diving deeper into this.

Here are some ideas to identify retail order flow.

## Better Option Analysis

My option analysis was largerly done with Greeks, but I'm pretty sure there are ways to improve this:
Some idea that I can come up with:
- Maturity in minutes/seconds instead of days
- 

## Smaller Time Intervals

## More Data!
You can always have more data.
Some things that I can come up with is:

- Order book for underlying stocks for Nikkei/TOPIX
- Text-data: news headlines, twitter feed ... etc
- Bringing in data from other venues such as CME
- Including data from not-nearest expiry options/futures