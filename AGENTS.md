## Stack
Languages: C# (.NET — version undetected, inspect .csproj TargetFramework before assuming)
Frameworks: likely ASP.NET Core (cart service pattern)
Test framework: inspect .csproj for xUnit, NUnit, or MSTest references before running tests

## Constraints
Never modify:
- `*.lock` files (packages.lock.json, etc.)
- `**/Migrations/**` — all EF Core migration files
- `**/*.Designer.cs` — generated designer files
- `**/*.g.cs`, `**/*.generated.cs` — any generated code
- `appsettings.Production.json`, `appsettings.*.json` containing secrets
- `.github/**`, `Dockerfile`, `docker-compose*.yml` — deployment config
- `**/*.pfx`, `**/*.key`, `**/*.pem` — credential/certificate files

## Conventions
- Test projects: look for `*.Tests.csproj` or `*Tests/` directories; do not conflate test and source projects
- Naming: PascalCase for classes and methods; follow existing file naming before introducing new patterns
- One class per file; namespace must match folder path relative to project root
- Cart domain: classes likely include Cart, CartItem, CartService — preserve public interfaces unless task explicitly requires breaking changes

## Dependency manifests
- `**/*.csproj` — all package references (NuGet); edit `<PackageReference>` elements only here
- `packages.lock.json` — do NOT edit; regenerate via `dotnet restore --use-lock-file` if needed after .csproj changes
- `global.json` — SDK version pin if present; do not change SDK version without explicit instruction

## Testing
- Run `dotnet test` from repo root to execute full suite; all tests must pass before committing changes
- Do not delete or skip existing tests; adding tests is permitted
