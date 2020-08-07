---
title: Arbeiten mit SSMA-Projekten (mysqlto SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2d9bec916103214169f549a0b555a46fd0d65fdb
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862451"
---
# <a name="working-with-ssma-projects-mysqltosql"></a>Arbeiten mit SSMA-Projekten (MySqlToSql)
Um MySQL-Datenbanken zu SQL Server oder SQL Azure zu migrieren, müssen Sie zunächst ein SSMA-Projekt erstellen. Das Projekt ist eine Datei, die die folgenden Informationen enthält:  
  
-   Metadaten zu den MySQL-Datenbanken, die Sie zu SQL Server oder SQL Azure migrieren möchten.  
  
-   Metadaten zur Ziel Instanz von SQL Server oder SQL Azure, die die migrierten Objekte und Daten empfangen.  
  
-   SQL Server oder SQL Azure Verbindungsinformationen aus.  
  
-   Projekteinstellungen.  
  
Wenn Sie ein Projekt öffnen, wird es von MySQL getrennt, SQL Server oder SQL Azure. Auf diese Weise können Sie offline arbeiten. Weitere Informationen zum erneuten Herstellen einer Verbindung mit SQL Server finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;mysqldesql&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="reviewing-default-project-settings"></a>Überprüfen der Standard Projekteinstellungen  
SSMA enthält mehrere Einstellungen zum umrechnen und Laden von Datenbanken, zum Migrieren von Daten und zum Synchronisieren von SSMA mit MySQL und SQL Server oder SQL Azure. Die Standardeinstellungen sind für viele Benutzer geeignet. Bevor Sie jedoch ein neues SSMA-Projekt erstellen, sollten Sie die Einstellungen überprüfen. Falls erforderlich, können Sie die Standardeinstellungen ändern, die für alle neuen Projekte verwendet werden.  
  
##### <a name="to-review-default-project-settings"></a>So überprüfen Sie die Standard Projekteinstellungen  
  
1.  Wählen **Sie im Menü** Extras die Option **Standard Projekteinstellungen** aus.  
  
2.  Wählen Sie in der Dropdown Liste **Migrations Ziel Version** den Projekttyp aus, für den Einstellungen angezeigt/geändert werden sollen, und klicken Sie auf die Registerkarte **Allgemein**  
  
3.  Klicken Sie im linken Bereich auf **Konvertierung**.  
  
4.  Überprüfen Sie im rechten Bereich die Einstellungen, und ändern Sie Sie nach Bedarf. Weitere Informationen zu diesen Einstellungen finden Sie unter [Project Settings &#40;Conversion&#41; &#40;mysqltoisql&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md) .  
  
5.  Wiederholen Sie die Schritte 1-3 für die Seiten Migration, Synchronisierung, SQL Azure, GUI und Typzuordnung.  
  
-   Informationen zu den Migrations Einstellungen finden Sie unter [Project Settings &#40;Migration&#41; &#40;mysqlto SQL&#41;](../../ssma/mysql/project-settings-migration-mysqltosql.md).  
  
-   Informationen zu den Einstellungen für die Synchronisierung mit SQL Server finden Sie unter [Project Settings &#40;Synchronisierung&#41; &#40;mysqldesql&#41;](../../ssma/mysql/project-settings-synchronization-mysqltosql.md).  
  
-   Informationen zu den GUI-Einstellungen finden Sie unter [Projekteinstellungen (GUI) (SSMA Common)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693).  
  
-   Informationen zu den Einstellungen für die Datentyp Zuordnung finden Sie unter [Project Settings &#40;Type Mapping&#41; &#40;mysqlto SQL&#41;](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
-   Informationen zu SQL Azure Einstellungen finden Sie unter [Projekteinstellungen &#40;Azure SQL-Datenbank&#41; &#40;mysqldesql&#41;](../../ssma/mysql/project-settings-azure-sql-db-mysqltosql.md).  
  
> [!NOTE]  
> Die SQL Azure Einstellungen werden nur angezeigt, wenn Sie beim Erstellen eines Projekts **Migration zum SQL Azure** auswählen.  
  
## <a name="creating-new-projects"></a>Erstellen neuer Projekte  
Wenn Sie Daten aus MySQL-Datenbanken zu SQL Server oder SQL Azure migrieren möchten, müssen Sie ein Projekt erstellen.  
  
##### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus. Das Dialogfeld **Neues Projekt** wird angezeigt. Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  
  
3.  Geben Sie im Feld **Speicherort** einen Ordner für das Projekt ein, oder wählen Sie einen Ordner aus.  
  
4.  Wählen Sie in der Dropdown Liste **Migration zu** die Version des Ziels aus, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Migration verwendet wird. Die verfügbaren Optionen sind:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014  
  
    -   Azure SQL-Datenbank  
  
Und klicken Sie dann auf **OK** .  
  
SSMA erstellt die Projektdatei.  
  
## <a name="customizing-project-settings"></a>Anpassen von Projekteinstellungen  
Zusätzlich zum Definieren der Standard Projekteinstellungen, die für alle neuen SSMA-Projekte gelten, können Sie auch die Einstellungen für jedes Projekt anpassen. Weitere Informationen finden Sie unter [Festlegen von Projektoptionen &#40;mysqlto SQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).  
  
Wenn Sie Datentyp Zuordnungen zwischen den Quell-und Ziel Datenbanken anpassen, können Sie Zuordnungen auf Projekt-, Datenbank-oder Objektebene definieren. Weitere Informationen finden Sie unter [Mapping MySQL and SQL Server Data Types &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).  
  
## <a name="saving-projects"></a>Speichern von Projekten  
Die Funktion zum Speichern von Projekten ermöglicht dem Benutzer das Speichern der Projekteinstellungen und optional der Daten Bank Metadaten in der SSMA-Projektdatei.  
  
##### <a name="to-save-a-project"></a>So speichern Sie ein Projekt  
  
-   Wählen Sie im Menü **Datei** die Option Projekt **Speichern** aus.  
  
Wenn sich Datenbanken innerhalb des Projekts geändert haben oder nicht konvertiert wurden, werden Sie von SSMA aufgefordert, Metadaten zu laden und zu speichern. Durch das Laden und Speichern von Metadaten können Sie offline arbeiten. Außerdem können Sie eine komplette Projektdatei an andere Personen senden, z. b. technische Supportmitarbeiter. Wenn Sie zum Speichern von Metadaten aufgefordert werden, gehen Sie wie folgt vor:  
  
1.  Aktivieren Sie für jede Datenbank, die den Status **fehlender Metadaten**anzeigt, das Kontrollkästchen neben dem Datenbanknamen. Das Speichern von Metadaten kann einige Minuten dauern. Wenn Sie an diesem Punkt keine Metadaten speichern möchten, aktivieren Sie keine Kontrollkästchen.  
  
2.  Klicken Sie auf **Speichern**.  
  
SSMA analysiert die MySQL-Schemas und speichert die Metadaten in der Projektdatei.  
  
## <a name="opening-projects"></a>Öffnen von Projekten  
Wenn Sie ein Projekt öffnen, wird es von MySQL und von SQL Server oder SQL Azure getrennt. Auf diese Weise können Sie offline arbeiten. Laden Sie Datenbankobjekte in SQL Server oder SQL Azure, um Metadaten zu aktualisieren. Zum Migrieren von Daten müssen Sie erneut eine Verbindung mit SQL Server oder SQL Azure herstellen.  
  
##### <a name="to-open-a-project"></a>So öffnen Sie ein Projekt  
  
1.  Verwenden Sie eines der folgenden Verfahren:  
  
    1.  Zeigen Sie im Menü **Datei** auf **zuletzt geöffnete Projekte**.  
  
    2.  Wählen Sie das Projekt aus, das Sie öffnen möchten.  
  
    3.  Wählen Sie im Menü **Datei** die Option **Projekt öffnen**aus, suchen Sie die Projektdatei. m2ssproj, wählen Sie die Datei aus, und klicken Sie dann auf **Öffnen**.  
  
2.  Um erneut eine Verbindung mit MySQL herzustellen, wählen Sie im Menü **Datei** die Option **Verbindung mit MySQL wieder**herstellen aus.  
  
3.  Um die Verbindung mit SQL Server wiederherzustellen, wählen Sie im Menü **Datei** die Option **Verbindung wiederherstellen mit SQL Server**.  
  
4.  Um die Verbindung mit SQL Azure wiederherzustellen, wählen Sie im Menü **Datei** die Option **Verbindung wiederherstellen mit SQL Azure.**  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs ist das [Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Herstellen einer Verbindung mit MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Herstellen einer Verbindung mit SQL Server &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
[Herstellen einer Verbindung mit Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
