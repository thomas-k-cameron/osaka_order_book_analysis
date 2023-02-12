# Future Direction: Technology
## Data Streaming LOB reconstruction
Current implementation requires all the data to be loaded onto the RAM before you start processing.  

It is simple to implement, but it is a terrible choice for performance; 
- Processing Efficiency: You can't start processing the data until it finishes loading up the data, locking you up for at least 60 to 90 seconds in a typical workload
- Instance Cost: Because it requires more RAM you are be forced to use more expensive computer when you ran it on the cloud

Instead of reading the whole thing upfront, I want to read it directly from the IO stream.

I was able to reduce the ram usage by optimizing the memory allocation (which actually allowed me to downsize the instance size, halving the cost), but I should be able to further improve the performance once 

## Parallel Processing for LOB reconstruction

Currently LOB reconstruction is single-threaded; Every ITCH message is read one-by-one to incrementally update the order book.   
Analysis of order book is done with callback functions and it doesn't move forward until all callbacks finishes executing, and callbacks aren't multi-threaded as well.

I considered saving the snapshot of order book for every tick but that would result in extremely huge data: There will be a lot of Storage/Query cost and IO becomes the bottleneck.

I should be able to make it faster/more cost efficient by improving this.

## Generics-based Order Book: Order book for different dataset

Current implementation is designed for ITCH protocol used by the Osaka Exchange and it doesn't work for other formats.

Algorithm for data generation must be re-written to make it work and this is going to be a painful and prone to error.

One thing that I really wanted to do is cross-exchange analysis: It would be interesting to figure out if the model you built for one particular product would work with completely differnet product traded on a completely different venues.

It would be helpful when you want to identify cross-exchange arbitrage opportunity or want to aggregate the trading data from different venues.

e.g. Nikkei 225 future contract on CME and Osaka or something.


