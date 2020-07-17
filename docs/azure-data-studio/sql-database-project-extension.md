---
title: SQL Database Projects-Erweiterung
description: Installieren und Verwenden Sie die Erweiterung „SQL Database Projects“ (Vorschau) für Azure Data Studio.
ms.custom: seodec18
ms.date: 06/25/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 609af04cec2f6eaaaf1890e19c6d85fbd4bd5b8a
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2020
ms.locfileid: "85519155"
---
# <a name="sql-database-projects-extension-preview"></a>SQL Database Projects-Erweiterung (Vorschau)

Die Erweiterung „SQL Database Projects“ (Vorschau) ist eine Erweiterung für die Entwicklung von SQL-Datenbanken in einer projektbasierten Entwicklungsumgebung. Sie befindet sich derzeit in der Vorschauphase und ist als [Azure Data Studio-Insider-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main) verfügbar.


## <a name="install-the-sql-database-projects-extension"></a>Installieren der Erweiterung „SQL Database Projects“

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Suchen Sie die Erweiterung *SQL Database Projects*, indem Sie deren Namen ganz oder teilweise in das Suchfeld für Erweiterungen eingeben. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Installieren der Erweiterung](media/extensions/sql-database-projects-extension/install-database-projects.png)

3. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
4. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).
5. Klicken Sie in der Aktivitätsleiste auf das Dateisymbol, oder klicken Sie im Menü **View** (Ansicht) auf **Explorer**. Ein neues Viewlet für **Projekte** ist nun verfügbar.

   > [!NOTE]
   > Für die Nutzung des vollen Funktionsumfangs wird empfohlen, die [Erweiterung „Schemavergleich“](schema-compare-extension.md) zusammen mit der Erweiterung „SQL Database Projects“ zu installieren.

## <a name="getting-started-with-database-projects"></a>Erste Schritte mit Database Projects

* Erstellen Sie ein neues Datenbankprojekt, indem Sie unter „Explorer“ zum Viewlet **Projects** (Projekte) navigieren oder in der Befehlspalette nach **New Database Project** (Neues Datenbankprojekt) suchen.
* Vorhandene Datenbankprojekte können in der Befehlspalette über **Open Database Project** (Datenbankprojekt öffnen) geöffnet werden.
* Starten Sie mit einer vorhandenen Datenbank, indem Sie in der Befehlspalette auf **Import New Database Project** (Neues Datenbankprojekt importieren) klicken.

   ![Neues Viewlet](media/extensions/sql-database-projects-extension/projects-viewlet.png)


### <a name="create-an-empty-database-project"></a>Erstellen eines leeren Datenbankprojekts

 Klicken Sie unter **Explorer** im Viewlet **Projects** (Projekte) auf die Schaltfläche **New Project** (Neues Projekt), und geben Sie in der angezeigten Texteingabe einen Projektnamen an.  Wählen Sie im angezeigten Dialogfeld „Select a Folder“ (Ordner auswählen) ein Verzeichnis für den Ordner, die .sqlproj-Datei und andere Inhalte des Projekts aus.
Das leere Projekt wird geöffnet und im Viewlet **Projects** (Projekte) für die Bearbeitung angezeigt.

### <a name="open-an-existing-project"></a>Öffnen eines vorhandenen Projekts

Klicken Sie im Viewlet **Projects** (Projekte) auf die Schaltfläche **Open Project** (Projekt öffnen), und öffnen Sie über die angezeigte Dateiauswahl eine vorhandene *.sqlproj*-Datei. Vorhandene Projekte können aus Azure Data Studio oder [Visual Studio SQL Server Data Tools](../ssdt/sql-server-data-tools.md) stammen.

Das vorhandene Projekt wird geöffnet und seine Inhalte werden im Viewlet **Projects** (Projekte) für die Bearbeitung angezeigt.

### <a name="create-a-database-project-from-an-existing-database"></a>Erstellen eines Datenbankprojekts aus einer vorhandenen Datenbank

Klicken Sie im Viewlet **Projects** (Projekte) auf die Schaltfläche **Import Project from Database** (Projekt aus Datenbank importieren), und stellen Sie eine Verbindung mit einer SQL Server-Instanz her.  Wählen Sie, sobald die Verbindung hergestellt wurde, eine Datenbank aus der Liste der verfügbaren Datenbanken aus, und legen Sie den Namen des Projekts fest.

Wählen Sie abschließend eine Zielstruktur für die Extraktion aus.  Das neue Projekt wird geöffnet und enthält SQL-Skripts für die Inhalte der ausgewählten Datenbank.

## <a name="build-and-publish"></a>Erstellen und Veröffentlichen

In der Erweiterung „SQL Database Projects“ für Azure Data Studio stellen Sie das Datenbankprojekt bereit, indem Sie es als [Datenschichtanwendungs-Datei](../relational-databases/data-tier-applications/data-tier-applications.md) (DACPAC) erstellen und auf einer unterstützten Plattform veröffentlichen. Weitere Informationen zu diesem Prozess finden Sie unter [Erstellen und Veröffentlichen eines Projekts](sql-database-project-extension-build.md).

## <a name="schema-compare"></a>Schemavergleich
Die Erweiterung „SQL Database Projects“ interagiert mit der [Erweiterung „Schemavergleich“](schema-compare-extension.md), sofern installiert, um die Inhalte eines Projekts mit einem DAC-Paket oder einer vorhandenen Datenbank zu vergleichen.  Der resultierende Schemavergleich kann verwendet werden, um die Unterschiede zwischen Quelle und Ziel anzuzeigen und zu übernehmen.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen und Veröffentlichen Sie ein Projekt mit der Erweiterung „SQL Database Projects“ für Azure Data Studio.](sql-database-project-extension-build.md)
- [Datenschichtanwendungen](../relational-databases/data-tier-applications/data-tier-applications.md)