---
title: Arbeiten mit SSMA-Projekten (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Working with SSMA projects, create new project
- Working with SSMA projects, customize settings
- Working with SSMA projects, Open project
- Working with SSMA projects, Save project
ms.assetid: 9e4394e9-f177-41d9-839e-5d53a9c9b840
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 518f899118d5a7d2dce4f56d185fce9d5b1e47df
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661669"
---
# <a name="working-with-ssma-projects-mysqltosql"></a>Arbeiten mit SSMA-Projekten (MySqlToSql)
Um MySQL-Datenbanken zu SQL Server oder SQL Azure zu migrieren, müssen Sie zuerst ein SSMA-Projekt erstellen. Das Projekt ist eine Datei mit den folgenden Informationen an:  
  
-   Metadaten über die MySQL-Datenbanken, die Sie in SQL Server oder SQL Azure migrieren möchten.  
  
-   Metadaten zu der Zielinstanz von SQL Server oder SQL Azure, die die migrierten Objekte und Daten erhält.  
  
-   SQL Server oder SQL Azure-Verbindungsinformationen.  
  
-   Projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird er von MySQL und SQL Server oder SQL Azure getrennt. Mit der Sie offline arbeiten. Weitere Informationen zum Wiederherstellen der Verbindung mit SQL Server, finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen die standardmäßigen Projekteinstellungen  
SSMA enthält verschiedene Einstellungen für konvertieren und laden die Datenbank, Migrieren von Daten und Synchronisieren von SSMA für MySQL und SQL Server oder SQL Azure. Die Standardeinstellungen eignen sich für viele Benutzer. Bevor Sie ein neues SSMA-Projekt erstellen, sollten Sie jedoch die Einstellungen überprüfen. Falls erforderlich, können Sie die Standardeinstellungen ändern, die für alle neuen Projekte verwendet werden.  
  
##### <a name="to-review-default-project-settings"></a>Standardprojekteinstellungen überprüfen  
  
1.  Wählen Sie **Projekt Standardeinstellungen** aus der **Tools** Menü.  
  
2.  Wählen Sie den Projekttyp in **Migration Zielversion** Dropdownliste aus, welche Einstellungen angezeigt oder geändert werden, und klicken Sie auf **allgemeine** Registerkarte.  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Klicken Sie im rechten Bereich überprüfen Sie und ändern Sie die Einstellungen nach Bedarf. Weitere Informationen zu diesen Einstellungen finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;MySQLToSQL&#41; ](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  Wiederholen Sie die Schritte 1 bis 3 für die Migration, Synchronisierung, SQL Azure, grafische Benutzeroberfläche und Type Mapping-Seiten.  
  
-   Weitere Informationen zu den migrationseinstellungen finden Sie unter [Projekteinstellungen &#40;Migration&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   Weitere Informationen zu den Einstellungen für die Synchronisierung mit SQL Server finden Sie unter [Projekteinstellungen &#40;Synchronisierung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   Weitere Informationen zu den GUI-Einstellungen finden Sie unter [Project Settings (GUI) (häufig SSMA)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
-   Weitere Informationen zu den Einstellungen der Zuordnung von Datentypen finden Sie unter [Projekteinstellungen &#40;Typzuordnung&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   Weitere Informationen zu SQL Azure-Einstellungen finden Sie unter [Projekteinstellungen &#40;Azure SQL-Datenbank&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> Die SQL Azure-Einstellungen werden angezeigt, nur, wenn Sie auswählen, **Migration zu SQL Azure** beim Erstellen eines Projekts.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Um Daten aus MySQL-Datenbanken zu SQL Server oder SQL Azure zu migrieren, müssen Sie ein Projekt erstellen.  
  
##### <a name="to-create-a-new-project"></a>Zum Erstellen eines neuen Projekts  
  
1.  Wählen Sie **neues Projekt** aus der **Datei** Menü. Das Dialogfeld **Neues Projekt** wird angezeigt. Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
3.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt.  
  
4.  In der **Migration zu** öffnen Sie die Dropdownliste, wählen Sie die Version des Ziels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   Azure SQL-Datenbank  
  
Und klicken Sie dann auf **OK**  
  
SSMA erstellt die Projektdatei.  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Projekteinstellungen, die an den neuen SSMA-Projekten, die Sie anwenden können auch die Einstellungen für jedes Projekt anpassen, zusätzlich zum Definieren der Standardwert. Weitere Informationen finden Sie unter [Setting Project Options Projektoptionen &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
Wenn Sie die replikationsdatentyp-Zuordnungen zwischen den Quell- und Zieldatenbanken anpassen, können Sie Zuordnungen auf das Projekt, Datenbank oder Objektebene definieren. Weitere Informationen finden Sie unter [Zuordnen von MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Das Speichern von Projekten-Feature kann der Benutzer im Wesentlichen den projekteinstellungen und (optional) die Datenbank-Metadaten in der SSMA-Projektdatei zu speichern.  
  
##### <a name="to-save-a-project"></a>Um ein Projekt zu speichern.  
  
-   Auf der **Datei** , wählen Sie im Menü **speichern** Projekt.  
  
Wenn Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, fordert SSMA Sie zum Laden und Speichern von Metadaten. Laden und Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine vollständige Projektdatei an andere Personen ein, z. B. Mitarbeiter des technischen Supports senden. Wenn Sie aufgefordert werden, um Metadaten zu speichern, führen Sie folgende Schritte aus:  
  
1.  Für jede Datenbank, die dem Status **fehlenden Metadaten**, wählen Sie das Kontrollkästchen neben dem Datenbanknamen. Speichern von Metadaten kann mehrere Minuten dauern. Wenn Sie nicht, um Metadaten an diesem Punkt zu speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
2.  Klicken Sie auf **Speichern**.  
  
SSMA wird die MySQL-Schemas zu analysieren und speichern Sie die Metadaten zu der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird er von MySQL und SQL Server oder SQL Azure-getrennt. Dadurch können Sie offline arbeiten. Um Metadaten zu aktualisieren, laden Sie Datenbankobjekte in SQL Server oder SQL Azure aus. Zum Migrieren von Daten müssen Sie eine Verbindung mit SQL Server oder SQL Azure wiederherstellen.  
  
##### <a name="to-open-a-project"></a>Um ein Projekt zu öffnen.  
  
1.  Verwenden Sie eine der folgenden Verfahren:  
  
    1.  Auf der **Datei** Startmenü **zuletzt geöffnete Projekte**.  
  
    2.  Wählen Sie das Projekt, die, das Sie öffnen möchten.  
  
    3.  Auf der **Datei** , wählen Sie im Menü **geöffneten Projekt**, suchen Sie die Projektdatei .m2ssproj, wählen Sie die Datei, und klicken Sie dann auf **öffnen**.  
  
2.  Verbindung mit MySQL, auf die **Datei** , wählen Sie im Menü **Wiederherstellen der Verbindung mit MySQL**.  
  
3.  Verbindung zu SQL Server, auf die **Datei** , wählen Sie im Menü **Wiederherstellen der Verbindung mit SQL Server**.  
  
4.  Verbindung zu SQL Azure, auf die **Datei** , wählen Sie im Menü **Erneutes Verbinden mit SQL Azure.**  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Herstellen einer Verbindung mit SQLServer &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
