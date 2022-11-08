# Making use of Inheritance in C#


### The *as* keyword

When using inherited classes you might have a parent class as a method parameter, but need to make use of the something from the child class. In case you have not set up for generics in this case, you might use the **as** keyword.

```
protected override async Task PostConnectionRequest(PostConnectionRequest postConnection, UserInputConnection item, MainDatabaseModel master, UserInputReport report)
    {
        var concreteItem = item as ParquetUserInputConnection;
    }
```

This is a method that implements an abstract method from the parent class. We know that we always need an UserInputConnection object. But in this case UserInputConnection have child classes and we need to use a child class here.

For the override to be valid the Type for item needs to be identical, but the method can not get to properties only present in the child of UserInputConnection.  

Using **as** we tell the program that here the object is supposed to be treated as one of its polymorphic family.