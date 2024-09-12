# Commands guide for .NET

---

Install Entity Framework (global)

```sh
donet tool install --global dotnet-ef
```

---

Connection string

```txt
uid=sa;pwd=123456;encrypt=true;trustServerCertificate=true;
```

---

Add package for code generation

```sh
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
```

Usage

```sh
dotnet-aspnet-codegenerator -p . controller -name [ControllerName] -api -m [Model] -dc [Database Context class] -outDir [Output folder] -namespace [Namespace]
```
