---
title: Migrations-Assistent (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migration Wizard dialog box
- Migration Wizard, adding Access databases
- Migration Wizard, Connect to SQL Azure
- Migration Wizard, Connect to SQL Server
- Migration Wizard, Link Tables
- Migration Wizard, Migration status
- Migration Wizard, New Project
- Migration Wizard, Selecting objects to migrate
ms.assetid: 5bab5914-b2ae-4795-8cf5-83e42d64bef2
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 658487186924fe5547edee70425524b2b4e3be6c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083593"
---
# <a name="migration-wizard-accesstosql"></a>Migrations-Assistent (accesstosql)
Der-Migrations-Assistent führt Sie durch die Migration von einer oder mehreren Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Access zu oder SQL Azure. Mit dem Assistenten erstellen Sie ein Projekt, fügen dem Projektdaten Banken hinzu, wählen zu migrierende Objekte aus und stellen eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit oder SQL Azure her. Außerdem werden Zugriffs Schemas und Daten konvertiert, geladen und migriert. Optional können Sie Zugriffs Tabellen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Tabellen verknüpfen.  
  
Die meisten Migrations-Assistenten Seiten enthalten dieselben Optionen wie vorhandene SSMA-Dialogfelder. Daher werden die Seiten des Assistenten hier beschrieben, und es werden Links bereitgestellt, damit Sie mehr über einzelne Optionen erfahren können. Wenn eine Seite eindeutige Optionen enthält, werden Sie hier dokumentiert.  
  
## <a name="starting-the-migration-wizard"></a>Starten des Migrations-Assistenten  
Der-Migrations-Assistent wird standardmäßig angezeigt, wenn Sie SSMA starten. Sie können den Assistenten auch im Menü **Datei** starten, indem Sie den **Migrations-Assistenten**auswählen.  
  
## <a name="welcome-page"></a>Startseite  
Die Willkommensseite führt den Migrations-Assistenten ein und bietet die folgende Option zum Starten des Assistenten.  
  
**Starten Sie diesen Assistenten beim Start.**  
Standardmäßig startet SSMA den Migrations-Assistenten, wenn Sie SSMA starten. Deaktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass der Assistent automatisch gestartet wird.  
  
## <a name="create-new-project-page"></a>Seite "Neues Projekt erstellen"  
Auf der Seite Neues Projekt erstellen können Sie den Projekt Dateinamen, den Speicherort und den Migrations Projekttyp (die Version des Ziel SQL Server für die Migration verwenden) eingeben. Weitere Informationen finden Sie unter [New Project (SSMA)](https://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Seite "Zugriffs Datenbanken hinzufügen"  
Auf der Seite Access-Datenbanken hinzufügen Fügen Sie dem Projekt eine oder mehrere Zugriffs Datenbanken hinzu. Sie können einzelne Datenbanken hinzufügen, indem Sie auf **Datenbanken hinzufügen**klicken und dann die Datenbanken im Fenster **Öffnen** auswählen. Sie können Datenbanken auch mithilfe der Schaltfläche **Datenbanken suchen** suchen. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md)  
  
-   [Assistent für die Datenbanksuche (Speicherorte auswählen)](https://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Assistent für die Datenbanksuche (Dateien auswählen)](https://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Assistent für die Datenbanksuche (Auswahl überprüfen)](https://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Seite "zu migrierende Objekte auswählen"  
Wählen Sie auf der Seite zu migrierende Objekte auswählen die Objekte aus, die konvertiert werden sollen. Sie können alle Objekte, Objektgruppen oder einzelne Objekte auswählen.  
  
**So wählen Sie Objekte aus**  
  
1.  Erweitern Sie **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Führen Sie eine oder mehrere der folgenden Aktionen aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben **Datenbanken**, um alle Datenbanken zu konvertieren.  
  
    -   Aktivieren oder deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um einzelne Datenbanken zu konvertieren oder auszulassen.  
  
    -   Wenn Sie Abfragen konvertieren oder weglassen möchten, erweitern Sie die Datenbank, und aktivieren oder deaktivieren Sie das Kontrollkästchen **Abfragen** .  
  
    -   Zum Konvertieren oder weglassen einzelner Tabellen erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
Wenn Sie über viele Objekte verfügen, können Sie die Optionen für **Erweiterte Objektauswahl** im rechten Bereich verwenden, um Access-Datenbankobjekte zu filtern. Wenn Sie z. b. **Tabellen** im linken Bereich auswählen, können Sie die Liste der Tabellen filtern, indem Sie Zeichen folgen in das **Filter** Feld eingeben. Anschließend können Sie die gefilterten Tabellen für die Migration mithilfe der Schaltflächen am oberen Rand des Bereichs auswählen oder löschen.  
  
Weitere Informationen zum Filtern finden Sie im Abschnitt "Optionen" unter [Erweiterte Objektauswahl (SSMA Common)](https://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Verbindung mit SQL Server Seite herstellen  
Legen Sie auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Seite verbinden mit die Verbindungs Eigenschaften fest, und stellen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dann eine Verbindung mit her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server](connect-to-sql-server-accesstosql.md).
  
> [!IMPORTANT]  
> Sobald die Verbindung erfolgreich hergestellt wurde, wird die Seite **Link Tabellen** angezeigt, auf der Sie die Möglichkeit haben, die Tabellen zu verknüpfen. Klicken Sie auf **weiter** , um die Migration zu starten.  
  
## <a name="connect-to-sql-azure-page"></a>Verbindung mit SQL Azure Seite herstellen  
Legen Sie auf der Seite mit SQL Azure verbinden die Verbindungs Eigenschaften fest, und stellen Sie dann eine Verbindung mit SQL Azure her. Zum Erstellen einer neuen Azure-Datenbank können Sie die Option **Create Azure Database** verwenden, die auf der Schaltfläche zum **Durchsuchen** klicken angezeigt wird. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Azure](connect-to-azure-sql-db-accesstosql.md)  
  
> [!IMPORTANT]  
> Sobald die Verbindung erfolgreich hergestellt wurde, wird die Seite **Link Tabellen** angezeigt, auf der Sie die Möglichkeit haben, die Tabellen zu verknüpfen. Klicken Sie auf der Seite Verknüpfungen auf **weiter** , um die Migration zu starten.  
  
## <a name="link-tables-page"></a>Link Tabellen (Seite)  
Auf der Seite Link Tabellen können Sie die ursprünglichen Zugriffs Tabellen mit den migrierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen oder SQL Azure Tabellen verknüpfen. Durch das Verknüpfen von Tabellen wird die Access-Datenbank geändert, sodass Ihre Abfragen, Formulare, Berichte und Datenzugriffsseiten die Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-oder-SQL Azure Datenbank anstelle der Daten in der Access-Datenbank verwenden.  
  
**Tabellen verknüpfen**  
Aktivieren Sie das Kontrollkästchen **Tabellen verknüpfen** , um Zugriffs Tabellen mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] migrierten Tabellen oder SQL Azure Tabellen zu verknüpfen. Um die Migration zu starten, klicken Sie auf die Schaltfläche **weiter** .  
  
## <a name="migration-status-page"></a>Seite "Migrations Status"  
Die Seite Migrations Status zeigt den Fortschritt der Konvertierung der Zugriffs Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in oder SQL Azure Schemas, das Laden der konvertierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas in oder SQL Azure und das anschließende Migrieren von Daten.  
  
Weitere Informationen zu dieser Seite finden Sie unter [konvertieren, laden und Migrieren](https://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b) .  
  
## <a name="see-also"></a>Weitere Informationen  
[Die ersten Schritte mit SQL Server Migration Assistant für Access &#40;accesstosql-&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Referenz zur Benutzeroberfläche (Zugriff)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
