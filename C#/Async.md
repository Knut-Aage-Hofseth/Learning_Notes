Async methods can be handed over to another thread to complete and can run concurrently with the main program.

Async methods should not return void. Return ``` Task ``` instead. returning task does not need a return statement, but the task is returned to the called thread and this allows checking the state of the task.  

```Await``` is the keyword for the task needs to complete before we can progress further. Can be used at the method call invoked on the returned task if the method was called earlier.
```
            var schemaListTask = GetSchemaList(master, report);
        
            await FindDomainId(master, report);

            // Fetch Schema List
            await schemaListTask;
```