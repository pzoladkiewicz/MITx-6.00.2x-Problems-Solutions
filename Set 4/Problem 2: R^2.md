After we create some regression models, we also want to be able to evaluate our models to figure out how well each model represents our data, and tell good models from poorly fitting ones. One way to evaluate how well the model describes the data is computing the model's R^2 value. R^2 provides a measure of how well the total variation of samples is explained by the model.

Implement the function ```r_squared```. This function will take in:

* list, ```y```, that represents the y-coordinates of the original data samples
* ```estimated```, which is a corresponding list of y-coordinates estimated from the regression model

This function should return the computed R^2 value. You can compute R^2 as follows, where ei is the estimated y value for the i-th data point (i.e. predicted by the regression), yi is the y value for the ith data point, and mean is the mean of the original data samples.

![R2](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/83df4c1c72ef01bd64e3ff4af2d2f60c/asset-v1:MITx+6.00.2x_6+3T2016+type@asset+block/r2.PNG)

If you are still confused about R^2 , its [wikipedia page](https://en.wikipedia.org/wiki/Coefficient_of_determination) has a good explanation about its use/how to calculate it.
```py
import numpy as np

def r_squared(y, estimated):
    """
    Calculate the R-squared error term.
    Args:
        y: list with length N, representing the y-coords of N sample points
        estimated: a list of values estimated by the regression model
    Returns:
        a float for the R-squared error term
    """
    error = 0
    mean = 0
    
    for i in range(len(y)):
        error += ((y[i] - estimated[i])**2)
        mean += ((y[i] - np.mean(y))**2)
        
    return 1 - (error / mean)
```
