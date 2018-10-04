---
title: Arbeiten mit SSMA-Projekten (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: bc0bdfac0ed1f1c4f992db8ef833d6f092b3fb53
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677914"
---
# <a name="working-with-ssma-projects-oracletosql"></a>Arbeiten mit SSMA-Projekten (OracleToSQL)
Migrieren von Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], erstellen Sie zunächst ein SSMA-Projekt. Das Projekt ist eine Datei mit den folgenden Informationen an:  
  
-   Metadaten für den Oracle-Datenbanken, die Sie zum migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Metadaten zu der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erhalten, die die migrierten Objekte und Daten.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungsinformationen.  
  
-   Projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird er getrennt von Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mit der Sie offline arbeiten. Informationen zum Wiederherstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen die standardmäßigen Projekteinstellungen  
SSMA enthält mehrere Einstellungen zum Umrechnen und laden die Datenbankobjekte, Migrieren von Daten und Synchronisieren von SSMA für Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Die Standardeinstellungen eignen sich für viele Benutzer. Bevor Sie ein neues SSMA-Projekt erstellen, sollten Sie jedoch die Einstellungen überprüfen. Wenn Sie möchten, können Sie die Standardeinstellungen ändern, die für alle neuen Projekte verwendet werden.  
  
**Standardprojekteinstellungen überprüfen**  
  
1.  Auf der **Tools** Menü klicken Sie auf **Projekt Standardeinstellungen**.  
  
2.  Wählen Sie den Projekttyp in **Migration Zielversion** Dropdownmenü für die Einstellungen sind erforderlich, angezeigt oder geändert werden soll, und klicken Sie dann auf **allgemeine** Registerkarte.  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Klicken Sie im rechten Bereich überprüfen Sie und ändern Sie die Einstellungen nach Bedarf. Weitere Informationen zu diesen Einstellungen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md).  
  
5.  Wiederholen Sie die Schritte 1 bis 3 für die Migration, Synchronisierung, beim Laden von Systemobjekten, grafische Benutzeroberfläche und Type Mapping-Seiten.  
  
    -   Weitere Informationen zu den migrationseinstellungen finden Sie unter [Projekteinstellungen &#40;Migration&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md).  
  
    -   Weitere Informationen zu den Einstellungen der System-Objekt finden Sie unter [Projekteinstellungen&#40;Laden von Systemobjekten&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md).  
  
    -   Weitere Informationen zu Einstellungen für die Synchronisierung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Projekteinstellungen&#40;Synchronisierung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md).  
  
    -   Weitere Informationen zu den GUI-Einstellungen finden Sie unter [Projekteinstellungen &#40;GUI&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md).  
  
    -   Weitere Informationen zu den Einstellungen der Zuordnung von Datentypen finden Sie unter [Projekteinstellungen &#40;Typzuordnung&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Migrieren von Daten aus Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], müssen Sie zunächst ein Projekt erstellen.  
  
**Zum Erstellen eines Projekts**  
  
1.  Auf der **Datei** Menü klicken Sie auf **neues Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
3.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt, und klicken Sie dann auf **OK**.  
  
4.  In der **Migration zu** öffnen Sie die Dropdownliste, wählen Sie die Version des Ziels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL-Datenbank  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren von standardmäßigen projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Setting Project Options Projektoptionen &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
Wenn Sie datentypzuordnungen zwischen Quell-und Zieldatenbanken anpassen, können Sie Zuordnungen auf das Projekt, Datenbank oder Objektebene definieren. Weitere Informationen finden Sie unter [Zuordnen von Oracle- und SQL Server-Datentypen &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Wenn Sie ein Projekt speichern, behält SSMA den projekteinstellungen und optional die Datenbank-Metadaten zu der Projektdatei.  
  
**Um ein Projekt zu speichern.**  
  
-   Auf der **Datei** Menü klicken Sie auf **Projekt speichern**.  
  
    Wenn die Schemas im Projekt geändert haben oder nicht konvertiert wurden, fordert SSMA Sie zum Laden und Speichern von Metadaten. Laden und Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine vollständige Projektdatei an andere Personen ein, z. B. Mitarbeiter des technischen Supports senden. Wenn Sie aufgefordert werden, um Metadaten zu speichern, führen Sie folgende Schritte aus:  
  
    1.  Für jedes Schema, das dem Status **fehlenden Metadaten**, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
        Speichern von Metadaten kann mehrere Minuten dauern. Wenn Sie noch keine Metadaten speichern möchten, Sie keine Kontrollkästchen aktivieren.  
  
    2.  Klicken Sie auf die **speichern** Schaltfläche.  
  
        SSMA analysiert die Oracle-Schemas und speichern Sie die Metadaten zu der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird er getrennt von Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mit der Sie offline arbeiten. Um Metadaten zu aktualisieren, laden Sie die Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Zum Migrieren von Daten müssen Sie eine Verbindung mit Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Um ein Projekt zu öffnen.**  
  
1.  Verwenden Sie eine der folgenden Verfahren:  
  
    -   Auf der **Datei** Startmenü **zuletzt geöffnete Projekte**, und klicken Sie dann auf das Projekt, das Sie öffnen möchten.  
  
    -   Auf der **Datei** , wählen Sie im Menü **geöffneten Projekt**, suchen Sie die Projektdatei .o2ssproj, wählen Sie die Datei, und klicken Sie dann auf **öffnen**.  
  
2.  Verbindung zu Oracle, auf die **Datei** Menü klicken Sie auf **Wiederherstellen der Verbindung mit Oracle**.  
  
3.  Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf die **Datei** Menü klicken Sie auf **Wiederherstellen der Verbindung mit SQL Server**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit Oracle-Datenbank (OracleToSQL)](http://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Herstellen einer Verbindung mit Oracle-Datenbank &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[Herstellen einer Verbindung mit SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
