Async methods can be handed over to another thread to complete and can run concurrently with the main program.

Async methods should not return void. Return **Task** instead. returning task does not need a return statement, but the task is returned to the called thread and this allows checking the state of the task.  

**Await** is the keyword for the task needs to complete before we can progress further. Can be used at the method call invoked on the returned task if the method was called earlier.
```
            //Starts the task and assigns it to a variable
            var schemaListTask = GetSchemaList(master, report);

            //Starts a task and awaits it directly
            await FindDomainId(master, report);

            //Waits for the task in the variable to complete before proceeding
            await schemaListTask;
```