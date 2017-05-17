##`O(n^2)` vs. `O(n*lg(n))` - Practical Example

It should be clear now that for any moderately large inputs, algorithms
that run in `O(n*lg(n))` time will significantly outperform those that run
in `O(n^2)`.

![time_complexity](./compareNlogNQuadratic.png)

While one of the goals of algorithm analysis is to stay agnostic of implementation details, let's briefly take a look at what this means in practice. In this demo we'll look at a timed comparison of Merge Sort and Bubble Sort for randomized array inputs of varying sizes.

We have provided a `sorting_demo.rb` script that you may run in your terminal to follow along with this reading. The demo will run 3 trials for each sorting algorithm with a randomized input of increasing size, and compute the total and average time taken to sort the arrays. Note that your running times may vary significantly from those listed here depending on your machine and the result of the array randomizer, but they should grow at roughly the same rate.

Let's start with something small: press any key to run Merge Sort and Bubble Sort for 5 elements. The results here are fairly uninteresting: the running time for both is so small that any differences are negligible.

```
Press any key to benchmark sorts for 5 elements
user     system      total        real
Tot. Merge:    0.000000   0.000000   0.000000 (  0.002130)
Tot. Bubble:   0.000000   0.000000   0.000000 (  0.000069)
Avg. Merge:    0.000000   0.000000   0.000000 (  0.000710)
Avg. Bubble:   0.000000   0.000000   0.000000 (  0.000023)
```

The story is similar when running this for the next batch, 50 elements.

```
Press any key to benchmark sorts for 50 elements
                user     system      total        real
Tot. Merge:    0.000000   0.000000   0.000000 (  0.001046)
Tot. Bubble:   0.000000   0.000000   0.000000 (  0.002036)
Avg. Merge:    0.000000   0.000000   0.000000 (  0.000349)
Avg. Bubble:   0.000000   0.000000   0.000000 (  0.000679)
```

Now let's move on to 500 elements.

```
Press any key to run sorts for 500 elements:
                user     system      total        real
Tot. Merge:    0.010000   0.000000   0.010000 (  0.008129)
Tot. Bubble:   0.080000   0.000000   0.080000 (  0.080440)
Avg. Merge:    0.003333   0.000000   0.003333 (  0.002710)
Avg. Bubble:   0.026667   0.000000   0.026667 (  0.026813)
```

We're beginning to see some separation here between the performance of the two. In practice, though, this doesn't mean much to us. Both are still taking well under a second to run on my machine. What about 5000 elements?

```
Press any key to run sorts for 5000 elements:
                user     system      total        real
Tot. Merge:    0.070000   0.000000   0.070000 (  0.073389)
Tot. Bubble:   8.040000   0.020000   8.060000 (  8.082406)
Avg. Merge:    0.023333   0.000000   0.023333 (  0.024463)
Avg. Bubble:   2.680000   0.006667   2.686667 (  2.694135)
```
At 5000, the times start to properly diverge on my machine. Bubble Sort no longer feels instantaneous. If we were writing an application where the user needed to wait for the results of the sort to continue, this would start significantly affecting their experience.

Can you give a rough estimate of how long Bubble Sort and Merge Sort will take for 50,000 elements? What factors would go into whether your estimate would be high or low? Picking different algorithms to solve a problem can lead to significant differences in application performance at scale.

```
Press any key to run sorts for 50000 elements:
                user     system      total        real
Tot. Merge:    1.010000   0.010000   1.020000 (  1.030560)
Tot. Bubble: 986.350000   5.460000 991.810000 (1004.896369)
Avg. Merge:    0.336667   0.003333   0.340000 (  0.343520)
Avg. Bubble: 328.783333   1.820000 330.603333 (334.965456)
```

We can see that Merge Sort still runs in a reasonable amount of time with 50,000 elements. This becomes less true for Bubble Sort as the element size increases.

When Bubble Sort has finished running, go ahead and play around with the input size a bit more. You can specify the default base (as well as number of runs for averaging) by modifying `SortingDemo::run_performance_tests`. Approximately how long do you estimate it will take to run this for 100,000 elements?
