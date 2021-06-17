# Azure Function App Typescript

Use command-line tools to create a Typescript function that responds to HTTP requests. 
After testing the code locally, you deploy it to the serverless environment of Azure Functions.
This is informational. You can skip this entire thing if you already have working `typescript code`.

# Why do this step?
To make sure that you build a function that works

# Based on the following guide from MS
[Create a Typescript function in Azure from the command line](https://docs.microsoft.com/en-us/azure/azure-functions/create-first-function-cli-typescript)

# Installation Prereq

[Install the Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=macos%2Ccsharp%2Cbash#install-the-azure-functions-core-tools)

Example steps for a mac:  

```bash
brew tap azure/functions
brew install azure-functions-core-tools@3
# if upgrading on a machine that has 2.x installed
brew link --overwrite azure-functions-core-tools@3
```

## Create a Function Project
[Create a local Functions project](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=macos%2Ccsharp%2Cbash#create-a-local-functions-project)

1. Create this in subdirectory of where your pulumi project is.  For Example.
   ```bash
     cd azure-function-workshop (where the Pulumi.yaml, **`package.json`**, etc are located. )
     mkdir app
     cd app
   ```
1. Select a worker runtime. Pick # 3
   ```
   Select a number for worker runtime:
    1. dotnet
    2. dotnet (isolated process)
    3. node
    4. python
    5. java
    6. powershell
    7. custom
    Choose option: 3
   ```

1. Select a number for language. Pick # 2 
   ```
   node
    Select a number for language:
    1. javascript
    2. typescript
    Choose option: 2
   ```
   Output
   ```
    typescript
    Writing .funcignore
    Writing package.json
    Writing tsconfig.json
    Writing .gitignore
    Writing host.json
    Writing local.settings.json
    Writing /Users/tusharshah/scratch/temp/.vscode/extensions.json
   ```
1. [Create a function](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=macos%2Ccsharp%2Cbash#create-func).
   To create a function, run the following command:

    ```
     func new
    ```

    You will also be prompted to choose a runtime for the project. Select **9. HTTP trigger**.

    ```
    Select a number for template:
    1. Azure Blob Storage trigger
    2. Azure Cosmos DB trigger
    3. Durable Functions activity
    4. Durable Functions entity
    5. Durable Functions Entity HTTP starter
    6. Durable Functions HTTP starter
    7. Durable Functions orchestrator
    8. Azure Event Grid trigger
    9. Azure Event Hub trigger
    10. HTTP trigger
    11. IoT Hub (Event Hub)
    12. Kafka output
    13. Kafka trigger
    14. Azure Queue Storage trigger
    15. RabbitMQ trigger
    16. SendGrid
    17. Azure Service Bus Queue trigger
    18. Azure Service Bus Topic trigger
    19. SignalR negotiate HTTP trigger
    20. Timer trigger
    ```

   Choose option: **10 HTTP trigger**
        
   Next you will have to name your function.  The default name is: `HttpTrigger`.  
    Here we entered **HelloWorld**  

   ```
    Function name: [HttpTrigger] **HelloWorld**
    Output:
    The function "HelloWorld" was created successfully from the "HTTP trigger" template.
   ```

1. Verify that the function and all the files were created.

   `azure-function-workshop/app#> ls`

   ```
    HelloWorld(This is a directory)  host.json  local.settings.json  package.json  tsconfig.json
   ```

    cd HelloWorld
    azure-function-workshop/app/HelloWorld#>ls -a
   
   ```
      function.json  index.ts
   ```

1. This above is what you will zip up use. 