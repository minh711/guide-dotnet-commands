# Commands guide for .NET

## Install packages

Install Entity Framework (global)

```sh
donet tool install --global dotnet-ef
```

## Database

Connection string

```txt
Server={server};Uid={uid};Pwd={pwd};Database={database};Encrypt=true;TrustServerCertificate=True;
```

Add migartion

```sh
dotnet ef migrations add [Migartion name] -o [Output direction]
```

Update database

```sh
dotnet ef database update
```

## Code generation

Add package for code generation

```sh
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
```

Usage

```sh
dotnet-aspnet-codegenerator -p . controller -name [ControllerName] -api -m [Model] -dc [Database Context class] -outDir [Output folder] -namespace [Namespace]
```
