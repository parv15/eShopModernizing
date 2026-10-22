# Catalog back office: a legacy ASP.NET MVC app on .NET Framework

This is the product catalog back office that shop staff use to list, add, edit and delete catalog items. It is an ASP.NET MVC 5 app on .NET Framework 4.7.2, with Entity Framework 6, Autofac, Web API 2, log4net and Application Insights, and it runs on IIS with SQL Server.

It is the starting point for a step-by-step walkthrough of migrating a .NET Framework app to .NET 10 with [Opsera Forge](https://opsera.ai/forge/modernization/framework-upgrades).

This repo is a fork of Microsoft's [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) sample (MIT licence). On the `before` branch only the legacy MVC app and its utilities project are kept. Microsoft's own ported and modernized versions were removed so the migration starts from the legacy code alone.

## What is in the repo

| Path | What it holds |
| --- | --- |
| `eShopLegacyMVCSolution/src/eShopLegacyMVC/` | The web app: controllers, views, models, `Global.asax`, `Web.config` |
| `eShopLegacyMVCSolution/eShopLegacy.Utilities/` | A small shared library used by the app |
| `eShopLegacyMVCSolution/eShopLegacyMVC.sln` | Visual Studio solution |
| `checks/staff_tasks.md` | The everyday staff tasks used to check the migrated app |

## Run the original app

The original app needs Windows.

1. Install Visual Studio 2022 with the **ASP.NET and web development** workload and the .NET Framework 4.7.2 targeting pack. SQL Server LocalDB comes with that workload.
2. Open `eShopLegacyMVCSolution/eShopLegacyMVC.sln` and let Visual Studio restore the NuGet packages.
3. Press F5. The app opens in the browser on IIS Express and creates its database with 12 sample items on first run.

To run without a database, set `UseMockData` to `true` in `eShopLegacyMVCSolution/src/eShopLegacyMVC/Web.config`. The app then serves the same sample items from memory.

## Check the migrated app

Work through `checks/staff_tasks.md` on the original app first and note what you see. Then run the same tasks on the migrated app. Every task should give the same result, apart from any change the team agreed during the migration.

## Branches

| Branch | What it holds |
| --- | --- |
| `before` | The .NET Framework app exactly as it was before the migration |
| `forge-migrated` | The .NET 10 version produced with Forge, running in a Linux container |
| `main` | Microsoft's original sample, untouched |

## Licence

MIT, from the original eShopModernizing sample. See `LICENSE`.
