## How to get different returns on sequential calls

From the [Github Moq Quickstart](https://github.com/Moq/moq4/wiki/Quickstart#miscellaneous):  
```
var mock = new Mock<IFoo>();
mock.SetupSequence(f => f.GetCount())
    .Returns(3)  // will be returned on 1st invocation
    .Returns(2)  // will be returned on 2nd invocation
    .Returns(1)  // will be returned on 3rd invocation
    .Returns(0)  // will be returned on 4th invocation
    .Throws(new InvalidOperationException());  // will be thrown on 5th invocation
``` 
Using multiple **Returns** return them in the order they have been set up.  
This uses **SetupSequence** instead of **Setup**.  
Please note that this can cause unexpected errors if the code loops and expects more **Returns** than have been set up.
