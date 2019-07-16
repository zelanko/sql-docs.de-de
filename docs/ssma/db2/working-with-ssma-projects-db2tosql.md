---
title: Arbeiten mit SSMA-Projekten (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 07abef8a-28e8-4a66-927c-c9a5b8c938ef
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d2c585764e5bb7fffa55624054aecc7a4c589bbe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086181"
---
# <a name="working-with-ssma-projects-db2tosql"></a>Arbeiten mit SSMA-Projekten (DB2ToSQL)
Zum Migrieren von DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], erstellen Sie zunächst ein SSMA-Projekt. Das Projekt ist eine Datei mit den folgenden Informationen an:  
  
-   Metadaten zu den DB2-Datenbanken, die Sie zum migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Metadaten zu der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erhalten, die die migrierten Objekte und Daten.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungsinformationen.  
  
-   Projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird er aus DB2 getrennt und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mit der Sie offline arbeiten. Informationen zum Wiederherstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen die standardmäßigen Projekteinstellungen  
SSMA enthält mehrere Einstellungen zum Konvertieren und Laden von Datenbankobjekten, Migrieren von Daten und Synchronisieren von SSMA mit DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Standardeinstellungen eignen sich für viele Benutzer. Bevor Sie ein neues SSMA-Projekt erstellen, sollten Sie jedoch die Einstellungen überprüfen. Wenn Sie möchten, können Sie die Standardeinstellungen ändern, die für alle neuen Projekte verwendet werden.  
  
**Standardprojekteinstellungen überprüfen**  
  
1.  Auf der **Tools** Menü klicken Sie auf **Projekt Standardeinstellungen**.  
  
2.  Wählen Sie den Projekttyp in **Migration Zielversion** Dropdownmenü für die Einstellungen sind erforderlich, angezeigt oder geändert werden soll, und klicken Sie dann auf **allgemeine** Registerkarte.  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Klicken Sie im rechten Bereich überprüfen Sie und ändern Sie die Einstellungen nach Bedarf. Weitere Informationen zu diesen Einstellungen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
5.  Wiederholen Sie die Schritte 1 bis 3 für die Migration, Synchronisierung, beim Laden von Systemobjekten, grafische Benutzeroberfläche und Type Mapping-Seiten.  
  
    -   Weitere Informationen zu den migrationseinstellungen finden Sie unter [Projekteinstellungen &#40;Migration&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md).  
  
    -   Weitere Informationen zu den Einstellungen der System-Objekt finden Sie unter [Projekteinstellungen&#40;Laden von Systemobjekten&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-loading-system-objects-db2tosql.md).  
  
    -   Weitere Informationen zu Einstellungen für die Synchronisierung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Projekteinstellungen&#40;Synchronisierung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
    -   Weitere Informationen zu den GUI-Einstellungen finden Sie unter [Projekteinstellungen &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md).  
  
    -   Weitere Informationen zu den Einstellungen der Zuordnung von Datentypen finden Sie unter [Projekteinstellungen &#40;Typzuordnung&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Migrieren von Daten aus DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], müssen Sie zunächst ein Projekt erstellen.  
  
**Zum Erstellen eines Projekts**  
  
1.  Klicken Sie im Menü **Datei** auf **Neues Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
3.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt, und klicken Sie dann auf **OK**.  
  
4.  In der **Migration zu** öffnen Sie die Dropdownliste, wählen Sie die Version des Ziels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL-Datenbank  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von standardmäßigen projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Setting Project Options Projektoptionen &#40;OracleToSQL&#41; ](../../ssma/oracle/setting-project-options-oracletosql.md) und Verwandte Abschnitte.  
  
Wenn Sie datentypzuordnungen zwischen Quell-und Zieldatenbanken anpassen, können Sie Zuordnungen auf das Projekt, Datenbank oder Objektebene definieren. Weitere Informationen finden Sie unter [Zuordnen von DB2- und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, behält SSMA den projekteinstellungen und optional die Datenbank-Metadaten zu der Projektdatei.  
  
**Um ein Projekt zu speichern.**  
  
-   Auf der **Datei** Menü klicken Sie auf **Projekt speichern**.  
  
    Wenn die Schemas im Projekt geändert haben oder nicht konvertiert wurden, fordert SSMA Sie zum Laden und Speichern von Metadaten. Laden und Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine vollständige Projektdatei an andere Personen ein, z. B. Mitarbeiter des technischen Supports senden. Wenn Sie aufgefordert werden, um Metadaten zu speichern, führen Sie folgende Schritte aus:  
  
    1.  Für jedes Schema, das dem Status **fehlenden Metadaten**, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
        Speichern von Metadaten kann mehrere Minuten dauern. Wenn Sie noch keine Metadaten speichern möchten, Sie keine Kontrollkästchen aktivieren.  
  
    2.  Klicken Sie auf die Schaltfläche **Speichern**.  
  
        SSMA analysiert die DB2-Schemas und speichern Sie die Metadaten zu der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird er getrennt von DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mit der Sie offline arbeiten. Um Metadaten zu aktualisieren, laden Sie die Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Zum Migrieren von Daten müssen Sie eine Verbindung mit DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Um ein Projekt zu öffnen.**  
  
1.  Verwenden Sie eine der folgenden Verfahren:  
  
    -   Auf der **Datei** Startmenü **zuletzt geöffnete Projekte**, und klicken Sie dann auf das Projekt, das Sie öffnen möchten.  
  
    -   Auf der **Datei** , wählen Sie im Menü **geöffneten Projekt**, suchen Sie die Projektdatei .o2ssproj, wählen Sie die Datei, und klicken Sie dann auf **öffnen**.  
  
2.  Verbindung mit DB2, auf die **Datei** Menü klicken Sie auf **Wiederherstellen der Verbindung mit DB2**.  
  
3.  Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf die **Datei** Menü klicken Sie auf **Wiederherstellen der Verbindung mit SQL Server**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit DB2-Datenbank](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
[Herstellen einer Verbindung mit DB2-Datenbank &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
[Herstellen einer Verbindung mit SQLServer &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
  
