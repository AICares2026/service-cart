## Stack
Languages: C# (.NET)
Frameworks: ASP.NET Core (version undetected, check .csproj TargetFramework)
Test suite present; test runner inferred from NuGet packages in .csproj files

## Constraints
Never modify:
- `*.lock` files (packages.lock.json, nuget.lock.json)
- `Migrations/` directories and any file matching `*_Migration.cs` or `*Migration.cs`
- `*.Designer.cs` and `*.g.cs` generated files
- `appsettings*.json` files containing credentials or connection strings
- `.github/` workflows unless the task explicitly targets CI
- `global.json` (controls SDK version pinning)

## Conventions
- Tests live in projects with `Test` or `Tests` in the project/folder name
- Test classes named `<Subject>Tests.cs`, test methods follow `MethodName_Scenario_ExpectedResult` or similar
- Source projects are separate from test projects; solution file (`.sln`) at repo root
- NuGet package references declared with `<PackageReference>` in `.csproj` files
- One class per file; filename matches class name

## Dependency manifests
- `**/*.csproj` — all NuGet `<PackageReference>` entries live here
- `global.json` — .NET SDK version constraint (if present)
- `packages.lock.json` — lockfile, read-only
