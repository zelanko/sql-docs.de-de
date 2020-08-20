---
description: Arbeiten mit SSMA-Projekten (SybaseToSQL)
title: Arbeiten mit SSMA-Projekten (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: a1a73e1dbc1c494080427ae5dfd686dd3c18abc1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497632"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>Arbeiten mit SSMA-Projekten (SybaseToSQL)
Zum Migrieren von Sybase-Datenbanken vom Typ Adaptive Server Enterprise (ASE) zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure erstellen Sie zunächst ein SSMA-Projekt. Das Projekt ist eine Datei mit Metadaten zu den ASE-Datenbanken, die zu migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden sollen, oder SQL Azure, Metadaten zur Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die die migrierten Objekte und Daten empfängt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Verbindungsinformationen und Projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird es getrennt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Auf diese Weise können Sie offline arbeiten. Sie können erneut eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure herstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [Herstellen einer Verbindung mit der Azure SQL-Datenbank &#40;sybasedesql&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen der Standard Projekteinstellungen  
SSMA enthält mehrere Optionen zum umrechnen und Laden von Datenbankobjekten, zum Migrieren von Daten und zum Synchronisieren von SSMA mit ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Die Standardeinstellungen für diese Optionen sind für viele Benutzer geeignet. Bevor Sie jedoch ein neues SSMA-Projekt erstellen, sollten Sie die Optionen überprüfen und ggf. die Standardwerte ändern, die für alle neuen Projekte verwendet werden.  
  
**So überprüfen Sie die Standard Projekteinstellungen**  
  
1.  Wählen Sie **im Menü Extras** die Option **Standard Projekteinstellungen**aus.  
  
2.  Wählen Sie in der Dropdown Liste **Migrations Ziel Version** den Projekttyp aus, für den Einstellungen angezeigt oder geändert werden müssen, und klicken Sie dann auf die Registerkarte **Allgemein**  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Überprüfen Sie im rechten Bereich die Optionen, und ändern Sie die Optionen nach Bedarf. Weitere Informationen zu diesen Optionen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  Wiederholen Sie die Schritte 1-3 für die Seiten Migration, SQL Azure, Laden von Objekten, GUI und Typzuordnung.  
  
    -   Informationen zu den Migrations Optionen finden Sie unter [Project Settings &#40;Migration&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   Informationen zu den Optionen zum Laden von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Project Settings &#40;Synchronisierung&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   Weitere Informationen zu GUI-Optionen finden Sie unter [Project Settings &#40;GUI&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   Um weitere Informationen zu den Einstellungen für die Datentyp Zuordnung zu erhalten, klicken Sie auf [Projekteinstellungen &#40;Typzuordnung&#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   Weitere Informationen zu SQL Azure Optionen finden Sie unter [Projekteinstellungen &#40;Azure SQL-Datenbank &#41; &#40;sybasedesql&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > Die SQL Azure Einstellungen werden nur angezeigt, wenn Sie beim Erstellen eines Projekts **Migration zum SQL Azure** auswählen.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Wenn Sie Daten aus ASE-Datenbanken zu oder SQL Azure migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie zunächst ein Projekt erstellen.  
  
**So erstellen Sie ein Projekt**  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  
  
3.  Geben Sie im Feld **Speicherort** einen Ordner für das Projekt ein, oder wählen Sie einen Ordner aus.  
  
4.  Wählen Sie in der Dropdown Liste **Migration zu** die Version des Ziels aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet wird. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL-Datenbank  
  
Und klicken Sie dann auf **OK**.  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von Standard Projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Festlegen von Projektoptionen &#40;sybaseto SQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
Wenn Sie Datentyp Zuordnungen zwischen Quell-und Ziel Datenbanken anpassen, können Sie Zuordnungen auf Projekt-, Datenbank-oder Objektebene definieren. Weitere Informationen zur Typzuordnung finden Sie unter [Mapping Sybase ASE und SQL Server Datentypen &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, behält SSMA die Projekteinstellungen und optional die Daten Bank Metadaten in der Projektdatei.  
  
**So speichern Sie ein Projekt**  
  
-   Wählen Sie im Menü **Datei** die Option **Projekt speichern**aus.  
  
    Wenn sich Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, werden Sie von SSMA aufgefordert, Metadaten im Projekt zu speichern. Wenn Sie Metadaten speichern, können Sie offline arbeiten und eine komplette Projektdatei an andere Personen, einschließlich technischer Supportmitarbeiter, senden. Wenn Sie zum Speichern von Metadaten aufgefordert werden, gehen Sie wie folgt vor:  
  
    1.  Aktivieren Sie für jede Datenbank, die den Status **fehlender Metadaten**anzeigt, das Kontrollkästchen neben dem Datenbanknamen.  
  
        Das Speichern von Metadaten kann einige Minuten dauern. Wenn Sie an diesem Punkt keine Metadaten speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
    2.  Klicken Sie auf die Schaltfläche **Save** .  
  
        SSMA analysiert die Sybase-ASE-Schemas und speichert die Metadaten in der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird es von ASE und von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure getrennt. Auf diese Weise können Sie offline arbeiten. Laden Sie Datenbankobjekte in oder SQL Azure, um Metadaten zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Zum Migrieren von Daten müssen Sie erneut eine Verbindung mit ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure herstellen.  
  
**So öffnen Sie ein Projekt**  
  
1.  Verwenden Sie eines der folgenden Verfahren:  
  
    -   Zeigen Sie im Menü **Datei** auf **zuletzt verwendete Projekte**, und wählen Sie dann das Projekt aus, das Sie öffnen möchten.  
  
    -   Wählen Sie im Menü **Datei** die Option **Projekt öffnen**aus, suchen Sie die Projektdatei. s2ssproj, wählen Sie die Datei aus, und klicken Sie dann auf **Öffnen**.  
  
2.  Um die Verbindung mit der ASE wiederherzustellen, wählen Sie im Menü **Datei** die Option **Verbindung mit Sybase wiederherstellen**aus.  
  
3.  Wählen Sie zum erneuten Herstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure im Menü **Datei** die Option **Verbindung wieder**herstellen aus, um die Verbindung mit SQL Azure wiederherzustellen SQL Server  /  **Reconnect to SQL Azure**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, eine [Verbindung mit der Sybase-ASE herzustellen](connecting-to-sybase-ase-sybasetosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Herstellen einer Verbindung mit der Sybase-ASE &#40;sybaseto SQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[Herstellen einer Verbindung mit SQL Server &#40;Sybase-SQL-&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;Sybase&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
