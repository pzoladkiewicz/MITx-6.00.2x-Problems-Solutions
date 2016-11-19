

In *ps2.py* we provided you with the ```Robot``` class, which stores the position and direction of a robot. For this class, decide what fields you will use and decide how the following operations are to be performed:

* Initializing the object
* Accessing the robot's position
* Accessing the robot's direction
* Setting the robot's position
* Setting the robot's direction

Complete the ```Robot``` class by implementing its methods in *ps2.py*.

**Note**: When a ```Robot``` is initialized, it should clean the first tile it is initialized on. Generally the model these Robots will follow is that after a robot lands on a given tile, we will mark the entire tile as clean. This might not make sense if you're thinking about really large tiles, but as we make the size of the tiles smaller and smaller, this does actually become a pretty good approximation.

Although this problem has many parts, it should not take long once you have chosen how you wish to represent your data. For reasonable representations, a *majority of the methods will require only a couple of lines of code*.)

**Note**: The ```Robot``` class is an abstract class, which means that we will never make an instance of it. Read up on the Python docs on abstract classes at [this link](http://docs.python.org/3/library/abc.html) and if you want more examples on abstract classes, follow [this link](http://julien.danjou.info/blog/2013/guide-python-static-class-abstract-methods).

In the final implementation of ```Robot```, not all methods will be implemented. Not to worry -- its subclass(es) will implement the method ```updatePositionAndClean()```

Enter your code for classes ```RectangularRoom``` (from the previous problem) and ```Robot``` below.
