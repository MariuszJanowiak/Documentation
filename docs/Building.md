# Building & Configuration
### Compilation

#### build
- The project is built using `dotnet build` and **RUN** with `dotnet run`.

#### tests
- Unit and integration tests can be executed using dotnet test. Tests are divided among the API, Application, Domain, and Infrastructure test projects, as well as TestHelpers

***Personally using Visual Studio 2022 which allowed me to do combination of tests (which is starts right after building process) and build by using one from Rebuild or Build option***

### Environment
- The development environment is configured via the launchSettings.json file, which specifies ports (HTTP: 5000, HTTPS: 5001) and launch settings (e.g., automatic Swagger launch).