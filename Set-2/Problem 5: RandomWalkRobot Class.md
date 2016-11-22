iRobot is testing out a new robot design. The proposed new robots differ in that they change direction randomly **after every time step**, rather than just when they run into walls. You have been asked to design a simulation to determine what effect, if any, this change has on room cleaning times.

Write a new class ```RandomWalkRobot``` that inherits from ```Robot``` (like ```StandardRobot```) but implements the new movement strategy. ```RandomWalkRobot``` should have the same interface as ```StandardRobot```.

Test out your new class. Perform a single trial with the ```StandardRobot``` implementation and watch the visualization to make sure it is doing the right thing. Once you are satisfied, you can call ```runSimulation``` again, passing ```RandomWalkRobot``` instead of ```StandardRobot```.

Enter your code for classes Robot and RandomWalkRobot below.

```py
class RandomWalkRobot(Robot):
    """
    A RandomWalkRobot is a robot with the "random walk" movement strategy: it
    chooses a new direction at random at the end of each time-step.
    """
    def updatePositionAndClean(self):
        """
        Simulate the passage of a single time-step.

        Move the robot to a new position and mark the tile it is on as having
        been cleaned.
        """

        self.newPosition = Position.getNewPosition(self.getRobotPosition(), self.robotDirection, self.speed)
        if self.room.isPositionInRoom(self.newPosition):
            self.setRobotPosition(self.newPosition)
            self.room.cleanTileAtPosition(self.getRobotPosition())
            self.setRobotDirection(random.uniform(0, 360))
        else:
            self.setRobotDirection(random.uniform(0, 360))
```
