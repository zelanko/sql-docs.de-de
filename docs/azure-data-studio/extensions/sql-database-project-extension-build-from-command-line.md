---
title: Erstellen eines Projekts über die Befehlszeile
description: Erstellen eines SQL Server-Datenbankprojekts über die Befehlszeile
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 08/07/2020
ms.openlocfilehash: 8c3dc88f13b7cfade3b650dcf621132d6bc22f9a
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123373"
---
# <a name="build-a-database-project-from-command-line"></a>Erstellen eines Datenbankprojekts über die Befehlszeile

Die SQL Database Project-Erweiterung für Azure Data Studio stellt eine grafische Benutzeroberfläche zum [Erstellen eines Datenbankprojekts](sql-database-project-extension-build.md) bereit. Für Windows-, macOS- und Linux-Umgebungen steht aber auch eine Buildoption über die Befehlszeile zur Verfügung. In diesem Artikel werden die Voraussetzungen und die Syntax für die Erstellung eines SQL-Projekts in einer DACPAC-Datei über die Befehlszeile beschrieben.

## <a name="prerequisites"></a>Voraussetzungen

1. Installieren und konfigurieren Sie die [Erweiterung „SQL Server-Datenbankprojekte“ für Azure Data Studio](sql-database-project-extension.md).

2. Die folgenden .NET Code-DLL-Dateien und die Zieldatei `Microsoft.Data.Tools.Schema.SqlTasts.targets` sind erforderlich, um ein SQL-Datenbankprojekt über die Befehlszeile zu erstellen. Dies gilt für alle Plattformen, die von der Azure Data Studio-Erweiterung „SQL Database Projects“ unterstützt werden. Diese Dateien werden von der Erweiterung während des ersten Builds auf der Benutzeroberfläche von Azure Data Studio erstellt und im Ordner der Erweiterung unter `BuildDirectory` gespeichert.  Unter Linux werden diese Dateien beispielsweise in `~\.azuredatastudio\extensions\microsoft.sql-database-projects-x.x.x\BuildDirectory\` platziert.  Kopieren Sie diese zehn Dateien in einen neuen, zugänglichen Ordner, oder notieren Sie sich den Speicherort.  Dieser Speicherort wird im vorliegenden Dokument als `DotNet Core build folder` bezeichnet.

    - Microsoft.Data.Tools.Schema.Sql.dll
    - Microsoft.Data.Tools.Schema.Tasks.Sql.dll
    - Microsoft.Data.Tools.Utilities.dll
    - Microsoft.SqlServer.Dac.dll
    - Microsoft.SqlServer.Dac.Extensions.dll
    - Microsoft.SqlServer.TransactSql.ScriptDom.dll
    - Microsoft.SqlServer.Types.dll
    - Microsoft.Data.Tools.Schema.SqlTasks.targets
    - System.ComponentModel.Composition.dll
    - Microsoft.Data.SqlClient.dll

3. Wenn das Projekt in Azure Data Studio erstellt wurde, fahren Sie mit dem Schritt [Erstellen des Projekts über die Befehlszeile](#build-the-project-from-the-command-line) fort. Wenn das Projekt in SQL Server Data Tools (SSDT) erstellt wurde, öffnen Sie es in der Azure Data Studio-Erweiterung „SQL Database Project“.  Durch Öffnen des Projekts in Azure Data Studio wird die Datei `sqlproj` automatisch mit folgenden drei Bearbeitungen aktualisiert:

    1. Importbedingungen

    ```console
    <Import Condition="'$(NetCoreBuild)' == 'true'" Project="$(NETCoreTargetsPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/> 
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' != ''" Project="$(SQLDBExtensionsRefPath)\Microsoft.Data.Tools.Schema.SqlTasks.targets"/>
    <Import Condition="'$(NetCoreBuild)' != 'true' AND '$(SQLDBExtensionsRefPath)' == ''" Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets"/>
    ```

    2. Referenz zu Paketen

    ```console
    <ItemGroup>
        <PackageReference Condition="'$(NetCoreBuild)' == 'true'" Include="Microsoft.NETFramework.ReferenceAssemblies" Version="1.0.0" PrivateAssets="All"/>
    </ItemGroup>
    ```

    3. Zielbereinigung, erforderlich zur Unterstützung der dualen Bearbeitung in SQL Server Data Tools (SSDT) und Azure Data Studio

        ```console
        <Target Name="AfterClean">
            <Delete Files="$(BaseIntermediateOutputPath)\project.assets.json"/>
        </Target>
        ```

## <a name="build-the-project-from-the-command-line"></a>Erstellen des Projekts über die Befehlszeile

Verwenden Sie unter Angabe des vollständigen .NET-Ordners den folgenden Befehl:

```console
dotnet build "<sqlproj file path>" /p:NetCoreBuild=true /p:NETCoreTargetsPath="<DotNet Core build folder>"
```

Verwenden Sie z. B. `/usr/share/dotnet` unter Linux:

```console
dotnet build "/home/myuser/Documents/DatabaseProject1/DatabaseProject1.sqlproj" /p:NetCoreBuild=true /p:NETCoreTargetsPath="/home/myuser/.azuredatastudio-insiders/extensions/microsoft.sql-database-projects-0.1.2/BuildDirectory"  
```

## <a name="next-steps"></a>Nächste Schritte

- [Erweiterung „SQL Server-Datenbankprojekte“ für Azure Data Studio](sql-database-project-extension.md)
- [Veröffentlichen von SQL-Datenbankprojekten](sql-database-project-extension-build.md#publish-a-database-project)
