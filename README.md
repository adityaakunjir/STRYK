# STRYK

STRYK is a mobile-priority football squad and local community website for recurring turf players. The MVP starts on the web first so squads can discover, join the Pune pilot, and preview the core coordination loop before a native app exists.

## Repo Layout

- `web/` - Mobile-first React + Vite website.
- `backend/Stryk.Api/` - ASP.NET Core .NET 8 Web API with EF Core, Azure SQL-ready models, JWT auth, and SignalR.
- `docs/` - architecture, roadmap, and SQL schema notes.

## Run Locally

Website:

```powershell
cd web
npm install
npm run dev
```

Backend:

```powershell
dotnet tool restore
dotnet restore
dotnet build
dotnet run --project backend/Stryk.Api/Stryk.Api.csproj
```

The API defaults to SQL Server LocalDB for development. Replace `ConnectionStrings:DefaultConnection` with Azure SQL in production and replace the JWT signing key before any real deployment.

Database:

```powershell
dotnet tool restore
dotnet tool run dotnet-ef database update --project backend/Stryk.Api/Stryk.Api.csproj --startup-project backend/Stryk.Api/Stryk.Api.csproj
```

The first migration is checked in under `backend/Stryk.Api/Migrations`, and an idempotent Azure SQL script is available at `docs/azure-sql-initial-schema.sql`.
