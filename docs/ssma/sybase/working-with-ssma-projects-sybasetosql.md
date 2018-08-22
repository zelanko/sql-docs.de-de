---
title: Arbeiten mit SSMA-Projekten (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d8f95fad58c2cc0b4011a7a3b1dd34f1985e3777
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392081"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Arbeiten mit SSMA-Projekten (SybaseToSQL)
Zum Migrieren von Sybase Adaptive Server Enterprise (ASE) Datenbanken auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Sie zuerst ein SSMA Projekt erstellen. Das Projekt ist eine Datei mit Metadaten über die ASE-Datenbanken, die Sie zum migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, Metadaten zu der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die die migrierten Objekte und Daten, erhält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Verbindungsinformationen und projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird er getrennt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Dadurch können Sie offline arbeiten. Sie können die Verbindung mit wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [eine Verbindung mit Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen die standardmäßigen Projekteinstellungen  
SSMA enthält mehrere Optionen zum Konvertieren und Migrieren von Daten und Synchronisieren von SSMA mit ASE-Datenbankobjekten werden geladen, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Die Standardeinstellungen für diese Optionen sind für viele Benutzer geeignet. Jedoch bevor Sie ein neues SSMA-Projekt erstellen, sollten Sie überprüfen Sie die Optionen und, wenn Sie möchten, ändern Sie die Standardeinstellungen, die für alle neuen Projekte verwendet werden.  
  
**Standardprojekteinstellungen überprüfen**  
  
1.  Auf der **Tools** , wählen Sie im Menü **Projekt Standardeinstellungen**.  
  
2.  Wählen Sie den Projekttyp in **Migration Zielversion** Dropdownmenü für die Einstellungen sind erforderlich, angezeigt oder geändert werden soll, und klicken Sie dann auf **allgemeine** Registerkarte.  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Überprüfen Sie im rechten Bereich die Optionen, die Optionen nach Bedarf ändern. Weitere Informationen zu diesen Optionen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Wiederholen Sie die Schritte 1 bis 3 für die Migration, SQL Azure, Laden von Objekten, grafische Benutzeroberfläche und Type Mapping-Seiten.  
  
    -   Informationen zu Migrationsoptionen finden Sie unter [Projekteinstellungen &#40;Migration&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Weitere Informationen zu Optionen zum Laden von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Projekteinstellungen &#40;Synchronisierung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Weitere Informationen zu den GUI-Optionen finden Sie unter [Projekteinstellungen &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Weitere Informationen zur Zuordnung von Datentypen mit Einstellungen, klicken Sie auf [Projekteinstellungen &#40;Typzuordnung&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Weitere Informationen zu SQL Azure-Optionen finden Sie unter [Projekteinstellungen &#40;Azure SQL-Datenbank &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Die SQL Azure-Einstellungen werden angezeigt, nur, wenn Sie auswählen, **Migration zu SQL Azure** beim Erstellen eines Projekts.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Migrieren von Daten aus dem ASE-Datenbanken, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, müssen Sie zunächst ein Projekt erstellen.  
  
**Zum Erstellen eines Projekts**  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
3.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt.  
  
4.  In der **Migration zu** öffnen Sie die Dropdownliste, wählen Sie die Version des Ziels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL-Datenbank  
  
Und klicken Sie dann auf **OK**.  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von standardmäßigen projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Setting Project Options Projektoptionen &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
Wenn Sie datentypzuordnungen zwischen Quell-und Zieldatenbanken anpassen, können Sie Zuordnungen auf das Projekt, Datenbank oder Objektebene definieren. Weitere Informationen zur Zuordnung finden Sie unter [Mapping Sybase ASE als auch SQL Server-Datentypen &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, behält SSMA den projekteinstellungen und optional die Datenbank-Metadaten zu der Projektdatei.  
  
**Um ein Projekt zu speichern.**  
  
-   Auf der **Datei** , wählen Sie im Menü **Projekt speichern**.  
  
    Wenn Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, werden Sie von SSMA aufgefordert, die Metadaten in das Projekt zu speichern. Speichern von Metadaten, können Sie offline arbeiten und eine vollständige Projektdatei an andere Personen, einschließlich Mitarbeiter des technischen Supports zu senden. Wenn Sie aufgefordert werden, um Metadaten zu speichern, führen Sie folgende Schritte aus:  
  
    1.  Für jede Datenbank, die dem Status **fehlenden Metadaten**, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
        Speichern von Metadaten kann mehrere Minuten dauern. Wenn Sie nicht, um Metadaten an diesem Punkt zu speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
    2.  Klicken Sie auf die **speichern** Schaltfläche.  
  
        SSMA analysiert die Sybase ASE Schemas und speichern Sie die Metadaten zu der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird er getrennt von der ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Dadurch können Sie offline arbeiten. Um Metadaten zu aktualisieren, laden Sie die Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Zum Migrieren von Daten, die Sie die ASE wiederherstellen müssen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.  
  
**Um ein Projekt zu öffnen.**  
  
1.  Verwenden Sie eine der folgenden Verfahren:  
  
    -   Auf der **Datei** Startmenü **zuletzt geöffnete Projekte**, und wählen Sie dann auf das Projekt, das Sie öffnen möchten.  
  
    -   Auf der **Datei** , wählen Sie im Menü **geöffneten Projekt**, suchen Sie die Projektdatei .s2ssproj, wählen Sie die Datei, und klicken Sie dann auf **öffnen**.  
  
2.  Verbindung zu App Service-Umgebung auf die **Datei** , wählen Sie im Menü **Wiederherstellen der Verbindung in Sybase**.  
  
3.  Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, auf die **Datei** , wählen Sie im Menü **Wiederherstellen der Verbindung mit SQL Server** / **Wiederherstellen der Verbindung zu SQL Azure**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit Sybase ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Herstellen einer Verbindung mit Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Herstellen einer Verbindung mit SQLServer &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
