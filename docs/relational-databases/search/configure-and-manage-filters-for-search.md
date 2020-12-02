---
description: Konfigurieren und Verwalten von Filtern für die Suche
title: Konfigurieren und Verwalten von Filtern für die Suche | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ebeaebbc4a082bcb7051dc3d6c784b6ce1ec11fc
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96130952"
---
# <a name="configure-and-manage-filters-for-search"></a>Konfigurieren und Verwalten von Filtern für die Suche
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Die Indizierung von Dokumenten in einer Spalte mit den Datentypen **varbinary**, **varbinary(max)**, **image** oder **xml** erfordert zusätzliche Verarbeitungsschritte. Diese Verarbeitung muss von einem Filter durchgeführt werden. Der Filter extrahiert die Textinformationen aus dem Dokument (hierbei wird die Formatierung entfernt). Der Filter überträgt den Text anschließend an die Komponente für die Wörtertrennung für die Sprache, die der Tabellenspalte zugeordnet ist.  
 
## <a name="filters-and-document-types"></a>Filter und Dokumenttypen
Ein bestimmter Filter ist immer spezifisch für einen bestimmten Dokumenttyp (DOC, PDF, XLS, XML usw.). Diese Filter implementieren die IFilter-Schnittstelle. Weitere Informationen zu diesen Dokumenttypen erhalten Sie, indem Sie die [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md) -Katalogsicht abfragen.  
  
Binäre Dokumente können in einer einzelnen **varbinary(max)** - oder **image** -Spalte gespeichert werden. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wählt für jedes Dokument anhand der Dateierweiterung den entsprechenden Filter aus. Da die Dateierweiterung nicht sichtbar ist, wenn die Datei in einer **varbinary(max)** - oder **image** -Spalte gespeichert wird, muss die Dateierweiterung (DOC, XLS, PDF usw.) in einer separaten Spalte der Tabelle gespeichert werden. Diese wird als Typspalte bezeichnet. Die Typspalte kann einen beliebigen zeichenbasierten Datentyp aufweisen. Sie enthält die Dokumentdateierweiterung, beispielsweise DOC für ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word-Dokument. In der **Document** -Tabelle in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]hat die **Document** -Spalte den Typ **varbinary(max)**, und die Typspalte **FileExtension** hat den Typ **nvarchar(8)**.  

**So zeigen Sie die Typspalte in einem vorhandenen Volltextindex an**  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
  
> [!NOTE]  
>  Ein Filter kann ggf. eingebettete Objekte im übergeordneten Objekt behandeln. Dies ist abhängig von der Implementierung des Filters. Filter werden in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch nicht für das Verfolgen von Links zu anderen Objekten konfiguriert.  

## <a name="installed-filters"></a>Installierte Filter 
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert seine eigenen XML- und HTML-Filter. Zusätzlich lädt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auch alle Filter für proprietäre Formate von [!INCLUDE[msCoName](../../includes/msconame-md.md)] (.doc, .xdoc, .ppt usw.), die bereits im Betriebssystem installiert sind. Um die Filter zu identifizieren, die gerade auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen werden, verwenden Sie die gespeicherte Prozedur [sp_help_fulltext_system_components](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md) wie folgt:  

```sql
EXEC sp_help_fulltext_system_components 'filter';   
```  

> [!NOTE]
> Selbst in der neuesten Version des Office Filter Pack, das XLSX-Support enthält, unterstützt SQL Server keine Strict Open XML-Tabellen.  Es wird jedoch kein Fehler zurückgegeben. In SQL Server wird der Inhalt von Strict Open XML-Tabellen einfach nicht indiziert.

## <a name="non-microsoft-filters"></a>Nicht-Microsoft-Filter
Bevor Sie Filter für nicht von [!INCLUDE[msCoName](../../includes/msconame-md.md)] stammende Formate verwenden können, müssen Sie sie jedoch manuell in die Serverinstanz laden. Weitere Informationen zum Installieren zusätzlicher Filter finden Sie unter [Anzeigen oder Ändern von registrierten Filtern und Wörtertrennungen](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)   
 [FILESTREAM-Kompatibilität mit anderen SQL Server-Funktionen](../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
