---
title: Erstellen und Verwalten von Projekten (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- creating projects
- new projects
- opening projects
- projects
- projects, creating and managing
- saving metadata
- saving projects
ms.assetid: f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1cf23a076f7e4d7e873f48988364c51b1daa03b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138802"
---
# <a name="creating-and-managing-projects-accesstosql"></a>Erstellen und Verwalten von Projekten (AccessToSQL)
Migrieren von Access-Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, müssen Sie zunächst ein SSMA-Projekt erstellen. Das Projekt ist eine Datei mit Metadaten über die Access-Datenbanken, die Sie zum migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Metadaten zu der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die die migrierten Objekte und Daten, erhält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungsinformationen und projekteinstellungen.  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen die standardmäßigen Projekteinstellungen  
SSMA enthält mehrere Optionen zum Umrechnen und Synchronisieren von Datenbankobjekten und Daten zu konvertieren. Die Standardeinstellung für diese Optionen eignet sich für viele Benutzer. Jedoch bevor Sie ein neues SSMA-Projekt erstellen, sollten Sie überprüfen Sie die Optionen und, wenn Sie möchten, ändern die Standardeinstellungen, die für alle neuen Projekte verwendet werden.  
  
**Standardprojekteinstellungen überprüfen**  
  
1.  Auf der **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**.  
  
2.  Wählen Sie den Projekttyp in **Migration Zielversion** Dropdownliste aus, welche Einstellungen angezeigt oder geändert werden, und klicken Sie auf **allgemeine** Registerkarte.  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Überprüfen Sie im rechten Bereich die Optionen aus. Weitere Informationen zu diesen Optionen finden Sie unter [Project Settings (Conversion)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).  
  
5.  Ändern Sie Optionen nach Bedarf.  
  
6.  Wiederholen Sie die vorherigen Schritte für die **Migration**, **GUI**, und **Type Mapping** Seiten.  
  
    -   Informationen zu Migrationsoptionen finden Sie unter [Project Settings (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).  
  
    -   Weitere Informationen zu den Benutzeroberflächenoptionen finden Sie unter [Project Settings (GUI)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
    -   Weitere Informationen zu Einstellungen für die Zuordnung von Datentypen, finden Sie unter [Projekteinstellungen (Typzuordnung)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655).  
  
    -   Weitere Informationen zu SQL Azure-Einstellungen finden Sie unter [Project Settings (SQL Azure)](https://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e).  
  
**Beachten Sie** SQL Azure-Einstellungen werden zur Verfügung stehen, nur, wenn Sie die Migration zu SQL Azure beim Erstellen eines Projekts auswählen.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
SSMA wird gestartet, ohne ein Standardprojekt angelegt werden geladen. Migrieren von Daten aus Access-Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, müssen Sie ein Projekt erstellen.  
  
**Zum Erstellen eines neuen Projekts**  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
3.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt  
  
4.  Klicken Sie in der Dropdownliste der Migration, nach-unten, wählen Sie eine von SQL Server 2005 / SQL Server 2008 / SQL Server 2012 / SQL Server 2014 / SQL Server 2016 / Azure SQL-Datenbank, und klicken Sie dann auf **OK**.  
  
SSMA erstellt die Projektdatei. Sie können nun den nächsten Schritt ausführen [Hinzufügen von Access-Datenbanken für eine oder mehrere](adding-and-removing-access-database-files-accesstosql.md).  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von standardmäßigen projekteinstellungen verwenden, die für alle neuen SSMA-Projekte gelten, können Sie auch die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Einstellung Konvertierung und Migrationsoptionen](setting-conversion-and-migration-options-accesstosql.md).  
  
Wenn Sie datentypzuordnungen zwischen Quell-und Zieldatenbanken anpassen, können Sie Zuordnungen auf das Projekt, Datenbank oder Objektebene definieren. Weitere Informationen zur Zuordnung finden Sie unter [Zuordnungsquelle und das Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, speichert SSMA den projekteinstellungen und optional die Datenbank-Metadaten zu der Projektdatei.  
  
**Um ein Projekt zu speichern.**  
  
-   Auf der **Datei** , wählen Sie im Menü **Projekt speichern**.  
  
    Wenn Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, werden Sie von SSMA aufgefordert, die Metadaten in das Projekt zu speichern. Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine vollständige Projektdatei an andere Personen, einschließlich Mitarbeiter des technischen Supports senden. Wenn Sie aufgefordert werden, um Metadaten zu speichern, führen Sie folgende Schritte aus:  
  
    1.  Für jede Datenbank, die dem Status **fehlenden Metadaten**, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
        Speichern von Metadaten kann mehrere Minuten dauern. Wenn Sie nicht, um Metadaten an diesem Punkt zu speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
    2.  Klicken Sie auf **Speichern**.  
  
        SSMA analysiert die Access-Schemas und speichern Sie die Metadaten zu der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird er getrennt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Dadurch können Sie offline arbeiten. Beim Aktualisieren der Metadaten-Load-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Zum Migrieren von Daten, die Sie zum Wiederherstellen müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
**Um ein Projekt zu öffnen.**  
  
1.  Verwenden Sie eine der folgenden Verfahren:  
  
    -   Auf der **Datei** Startmenü **zuletzt geöffnete Projekte**, und wählen Sie dann auf das Projekt, das Sie öffnen möchten.  
  
    -   Auf der **Datei** , wählen Sie im Menü **geöffneten Projekt**, suchen Sie die Projektdatei .a2ssproj, wählen Sie die Datei, und klicken Sie dann auf **öffnen**.  
  
2.  Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf die **Datei** , wählen Sie im Menü **Wiederherstellen der Verbindung mit SQL Server**.  
  
3.  Verbindung zu SQL Azure, auf die **Datei** , wählen Sie im Menü **Erneutes Verbinden mit SQL Azure.**  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [mindestens eine Access-Datenbanken hinzufügen](adding-and-removing-access-database-files-accesstosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md)  
  
