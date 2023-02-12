Here I write about things that I learned.

# Things that didn't work or wished I've done it differently
## Single Threaded Order Book
ITCH messages has to be processed sequentially, and there is no multi-threading during the simulation process.

My reasoning behind this implementation was to reduce the complexity of the software and allow me to quickly add new features when I need it.


# Things that I learned 
# Cloud Infrastructure and Data Management

# Software Optimization
## Reducing Memory Usage
This one was very tricky for me.  My initial implementation did not account for ram usage; It would have costed me more than twice the amount of money on AWS if I hadn't invested in optimizing ram usage.

Here I write how I managed to reduce the ram usage by over 70%.

- Data structures

Initially, I was using rust's standard library's `BTreeMap`; It is a binary tree map and it consumed around 30 GB of ram with my test data.

I initially suspected a memory leak. After few month, I realized that it was coming form the `BTreeMap` when I tried using `HashMap`.

After reading some code, I realized that rust's `BTreeMap` allocates lots and lots of buffer.

`HashMap` doesn't allocate as much as the `BTreeMap`. 

Eventually, I was able to reduce the memory usage to less than 15 GB by using `Vec`, rust's growable array and manually allocating additional capacity as need it.

- enum
  
Upon initialization, Rust's `enum` consumes the amount of ram that the biggest variant would use.
Allocating inner elemnt's reduced the size of the ram that enum needs to 12 bytes from 134 bytes.  

Allowing me to run tests with less than 10 GB of ram instead of 15GB; This helped me a lot when I wanted to run stuff on my local machine.

## Data Compression