# Usage

## Prep

Install dotnet core 5.x for your platform. Then run:

`dotnet restore ./site/*.csproj`

# Configuration

## ASP.NET Core

### Connection strings

The ASP.NET Core project is set up so that it uses SQLite during development and PostgreSQL in production. Replace the password in _appsettings.json_ with a more appropriate one.

In _appsettings.Development.json_:

```
{
  "ConnectionStrings": {
    "DefaultConnection": "DataSource=app.db;Cache=Shared"
  },
  "Logging": {
    ...
  }
}
```

In _appsettings.json_:

```
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=postgres;Port=5432;Username=postgres;Password=<changeme>;Database=postgres;"
  },
  "Logging": {
    ...
  },
  "AllowedHosts": "*"
}
```

# Build and run the application in development

This will build and run the appliction in development.  

`cd ./site`  
`ASPNETCORE_ENVIRONMENT=Development dotnet run`

# Build the application for production

This will pull all the build requirements and build your application for deployment to a hosting system.  

`cd ./site`  
`ASPNETCORE_ENVIRONMENT=Production dotnet publish -c Release -o out`


## Run the application in production

`cd ./out`  
`dotnet Site.dll`


