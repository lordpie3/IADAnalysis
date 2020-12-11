# IAD Analysis
## Purpose
This program is an attempt to quantify the effectiveness of an IAD (integrated air defense) for Wargame: Red Dragon using raw accuracy as the primary metric.  Range, launch angle, and other factors of anti-air are not addressed here.  The program has the capability to generate and save plots for missile based IADs, and it can calculate the mean damage of SPAAGs.  This analysis applies to both planes and helicopters.

## Mathematics
The underlying mathematics of these calculations is straight forward.  The problem can be viewed in terms of flipping a coin.  When a missile is fired at a plane, there are two outcomes: it hits or it misses.  Because of ingame factors, the probability to hit or miss not guaranteed to be 50%, so firing a missile is equivalent to flipping a weighted coin; furthermore, each missile fired does not necessarily share the same accuracy statistics.  Thus, firing multiple missiles is equivalent to flipping weighted coins.  In most scenarios, the damage associated with each missile is of less concern than how many missiles have a positive result--we tend to care more about how many heads or tails we have rather than the total cost of all the coins who display heads.  To capture this, a [poisson binomial distribution](https://en.wikipedia.org/wiki/Poisson_binomial_distribution) is employed.

The same mathematical formalism is carried out with SPAAGs under a slight modification.  A player is typically not concerned with how many times a SPAAG or SPAAGs hit when firing one shot.  This is due to the low damage of a SPAAG shot in comparison to a missile.  Rather, a player is typically concerned with the mean damage done over some time period along with the associated variance.  Calculating this is identical to the missile case with the exception that SPAAG damage needs to be accounted.

## Credit
I would like to credit the [armory tool](https://github.com/pvutov/armory) by letting me access ingame unit details without forcing me to write that code myself.
