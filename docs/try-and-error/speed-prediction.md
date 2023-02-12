# Attempt 1: Regression
First, I tried regression with other parameters being the out of box.

Here are the results.

It just doesn't work.
Also, every time I try something, values for loss function changes dramatically.

Truthy value ranges from 1e+6 to 1e+23; I assumed that this was the issue.

Possible solutions are,
## Custom Loss Function
I can tailor loss functions to tailored for my need.  
First, *loss* I want is relative to the truthy value;  
For example, if the order's fastest reaction time was 10,000 nano seconds and it was predicted to react in an hour, that's very problematic for me.
However, For example, if the order's fastest reaction time was 2 hours and predicted to react in 3 hours, loss would be almost the same, but the latter is less significant 

For both cases, loss that loss function generates is almost the same, but the wrong-ness is very different.

We 

##