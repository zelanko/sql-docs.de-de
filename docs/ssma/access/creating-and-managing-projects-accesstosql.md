---
description: Erstellen und Verwalten von Projekten (accesstosql)
title: Erstellen und Verwalten von Projekten (accesstosql) | Microsoft-Dokumentation
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ee6cf3bea905b169503851efe375fd614c4589e9
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988196"
---
# <a name="creating-and-managing-projects-accesstosql"></a>Erstellen und Verwalten von Projekten (accesstosql)
Wenn Sie Access-Datenbanken zu oder SQL Azure migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie zunächst ein SSMA-Projekt erstellen. Das Projekt ist eine Datei mit Metadaten zu den Access-Datenbanken, die Sie zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Metadaten zur Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die die migrierten Objekte und Daten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungsinformationen und Projekteinstellungen empfängt.  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen der Standard Projekteinstellungen  
SSMA enthält mehrere Optionen zum umrechnen und Synchronisieren von Datenbankobjekten und zum Datenkonvertierung. Die Standardeinstellung für diese Optionen eignet sich für viele Benutzer. Bevor Sie jedoch ein neues SSMA-Projekt erstellen, sollten Sie die Optionen überprüfen und ggf. die Standardeinstellungen ändern, die für alle neuen Projekte verwendet werden.  
  
**So überprüfen Sie die Standard Projekteinstellungen**  
  
1.  Wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus.  
  
2.  Wählen Sie in der Dropdown Liste **Migrations Ziel Version** den Projekttyp aus, für den Einstellungen angezeigt/geändert werden sollen, und klicken Sie auf die Registerkarte **Allgemein**  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Überprüfen Sie im rechten Bereich die Optionen. Weitere Informationen zu diesen Optionen finden Sie unter [Projekteinstellungen (Konvertierung)](./project-settings-conversion-accesstosql.md).  
  
5.  Ändern Sie die Optionen nach Bedarf.  
  
6.  Wiederholen Sie die vorherigen Schritte für die Seiten " **Migration**", " **GUI**" und " **Typzuordnung** ".  
  
    -   Informationen zu den Migrations Optionen finden Sie unter [Projekteinstellungen (Migration)](./project-settings-migration-accesstosql.md).  
  
    -   Weitere Informationen zu den Optionen der Benutzeroberfläche finden Sie unter [Projekteinstellungen (GUI)](../sybase/project-settings-gui-sybasetosql.md).  
  
    -   Weitere Informationen zu den Einstellungen für die Datentyp Zuordnung finden Sie unter [Projekteinstellungen (Typzuordnung)](./project-settings-type-mapping-accesstosql.md).  
  
    -   Weitere Informationen zu SQL Azure Einstellungen finden Sie unter [Project Settings (SQL Azure)](./project-settings-azure-sql-db-accesstosql.md).  
  
**Hinweis** SQL Azure Einstellungen stehen nur zur Verfügung, wenn beim Erstellen eines Projekts Migration zum SQL Azure ausgewählt wird.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
SSMA startet, ohne ein Standard Projekt zu laden. Wenn Sie Daten aus Access-Datenbanken zu oder SQL Azure migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie ein Projekt erstellen.  
  
**So erstellen Sie ein neues Projekt**  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  
  
3.  Geben Sie im Feld **Speicherort** einen Ordner für das Projekt ein, oder wählen Sie ihn aus.  
  
4.  Wählen Sie in der Dropdown-Migration eine der SQL Server 2005/SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016/Azure SQL-Datenbank aus, und klicken Sie dann auf **OK**.  
  
SSMA erstellt die Projektdatei. Sie können jetzt den nächsten Schritt zum [Hinzufügen einer oder mehrerer Access-Datenbanken](adding-and-removing-access-database-files-accesstosql.md)ausführen.  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von Standard Projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie auch die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Festlegen von Konvertierungs-und Migrations Optionen](setting-conversion-and-migration-options-accesstosql.md).  
  
Wenn Sie Datentyp Zuordnungen zwischen Quell-und Ziel Datenbanken anpassen, können Sie Zuordnungen auf Projekt-, Datenbank-oder Objektebene definieren. Weitere Informationen zur Typzuordnung finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, speichert SSMA die Projekteinstellungen und optional die Daten Bank Metadaten in der Projektdatei.  
  
**So speichern Sie ein Projekt**  
  
-   Wählen Sie im Menü **Datei** die Option **Projekt speichern**aus.  
  
    Wenn sich Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, werden Sie von SSMA aufgefordert, Metadaten im Projekt zu speichern. Durch das Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine komplette Projektdatei an andere Personen senden, einschließlich der technischen Supportmitarbeiter. Wenn Sie zum Speichern von Metadaten aufgefordert werden, gehen Sie wie folgt vor:  
  
    1.  Aktivieren Sie für jede Datenbank, die den Status **fehlender Metadaten**anzeigt, das Kontrollkästchen neben dem Datenbanknamen.  
  
        Das Speichern von Metadaten kann einige Minuten dauern. Wenn Sie an diesem Punkt keine Metadaten speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
    2.  Klicken Sie auf **Speichern**.  
  
        SSMA analysiert die Zugriffs Schemas und speichert die Metadaten in der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird es getrennt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Auf diese Weise können Sie offline arbeiten. Zum Aktualisieren von Metadaten laden Sie Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Zum Migrieren von Daten müssen Sie erneut eine Verbindung mit herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
**So öffnen Sie ein Projekt**  
  
1.  Verwenden Sie eines der folgenden Verfahren:  
  
    -   Zeigen Sie im Menü **Datei** auf **zuletzt verwendete Projekte**, und wählen Sie dann das Projekt aus, das Sie öffnen möchten.  
  
    -   Wählen Sie im Menü **Datei** die Option **Projekt öffnen**aus, suchen Sie die Projektdatei. a2ssproj, wählen Sie die Datei aus, und klicken Sie dann auf **Öffnen**.  
  
2.  Um erneut eine Verbindung mit herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wählen Sie im Menü **Datei** die Option **Verbindung wiederherstellen mit SQL Server**.  
  
3.  Um die Verbindung mit SQL Azure wiederherzustellen, wählen Sie im Menü **Datei** die Option **Verbindung wiederherstellen mit SQL Azure.**  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, [eine oder mehrere Zugriffs Datenbanken hinzuzufügen](adding-and-removing-access-database-files-accesstosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md)  
