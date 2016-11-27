Write a function that meets the specification below.
```py
def max_contig_sum(L):
    """ L, a list of integers, at least one positive
    Returns the maximum sum of a contiguous subsequence in L """
    #YOUR CODE HERE
```
Paste your entire function in the box below. Do not leave any print statements.
```py
def max_contig_sum(L):
    """ L, a list of integers, at least one positive
    Returns the maximum sum of a contiguous subsequence in L """
    
    return max(
              sum(L[outer:inner]) 
              for outer in range(len(L)+1) 
              for inner in range(outer, len(L)+1)
              )         
```
