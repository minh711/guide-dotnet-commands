# Commands Guide for .NET

This guide provides a step-by-step reference for creating, managing, and running .NET projects with essential CLI commands.

---

## Table of Contents
1. [Create Project](#create-project)
   - [Create a New Solution File](#create-a-new-solution-file)
   - [Add Projects to the Solution](#add-projects-to-the-solution)
     - [Class Library Project](#class-library-project)
     - [Web API Project](#web-api-project)
     - [Web Application (MVC) Project](#web-application-mvc-project)
     - [Web Application (Razor Pages) Project](#web-application-razor-pages-project)
2. [Install Packages](#install-packages)
   - [Install Entity Framework Core (Globally)](#install-entity-framework-core-globally)
   - [Add Package to Project](#add-package-to-project)
3. [Database Management](#database-management)
   - [Connection String Format](#connection-string-format)
   - [Add Migration](#add-migration)
   - [Update Database](#update-database)
4. [Code Generation](#code-generation)
   - [Install Code Generator Tool](#install-code-generator-tool)
   - [Add Code Generation Package](#add-code-generation-package)
   - [Code Generation Usage](#code-generation-usage)
5. [Run and Build](#run-and-build)
   - [Run the Project](#run-the-project)
   - [Build and Check for Errors](#build-and-check-for-errors)
   - [Publish the Project](#publish-the-project)

---

## 1. **Create Project**

### 1.1 Create a New Solution File

To create a solution file in an empty folder:

```bash
dotnet new sln -n SolutionName
```

### 1.2 Add Projects to the Solution

Once the solution file is created, you can add different types of projects to it.

#### 1.2.1 Class Library Project

```bash
dotnet new classlib -n [ProjectName]
```

#### 1.2.2 Web API Project

```bash
dotnet new webapi -n [ProjectName] -controllers
```

#### 1.2.3 Web Application (MVC) Project

```bash
dotnet new mvc -n [ProjectName]
```

#### 1.2.4 Web Application (Razor Pages) Project

```bash
dotnet new razor -n [ProjectName]
```

### 1.3 Add Project to Solution

After creating a project, add it to your solution:

```bash
dotnet sln add [ProjectName]/[ProjectName].csproj
```

## 2. **Install Packages**

### 2.1 Install Entity Framework Core (Globally)

To install EF Core globally:

```bash
dotnet tool install --global dotnet-ef
```

### 2.2 Add Package to Project

To install a package in a specific project:

```bash
dotnet add package [PackageName]
```

For example, adding Entity Framework Core package:

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

## 3. **Database Management**

### 3.1 Connection String Format

To connect to a database, use the following format for the connection string:

```txt
Server={server};Uid={uid};Pwd={pwd};Database={database};Encrypt=true;TrustServerCertificate=True;
```

### 3.2 Add Migration

To create a new migration:

```bash
dotnet ef migrations add [MigrationName] -o [OutputDirectory]
```

For example:

```bash
dotnet ef migrations add InitialCreate -o Migrations
```

### 3.3 Update Database

After creating migrations, update the database:

```bash
dotnet ef database update
```

## 4. **Code Generation**

### 4.1 Install Code Generator Tool

Install the ASP.NET Core code generator tool globally:

```bash
dotnet tool install -g dotnet-aspnet-codegenerator
```

### 4.2 Add Code Generation Package

Add the code generation design package to your project:

```bash
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
```

### 4.3 Code Generation Usage

Generate API controllers with Entity Framework Core:

```bash
dotnet-aspnet-codegenerator -p . controller -name [ControllerName] -api -m [Model] -dc [DbContextClass] -outDir [OutputDirectory] -namespace [Namespace]
```

Example:

```bash
dotnet-aspnet-codegenerator -p . controller -name ProductsController -api -m Product -dc AppDbContext -outDir Controllers -namespace MyApp.Controllers
```

## 5. **Run and Build**

### 5.1 Run the Project

To run the project locally:

```bash
dotnet run
```

### 5.2 Build and Check for Errors

To build the project and check for compilation errors:

```bash
dotnet build
```

### 5.3 Publish the Project

To publish a release build of the project:

```bash
dotnet publish -c Release
```
