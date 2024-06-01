# Razor Pages Movie Application

This is a simple Razor Pages web application for managing a movie database. The project demonstrates how to build and run an ASP.NET Core web application, manage HTTPS certificates, and use Entity Framework Core for database operations.

## Building the Project

To create a new Razor Pages web application, run the following commands:

```sh
dotnet new webapp -o RazorPagesMovie
code -r RazorPagesMovie
```

## Trusting the ASP.NET Core HTTPS Development Certificate
To trust the ASP.NET Core HTTPS development certificate on Windows and macOS, run:

```sh
dotnet dev-certs https --trust
```

For more options, use:

```sh
dotnet dev-certs https --help
```
## Trusting the HTTPS Certificate on Linux
To trust the HTTPS certificate on Linux, use linux-dev-certs:

```sh
dotnet tool update -g linux-dev-certs
dotnet linux-dev-certs install
```

## Running the Web Application
To run the web application, navigate to the project directory and start the application:

```sh
cd RazorPagesMovie
dotnet watch run
```

## Adding NuGet Packages and EF Tools
Install the necessary NuGet packages and Entity Framework tools by running the following commands:

```sh
dotnet tool uninstall --global dotnet-aspnet-codegenerator
dotnet tool install --global dotnet-aspnet-codegenerator
dotnet tool uninstall --global dotnet-ef
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.SQLite
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
```

## Scaffolding the Movie Model
To scaffold the movie model, use the following command:

```sh
dotnet aspnet-codegenerator razorpage -m Movie -dc RazorPagesMovie.Data.RazorPagesMovieContext -udl -outDir Pages/Movies --referenceScriptLibraries --databaseProvider sqlite
```

```sh
dotnet aspnet-codegenerator razorpage -h
```

Parameters:

-m: The name of the model.
-dc: The DbContext class to use, including namespace.
-udl: Use the default layout.
-outDir: The relative output folder path to create the views.
--referenceScriptLibraries: Adds _ValidationScriptsPartial to Edit and Create pages.

## Creating the Initial Database Schema
To create the initial database schema using EF's migration feature, run:

```sh
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## Adding a New Field Migration
To add a new field and update the database schema, run:

```sh
dotnet ef migrations add rating
dotnet ef database update
```

## Optional: Dropping and Recreating the Database
If needed, you can drop and re-create the database for other providers:

```sh
dotnet ef database drop
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## This README.md file provides a comprehensive guide to setting up, running, and managing the Razor Pages Movie application. Follow these instructions to get started with your project.
