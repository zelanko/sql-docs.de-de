---
title: Sichern und Wiederherstellen von Volltextkatalogen und Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], backing up
- full-text search [SQL Server], back up and restore
- recovery [full-text search]
- backups [SQL Server], full-text indexes
- full-text indexes [SQL Server], restoring
- restore operations [full-text search]
ms.assetid: 6a4080d9-e43f-4b7b-a1da-bebf654c1194
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 28ab36c2f9f500df89b1d936ec60871c0904bc1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012821"
---
# <a name="back-up-and-restore-full-text-catalogs-and-indexes"></a>Sichern und Wiederherstellen von Volltextkatalogen und Indizes
  In diesem Thema wird erläutert, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellte Volltextindizes sichern und wiederherstellen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist der Volltextkatalog ein logisches Konzept und befindet sich nicht in einer Dateigruppe. Um in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]einen Volltextkatalog zu sichern, müssen Sie daher jede Dateigruppe identifizieren, die einen Volltextindex enthält, der zum Katalog gehört. Dann müssen Sie diese Dateigruppen einzeln sichern.  
  
> [!IMPORTANT]  
>  Beim Aktualisieren einer [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbank ist es möglich, Volltextkataloge zu importieren. Jeder importierte Volltextkatalog ist eine Datenbankdatei in einer eigenen Dateigruppe. Um einen importierten Katalog zu sichern, können Sie einfach die entsprechende Dateigruppe sichern. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Volltextkatalogen](https://go.microsoft.com/fwlink/?LinkID=121052)in der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Onlinedokumentation.  
  
##  <a name="backingup"></a> Sichern der Volltextindizes eines Volltextkatalogs  
  
###  <a name="Find_FTIs_of_a_Catalog"></a> Suchen der Volltextindizes eines Volltextkatalogs  
 Sie können die Eigenschaften der Volltextindizes abrufen, indem Sie die folgende [SELECT](/sql/t-sql/queries/select-transact-sql) -Anweisung verwenden. Diese Anweisung wählt Spalten aus den Katalogsichten [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql) und [sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql) aus.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @TableID int;  
SET @TableID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product'));  
SELECT object_name(@TableID), i.is_enabled, i.change_tracking_state,   
   i.has_crawl_completed, i.crawl_type, c.name as fulltext_catalog_name   
   FROM sys.fulltext_indexes i, sys.fulltext_catalogs c   
   WHERE i.fulltext_catalog_id = c.fulltext_catalog_id;  
GO  
```  
  

  
###  <a name="Find_FG_of_FTI"></a> Suchen der Dateigruppe oder der Datei, die einen Volltextindex enthält  
 Wenn ein Volltextindex erstellt wird, wird dieser an einem der folgenden Speicherorte gespeichert:  
  
-   In einer vom Benutzer angegebenen Dateigruppe  
  
-   In derselben Dateigruppe als Basistabelle oder Sicht für eine nicht partitionierte Tabelle  
  
-   In der primären Dateigruppe für eine partitionierte Tabelle  
  
> [!NOTE]  
>  Informationen zum Erstellen eines Volltextindex finden Sie unter [Erstellen und Verwalten von Volltextindizes](create-and-manage-full-text-indexes.md)[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).  
  
 Um die Dateigruppe eines Volltextindex für eine Tabelle oder Sicht zu finden, verwenden Sie die folgende Abfrage, in der *object_name* für den Namen der Tabelle oder Sicht steht:  
  
```  
SELECT name FROM sys.filegroups f, sys.fulltext_indexes i   
   WHERE f.data_space_id = i.data_space_id   
      and i.object_id = object_id('object_name');  
GO  
  
```  
  

  
###  <a name="Back_up_FTIs_of_FTC"></a> Sichern der Dateigruppen, die Volltextindizes enthalten  
 Nachdem Sie die Dateigruppen gefunden haben, die die Indizes eines Volltextkatalogs enthalten, müssen Sie die einzelnen Dateigruppen sichern. Während der Sicherung können Volltextkataloge nicht gelöscht oder hinzugefügt werden.  
  
 Die erste Sicherung einer Dateigruppe muss eine vollständige Dateisicherung sein. Nachdem Sie eine vollständige Dateisicherung für eine Dateigruppe erstellt haben, können Sie bei Bedarf nur die Änderungen in einer Dateigruppe sichern, indem Sie eine oder mehrere differenzielle Dateisicherungen erstellen, die auf dieser vollständigen Dateisicherung basieren.  
  
 **So sichern Sie Dateien und Dateigruppen**  
  
-   [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](../backup-restore/back-up-files-and-filegroups-sql-server.md)  
  
-   [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)  
  

  
##  <a name="Restore_FTI"></a> Wiederherstellen eines Volltextindexes  
 Beim Wiederherstellen einer gesicherten Dateigruppe werden die Volltextindexdateien und die anderen Dateien der Dateigruppe wiederhergestellt. Standardmäßig wird die Dateigruppe an dem Speicherort auf einem Datenträger wiederhergestellt, an dem die Dateigruppe gesichert wurde.  
  
 Wenn bei der Erstellung der Sicherung eine Tabelle mit Volltextindizierung online war und eine Auffüllung ausgeführt wurde, wird die Auffüllung nach der Wiederherstellung fortgesetzt.  
  
 **So stellen Sie eine Dateigruppe wieder her**  
  
-   [Wiederherstellen von Dateien und Dateigruppen &#40;SQL Server&#41;](../backup-restore/restore-files-and-filegroups-sql-server.md)  
  
-   [Wiederherstellen von Dateien und Dateigruppen über vorhandene Dateien &#40;SQL Server&#41;](../backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
-   [Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  

  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten und Überwachen der Volltextsuche auf einer Serverinstanz](manage-and-monitor-full-text-search-for-a-server-instance.md)   
 [Upgrade der Volltextsuche](upgrade-full-text-search.md)  
  
  
