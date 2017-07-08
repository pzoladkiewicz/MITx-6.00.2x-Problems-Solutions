##### Part 3: Compare the Algorithms

Implement '''compare_cow_transport_algorithms'''. Load the cow data in *ps1_cow_data.txt*, and then run your greedy and brute force cow transport algorithms on the data to find the minimum number of trips found by each algorithm and how long each method takes. Use the default weight limits of 10 for both algorithms. Make sure you’ve tested both your greedy and brute force algorithms before you implement this!

Hints:

  You can measure the time a block of code takes to execute using the ```time.time()``` function as follows. This prints the duration in seconds, as a float. For a very small fraction of a second, it will print 0.0.    
```python
start = time.time()
## code to be timed
end = time.time()
print(end - start)
```
  Using the given default weight limits of 10 and the given cow data, both algorithms should not take more than a few seconds to run.

```python
def compare_cow_transport_algorithms():
    """
    Using the data from ps1_cow_data.txt and the specified weight limit, run your
    greedy_cow_transport and brute_force_cow_transport functions here. Use the
    default weight limits of 10 for both greedy_cow_transport and
    brute_force_cow_transport.

    Print out the number of trips returned by each method, and how long each
    method takes to run in seconds.

    Returns:
    Does not return anything.
    """
    startGreedy = time.time()
    greedyTrips = greedy_cow_transport(cows, limit)
    endGreedy = time.time()
    durationGreedy = endGreedy - startGreedy

    startBrute = time.time()
    bruteTrips = brute_force_cow_transport(cows, limit)
    endBrute = time.time()
    durationBrute = endBrute - startBrute

    print('Greedy: trips - ', len(greedyTrips), 'duration - ', durationGreedy)
    print('Brute: trips - ', len(bruteTrips), 'duration - ', durationBrute)
```
