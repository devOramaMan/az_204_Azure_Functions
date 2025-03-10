# az_204_Azure_Functions
In this exercise, you learn how to create a C# function that responds to HTTP requests. After creating and testing the code locally in Visual Studio Code, you'll deploy to Azure ([Resorce](https://learn.microsoft.com/nb-no/training/modules/develop-azure-functions/5-create-function-visual-studio-code)).

# Pre req
- .net 8
- Azure function core tools

# Lets step dance
1)  In Visual Studio Code, press F1 to open the command palette and search for and run the command Azure Functions: Create New Project....

```
- Select a language: Choose C#.
- Select a .NET runtime: Choose .NET 8.0 Isolated (LTS)
- Select a template for your project's first function: Choose HTTP trigger.1
- Provide a function name: Type HttpExample.
- Provide a namespace: Type My.Function.
- Authorization level: Choose Anonymous, which enables anyone to call your function endpoint.
- Select how you would like to open your project: Select Open in current window.
```

2) Press F5 to start the function app project in the debugger. Output from Core Tools is displayed in the Terminal panel. Your app starts in the Terminal panel. You can see the URL endpoint of your HTTP-triggered function running locally.
Outputs Azure function terminal:
``` bash
[2025-03-10T13:28:40.424Z] Found C:\cygwin64\home\andreas.derasmo\az_204_Azure_Functions\az_204_Azure_Functions.csproj. Using for user secrets file configuration.
[2025-03-10T13:28:53.619Z] Worker process started and initialized.

Functions:

        HttpExample: [GET,POST] http://localhost:7071/api/HttpExample

For detailed output, run func with --verbose flag.
[2025-03-10T13:28:55.536Z] Unable to update the debug sentinel file.
[2025-03-10T13:28:58.586Z] Host lock lease acquired by instance ID '000000000000000000000000BE0B442D'.
```

3) With Core Tools running, go to the Azure: Functions area. Under Functions, expand Local Project > Functions. Right-click the HttpExample function and choose Execute Function Now....  enter request body { "name": "Azure" }.
   
```
[2025-03-10T13:50:32.743Z] Executing 'Functions.HttpExample' (Reason='This function was programmatically called via the host APIs.', Id=e7e81d21-9f30-4b28-baad-3ba3fb20144f)
[2025-03-10T13:50:33.299Z] C# HTTP trigger function processed a request.
[2025-03-10T13:50:33.304Z] Executing OkObjectResult, writing value of type 'System.String'.
[2025-03-10T13:50:33.381Z] Executed 'Functions.HttpExample' (Succeeded, Id=e7e81d21-9f30-4b28-baad-3ba3fb20144f, Duration=656ms)
```

4) shift + F5 to stop azure debugger
5) Sign in and create function App in Azure... (use small letters, no wide space and special char or num)
6) (update/refesh button to verify creation under function app)
7) Deploy azure function: Ctrl+Shift+P - Azure Functions: Deploy to Function App... enter request body { "name": "Azure" }.
output:
```
Executed function "HttpExample". Response: "Welcome to Azure Functions!"
```

NB delete recources (az resource list)
``` bash
az group delete --name azfunctestnumto
```

