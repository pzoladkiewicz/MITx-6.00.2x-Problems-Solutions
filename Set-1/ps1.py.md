
```
###########################
# 6.00.2x Problem Set 1: Space Cows 

from ps1_partition import get_partitions
import time

#================================
# Part A: Transporting Space Cows
#================================

def load_cows(filename):
    """
    Read the contents of the given file.  Assumes the file contents contain
    data in the form of comma-separated cow name, weight pairs, and return a
    dictionary containing cow names as keys and corresponding weights as values.

    Parameters:
    filename - the name of the data file as a string

    Returns:
    a dictionary of cow name (string), weight (int) pairs
    """

    cow_dict = {}

    f = open(filename, 'r')
    
    for line in f:
        line_data = line.split(',')
        cow_dict[line_data[0]] = int(line_data[1])
    return cow_dict


# Problem 1
def greedy_cow_transport(cows,limit=10):
    """
    Uses a greedy heuristic to determine an allocation of cows that attempts to
    minimize the number of spaceship trips needed to transport all the cows. The
    returned allocation of cows may or may not be optimal.
    The greedy heuristic should follow the following method:

    1. As long as the current trip can fit another cow, add the largest cow that will fit
        to the trip
    2. Once the trip is full, begin a new trip to transport the remaining cows

    Does not mutate the given dictionary of cows.

    Parameters:
    cows - a dictionary of name (string), weight (int) pairs
    limit - weight limit of the spaceship (an int)
    
    Returns:
    A list of lists, with each inner list containing the names of cows
    transported on a particular trip and the overall list containing all the
    trips
    """

    output = []

    def getKey(item):
        return item[1]

    cowsSorted = sorted(cows.items(), key=getKey, reverse=True)
            
    def findCowSet(c, w):
        weight = 0
        ret = []
        for cow in c:
            if weight + cow[1] <= w:
                weight += cow[1]
                ret.append(cow[0])
        return ret
     
    while len(cowsSorted) > 0:
        cowSet = findCowSet(cowsSorted, limit)
        output.append(cowSet)
        
        if cowSet:
            for i in cowSet:    
                for j in cowsSorted:
                    if i == j[0]:
                        cowsSorted.remove(j)

    
    return output


# Problem 2
def brute_force_cow_transport(cows,limit=10):
    """
    Finds the allocation of cows that minimizes the number of spaceship trips
    via brute force.  The brute force algorithm should follow the following method:

    1. Enumerate all possible ways that the cows can be divided into separate trips
    2. Select the allocation that minimizes the number of trips without making any trip
        that does not obey the weight limitation
            
    Does not mutate the given dictionary of cows.

    Parameters:
    cows - a dictionary of name (string), weight (int) pairs
    limit - weight limit of the spaceship (an int)
    
    Returns:
    A list of lists, with each inner list containing the names of cows
    transported on a particular trip and the overall list containing all the
    trips
    """
    output = []

    # worst scenario - we need as many trips as number of cows
    bestTrips = len(cows)
    
    # for every combination of set of cows
    for cowSet in (get_partitions(cows)):
        weight = 0 
        
        # for every list of cows in combination
        for c in cowSet:
            tempW = 0
            
            # for every cow in list
            # sum cows temp weight
            # and if it is larger than previous previous list
            # make it largest
            for x in c:
                tempW += cows[x]
            if tempW > weight: weight = tempW

        # if cow set weight is in cargo limit
        if weight <= limit:
            
            # if number of trips if better than previous
            # clear transport list and start new one
            # otherwise..
            if len(cowSet) < bestTrips:
                output = []
                bestTrips = len(cowSet)
                output.append(cowSet)
            # if numbet of trips is equal
            # just add set to possible combinations
            elif len(cowSet) == bestTrips:
                output.append(cowSet)

                
    return output

        
# Problem 3
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
    

"""
Here is some test data for you to see the results of your algorithms with. 
Do not submit this along with any of your answers. Uncomment the last two
lines to print the result of your problem.
"""

cows = load_cows("ps1_cow_data_kopia.txt")
limit=10
print(cows)
#
#print('greedy', greedy_cow_transport(cows, limit))
#print('brute ', brute_force_cow_transport(cows, limit))

compare_cow_transport_algorithms()

```
