---
title: Migrations-Assistent (AccessToSQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: acb05f10772ebdf77355b78e1f4ce998cc6c8056
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657014"
---
# <a name="migration-wizard-accesstosql"></a>Migrations-Assistent (AccessToSQL)
Der Migrations-Assistent führt Sie durch die Migration von einer oder mehreren Datenbanken vom Zugang zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Mithilfe des Assistenten zum Sie erstellen ein Projekt, Datenbanken zum Projekt hinzufügen, wählen Sie Objekte migrieren und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie werden auch konvertieren, laden und Migrieren von Access-Schemas und Daten. Sie können optional, zugreifen auf Tabellen zu verknüpfen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen.  
  
Die meisten Migrations-Assistent Seiten enthalten die gleichen Optionen wie vorhandene SSMA-Dialogfelder. Aus diesem Grund werden die Seiten des Assistenten werden hier beschrieben, und klicken Sie dann Links werden bereitgestellt, sodass Sie weitere Informationen zu einzelnen Optionen können. Wenn eine Seite eindeutige Optionen enthält, werden sie hier dokumentiert.  
  
## <a name="starting-the-migration-wizard"></a>Der Migrations-Assistent wird gestartet.  
Standardmäßig wird der Migrations-Assistent angezeigt, beim Starten von SSMA. Sie können den Assistenten auch starten, auf die **Datei** im Menü **Migrations-Assistent**.  
  
## <a name="welcome-page"></a>Willkommensseite  
Die Seite "Willkommen" führt der Migrations-Assistent und bietet die folgende Option zum Starten des Assistenten.  
  
**Starten Sie die Assistenten bei Systemstart.**  
Standardmäßig wird SSMA der Migrations-Assistent gestartet, beim Starten von SSMA. Um den automatischen Start des Assistenten zu verhindern, können deaktivieren Sie dieses Kontrollkästchen.  
  
## <a name="create-new-project-page"></a>Erstellen Sie die neue Projektseite  
Die Seite "Neues Projekt erstellen" ist, in dem Sie die Project-Datei Name, Speicherort und Migration-Projekt (die Version des Ziels für die Migration verwendete SQL Server) eingeben. Weitere Informationen finden Sie unter [neues Projekt (SSMA)](https://msdn.microsoft.com/ca294f6d-eeb5-42ca-9306-156281a3f0f3)  
  
## <a name="add-access-databases-page"></a>Fügen Sie die Seite "Access-Datenbanken"  
Die Access-Datenbanken hinzufügen-Seite ist, in dem Sie das Projekt mindestens eine Access-Datenbanken hinzufügen. Sie können einzelne Datenbanken hinzufügen, indem Sie auf **Datenbanken hinzufügen**, und wählen Sie dann auf die Datenbanken aus dem **öffnen** Fenster. Oder Datenbanken finden Sie unter Verwendung der **Datenbanken suchen** Schaltfläche. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md)  
  
-   [Find suchen Sie Databases Wizard (Option Standorte)](https://msdn.microsoft.com/00b2d32a-998b-47a7-b25c-589b5bd6777a)  
  
-   [Find suchen Sie Databases Wizard (Option-Dateien)](https://msdn.microsoft.com/2f574a34-4bab-40a4-89a8-ad4907ffc3fd)  
  
-   [Find Databases Wizard (Verify Selection) (Suchen des Assistenten für Datenbanken (Auswahl überprüfen))](https://msdn.microsoft.com/62e20e03-50cc-4ac8-8072-524d194d2ec3)  
  
## <a name="select-objects-to-migrate-page"></a>Wählen Sie Objekte auf der Seite-Migration  
Für die auswählen-Objekte zur Migration-Seite Wählen Sie die Objekte zu konvertieren. Sie können alle Objekte, Gruppen von Objekten oder einzelne Objekte auswählen.  
  
**Objekte auswählen**  
  
1.  Erweitern Sie **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Führen Sie eine oder mehrere der folgenden:  
  
    -   Um alle Datenbanken zu konvertieren, wählen Sie das Kontrollkästchen neben **Datenbanken**.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie die einzelne Datenbanken, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Zum konvertieren, oder lassen Sie Abfragen aus, erweitern Sie die Datenbank, und aktivieren bzw. Deaktivieren der **Abfragen** Kontrollkästchen.  
  
    -   Klicken Sie zum konvertieren, oder lassen Sie einzelne Tabellen, erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
Wenn Sie viele Objekte verfügen, sollten Sie verwenden die **erweiterte Objektauswahl** Optionen im rechten Bereich zum Filtern von Access-Datenbankobjekten. Wenn Sie auswählen, z. B. **Tabellen** im linken Bereich können Sie dann die Liste der Tabellen durch Eingeben von Zeichenfolgen in Filtern die **Filter** Feld. Sie können dann aktivieren oder deaktivieren die gefilterte Tabellen für die Migration, mithilfe der Schaltflächen am oberen Rand des Bereichs.  
  
Weitere Informationen zur Filterung finden Sie unter dem Abschnitt "Optionen" [Objektauswahl Advanced (häufig SSMA)](https://msdn.microsoft.com/f53b0c79-5473-410a-a0dc-d8f544f7a63c).  
  
## <a name="connect-to-sql-server-page"></a>Verbinden Sie mit SQL Server-Seite  
Klicken Sie auf das Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Seite, Sie geben Sie die Verbindungseigenschaften, und verbinden Sie dann mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server](connect-to-sql-server-accesstosql.md).
  
> [!IMPORTANT]  
> Sobald die Verbindung erfolgreich ist, treten **Verknüpfungstabellen** Seite, in dem Sie haben die Möglichkeit der Verknüpfung von Tabellen. Klicken Sie auf **Weiter** und die Migration startet.  
  
## <a name="connect-to-sql-azure-page"></a>Verbinden mit SQL Azure-Seite  
Auf der Seite Connect to SQL Azure Geben Sie die Verbindungseigenschaften, und Verbinden mit SQL Azure. Um eine neue Azure-Datenbank zu erstellen, Sie können dazu mithilfe von **Azure-Datenbank erstellen** Option, die auf das Klicken auf **Durchsuchen** Schaltfläche. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Azure](connect-to-azure-sql-db-accesstosql.md)  
  
> [!IMPORTANT]  
> Sobald die Verbindung erfolgreich ist, treten **Verknüpfungstabellen** Seite, in dem Sie haben die Möglichkeit der Verknüpfung von Tabellen. Klicken Sie auf **Weiter** Schaltfläche auf der Seite Links, um die Migration zu starten.  
  
## <a name="link-tables-page"></a>Link-Seite "Tabellen"  
Die Tabellen verknüpfen-Seite können Sie die verknüpfen Sie der ursprünglichen Access-Tabellen mit den migrierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen. Verknüpfen von Tabellen die Access-Datenbank ändert, sodass Ihre Abfragen, Formulare, Berichte und Data Access-Seiten verwenden Sie die Daten in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank anstelle der Daten in der Access-Datenbank.  
  
**Verknüpfungstabellen**  
Wählen Sie die **Verbindungstabellen** Kontrollkästchen, um das Verknüpfen von Access-Tabellen mit den migrierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Tabellen. Um die Migration zu starten, klicken Sie auf **Weiter** Schaltfläche.  
  
## <a name="migration-status-page"></a>Status-Seite-Migration  
Der Migrationsstatus-Seite wird der Fortschritt der Konvertierung von Schemas den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Schemas, die beim Laden der konvertierten Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, und klicken Sie dann die Daten migriert.  
  
Weitere Informationen zu dieser Seite finden Sie unter [konvertieren, laden und migrieren](https://msdn.microsoft.com/4ec83e96-88a5-4b7b-8d5a-f3429d9a936b)  
  
## <a name="see-also"></a>Siehe auch  
[Erste Schritte mit SQL Server Migration Assistant für Access &#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Benutzer-Schnittstelle Reference(Access)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
