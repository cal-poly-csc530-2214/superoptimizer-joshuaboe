# Superoptimizer - jboe

I began by reading Massalin's "Superoptimizer: a look at the smallest program" and skimming Gulwani's "Dimensions in Program Synthesis." I took handwritten notes on Massalin's.

I then forked and cloned the Aha repository. Once I had it available locally and running, I began running the prexisting test programs and observing the outputs. I also played around and wrote my own programs, most of which could not be compiled within the 5 instruction limit.

One of the functions I wrote (josh_count.frag.c) involved a for loop, without a body, that would increment a variable i until the loop finished and then return it. Essentially, it was a roundabout way of returning an integer. The function could have been condensed into one line "return <num>" and have seemingly operated functionally equivalently. When I made the for loop iterate up to 514 times, Aha was able to find optimized instruction sets of size 5 for it. However, when I made the number of iterations slightly larger (524), it failed to find any.
  
I then realized that condensing the functions into single line returns also gave the same result.

I am still wondering why it behaves the way it does. My guess was that it had to do something with the max size of the registers. However, I have not yet reasoned why it would work with 514 but not 524. If the int size was 8 bytes, I might expect odd behavior passing the 512 threshold, but the difference between 514 and 524 seems trivial.

I will continue running more numbers between 514 and 524 to find the first failing integer, and then I will attempt to reason why it behaves this way. I have not yet finished doing so since running the program just takes time.
