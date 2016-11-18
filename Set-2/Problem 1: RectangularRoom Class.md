You will need to design two classes to keep track of which parts of the room have been cleaned as well as the position and direction of each robot.

In ps2.py, we've provided skeletons for the following two classes, which you will fill in in Problem 1:

* ```RectangularRoom```: Represents the space to be cleaned and keeps track of which tiles have been cleaned.
* ```Position```: We've also provided a complete implementation of this class. It stores the x- and y-coordinates of a robot in a room.
Read ps2.py carefully before starting, so that you understand the provided code and its capabilities.

####PROBLEM 1

In this problem you will implement the ```RectangularRoom``` class. For this class, decide what fields you will use and decide how the following operations are to be performed:

* Initializing the object
* Marking an appropriate tile as cleaned when a robot moves to a given position (casting floats to ints - and/or the function ```math.floor``` - may be useful to you here)
* Determining if a given tile has been cleaned
* Determining how many tiles there are in the room
* Determining how many cleaned tiles there are in the room
* Getting a random position in the room
* Determining if a given position is in the room
Complete the ```RectangularRoom``` class by implementing its methods in ps2.py.

Although this problem has many parts, it should not take long once you have chosen how you wish to represent your data. For reasonable representations, *a majority of the methods will require only a couple of lines of code*.)

***Hint***: During debugging, you might want to use ```random.seed(0)``` so that your results are reproducible.

Enter your code for ```RectangularRoom``` below.
