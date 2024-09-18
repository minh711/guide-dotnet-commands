# Commands Guide for .NET

This guide provides a step-by-step reference for creating, managing, and running .NET projects with essential CLI commands.

---

## Table of Contents
1. [1. Create Project](#1-create-project)
   - [1.1 Create a New Solution File](#11-create-a-new-solution-file)
   - [1.2 Add Projects to the Solution](#12-add-projects-to-the-solution)
     - [1.2.1 Class Library Project](#121-class-library-project)
     - [1.2.2 Web API Project](#122-web-api-project)
     - [1.2.3 Web Application (MVC) Project](#123-web-application-mvc-project)
     - [1.2.4 Web Application (Razor Pages) Project](#124-web-application-razor-pages-project)
2. [2. Install Packages](#2-install-packages)
   - [2.1 Install Entity Framework Core (Globally)](#21-install-entity-framework-core-globally)
   - [2.2 Add Package to Project](#22-add-package-to-project)
3. [3. Database Management](#3-database-management)
   - [3.1 Connection String Format](#31-connection-string-format)
   - [3.2 Add Migration](#32-add-migration)
   - [3.3 Update Database](#33-update-database)
4. [4. Code Generation](#4-code-generation)
   - [4.1 Install Code Generator Tool](#41-install-code-generator-tool)
   - [4.2 Add Code Generation Package](#42-add-code-generation-package)
   - [4.3 Code Generation Usage](#43-code-generation-usage)
5. [5. Run and Build](#5-run-and-build)
   - [5.1 Run the Project](#51-run-the-project)
   - [5.2 Build and Check for Errors](#52-build-and-check-for-errors)
   - [5.3 Publish the Project](#53-publish-the-project)

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
