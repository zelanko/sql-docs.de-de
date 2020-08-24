---
title: SQL Database Projects-Erweiterung
description: Installieren und Verwenden Sie die Erweiterung „SQL Database Projects“ (Vorschau) für Azure Data Studio.
ms.custom: seodec18
ms.date: 07/30/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 39ebf2d26e69e47edc700a489743d70762bef7b0
ms.sourcegitcommit: bf5acef60627f77883249bcec4c502b0205300a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88199987"
---
# <a name="sql-database-projects-extension-preview"></a>SQL Database Projects-Erweiterung (Vorschau)

Die Erweiterung „SQL Database Projects“ (Vorschau) ist eine Erweiterung für die Entwicklung von SQL-Datenbanken in einer projektbasierten Entwicklungsumgebung. Sie befindet sich derzeit in der Vorschauphase und ist als [Azure Data Studio-Insider-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main) verfügbar.


## <a name="features"></a>Features
1. Erstellen eines Projekts aus einer verbundenen Datenbank 
2. Erstellen eines neuen leeren Projekts
3. Öffnen eines Projekts, das in [Azure Data Studio](sql-database-project-extension-getting-started.md) oder [SQL Server Data Tools](../ssdt/sql-server-data-tools.md) erstellt wurde 
4. Bearbeiten eines Projekts durch Hinzufügen oder Entfernen von Tabellen, Sichten, gespeicherten Prozeduren oder benutzerdefinierten Skripts 
5. Organisieren von Dateien oder Skripts in Ordner 
6. Hinzufügen von Verweisen auf Systemdatenbanken oder Benutzer-DACPACs
7. Erstellen eines einzelnen Projekts 
8. Bereitstellen eines einzelnen Projekts
9. Laden von Verbindungsdetails (SQL-Windows-Authentifizierung) und SQLCMD-Variablen aus einem Bereitstellungsprofil 

## <a name="install-the-sql-database-projects-extension"></a>Installieren der Erweiterung „SQL Database Projects“

1. Öffnen Sie den Erweiterungs-Manager, um auf die verfügbaren Erweiterungen zuzugreifen.  Klicken Sie dazu entweder auf das Erweiterungssymbol, oder wählen Sie im Menü **Ansicht** die Option **Erweiterungen** aus.
2. Suchen Sie die Erweiterung *SQL Database Projects*, indem Sie deren Namen ganz oder teilweise in das Suchfeld für Erweiterungen eingeben. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Installieren der Erweiterung](media/extensions/sql-database-projects-extension/install-database-projects.png)

3. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
4. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).
5. Klicken Sie in der Aktivitätsleiste auf das Dateisymbol, oder klicken Sie im Menü **View** (Ansicht) auf **Explorer**. Ein neues Viewlet für **Projekte** ist nun verfügbar.


   > [!NOTE]
   > Das .NET Core SDK ist für die Buildfunktion des Projekts erforderlich, und Sie werden zur Installation des SDK aufgefordert, wenn es von der Erweiterung nicht gefunden wird.  Das .NET Core SDK (v3.1 oder höher) kann von [https://dotnet.microsoft.com/download/dotnet-core/3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) heruntergeladen und installiert werden.

   > [!NOTE]
   > Für die Nutzung des vollen Funktionsumfangs wird empfohlen, die [Erweiterung „Schemavergleich“](schema-compare-extension.md) zusammen mit der Erweiterung „SQL Database Projects“ zu installieren.

## <a name="known-limitations"></a>Bekannte Einschränkungen
1. Das Hinzufügen von Projektverweisen und das Laden vorhandener Projektverweise im Azure Data Studio-Viewlet werden derzeit nicht unterstützt. 
2. Das Laden von Dateien als Link wird im Azure Data Studio-Viewlet derzeit nicht unterstützt. Die Dateien werden aber in die oberste Ebene der Struktur geladen und beim Kompilieren erwartungsgemäß einbezogen. 
3. Das Hinzufügen und Laden von Skripts mit Befehlen vor und nach der Bereitstellung im Viewlet wird derzeit nicht unterstützt. Wenn Sie diese Dateien jedoch manuell zum Projekt hinzufügen, werden sie zur Kompilierzeit berücksichtigt. 
3. SQLCLR-Objekte im Projekt werden in der .NET Core-Version von DacFx nicht unterstützt. 
3. Tasks (Kompilieren/Veröffentlichen) sind nicht benutzerdefiniert.
3. Veröffentlichen von Zielen, die von DacFx definiert wurden.
3. Bei der Integration der Quellcodeverwaltung und beim Erstellen neuer Projekte wird nicht automatisch eine .gitignore-Datei erstellt. 
3. Die Unterstützung für die WSL-Umgebung ist eingeschränkt. 

## <a name="next-steps"></a>Nächste Schritte
- [Erste Schritte mit der Erweiterung „SQL Database Projects“](sql-database-project-extension-getting-started.md)
- [Erstellen und Veröffentlichen Sie ein Projekt mit der Erweiterung „SQL Database Projects“ für Azure Data Studio.](sql-database-project-extension-build.md)