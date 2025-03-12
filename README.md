# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.


# Answer

In class, we discussed how a pivot is 'good' when it is in the middle 50% of the input array.  
More specifically, the first $\frac{n}{4}$ elements and the elements over $\frac{3n}{4}$ are 'bad'  
pivots. Since the first and last quarters are 'bad,' the middle two quarters would be 'good,' giving a 50% chance  
of finding a good pivot when just choosing randomly.  

The median of three method is better because it gives higher odds of picking a good pivot when choosing one.  

Choosing 3 items randomly from the whole array, each item has two 'states' in this case: good or bad pivot.  
3 items with 2 states nets $2^3 = 8$ possible combinations. The possible combinations are as follows:  

G = good pivot    B = bad pivot
GGG  
GGB  
GBG  
GBB  
BGG  
BGB  
BBG  
BBB  

Some of these are functionally, from a combination standpoint, the same. In particular, the cases where  
two good pivots and one bad are chosen, and one good pivot and two bad ones are chosen. They are not fully  
the same in that second case, which will be addressed later.  

You can figure out the odds of each combination occurring by looking at how many of 8 there are:  

3 goods: $\frac{1}{8}$  
2 goods, 1 bad: $\frac{3}{8}$  
1 good, 2 bads: $\frac{3}{8}$  
3 bads: $\frac{1}{8}$  

Now to look at each case individually.

### 3 Goods

In the case of 3 good pivots, the pivot will be good no matter what.  


### 2 Goods, 1 bad

When 2 good pivots are taken, and one bad pivot is taken, the good pivots would have to be from the middle half of the array.  
This being the case, it does not matter if the bad pivot is taken from the left quarter or the right quarter: the median  
item/index of those three will always be a good pivot, no matter what is done. So, in the case of 2 goods, 1 bad, the pivot will always be 'good.'

### 2 bads, 1 good

When two of the randomly chosen pivots are bad, the order in which they are chosen can matter, making there technically be 4 cases here, rather than the 3 mentioned earlier. It also matters which side of the array the pivots came from.  
When two bad pivots are taken from the left quarter of the array, then the median of the three total will be bad. The same goes for the if both bad pivots are taken from the right quarter of the array. The order for these two cases doesn't really matter; the chosen pivot will be bad.  
When the two bad pivots are taken from opposite quarters of the array, one can be chosen before the other (i.e. bad from the right first, then from the left.) This introduces two 'new' cases: $B_{L}GB_{R}$ and $B_{R}GB_{L}$  
While these are two distinct cases, they are functionally both the same: the pivot will be good, since the median of the three will end up being the good pivot.  
Thus, out of the four cases from 2 bad pivots and one good pivot, two will end up having a good pivot, and two will end up having a bad pivot.  
Therefore, the odds of getting a good pivot from the case of 2 bads, 1 good is $\frac{1}{2}$  

### 3 bads

The pivot will be bad no matter what.  

### Final Probability

To find the final probability, we can add together the odds of each case of the 8 outcomes, multiplying the odds of a good or bad  
pivot for each case.  
(3 goods) $\frac{1}{8} * 1$ + (2 goods 1 bad) $\frac{3}{8} * 1$ + (2 bads, 1 good) $\frac{3}{8} * \frac{1}{2}$ + (3 bads) 0  
This simplifies down to $\frac{1}{8} + \frac{3}{8} + \frac{3}{16}$  which is 0.6875 in decimal form and 68.75% as a percentage.  

This means that the odds of getting a good pivot when using the median of three method has a 68.75% chance to choose a good pivot,  
while choosing randomly has just a 50% chance. Since 68.75% is a larger odd than 50%, the median of three method is better for  
choosing a pivot in a quick sort algorithm.  

I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

Gage Hepworth helped me understand the idea of finding 8 different combinations, as well as looking at each specific case to see the odds of a good pivot from those (most relevant with the 2 bads, 1 good case.)  
