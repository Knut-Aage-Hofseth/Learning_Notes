### Mocking Async Methods
  
Async methods returns tasks or valuetasks. This is accomplished by mocking the result. Correct syntax is:
```
mock.Setup(foo => foo.DoSomethingAsync().Result).Returns(true);
```

Example is:
```
var deleteResponse = new Mock<Response>();
deleteResponse.Setup( x => x.Status).Returns(200);
blobClientMock.Setup(x => x.DeleteAsync().Result).Returns(deleteResponse.Object);
```
In this example the method DeleteAsync returns a Task\<Response>. Setting this up requires mocking the response. Adding a value to the Status property. Here a 200 for the HttpResponse code.  
Since we are using the .Result option for mocking the DeleteAsync method we do not have to wrap the response in a Task. The Moq library will do that for us.  
Remember that to return the mocked object we need to return the Mocks Object property.