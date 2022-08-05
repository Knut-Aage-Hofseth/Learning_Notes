## Using Environment Variable in Unit testing

### First solution
This is probably not the proper way to do things.  

Environment variables are not set at the initialization of testing.
Quick and dirty workaround is to set them manually with:
```
Environment.SetEnvironmentVariable("VariableName", "VariableValue");
```  
This needs to be set inside each test when done with this method. Because of this making a **Static** method collecting all the **Environment Variables** we need and just call that in the tests needing it seems like a good idea.