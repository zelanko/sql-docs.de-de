---
title: Konfigurieren und Verwalten von Filtern für die Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997745"
---
# <a name="configure-and-manage-filters-for-search"></a>Konfigurieren und Verwalten von Filtern für die Suche
  Die Indizierung von Dokumenten in einer Spalte mit dem Datentyp `varbinary`, `varbinary(max)`, `image` oder `xml` erfordert zusätzliche Verarbeitungsschritte. Diese Verarbeitung muss von einem Filter durchgeführt werden. Der Filter extrahiert die Textinformationen aus dem Dokument (hierbei wird die Formatierung entfernt). Der Filter überträgt den Text anschließend an die Komponente für die Wörtertrennung für die Sprache, die der Tabellenspalte zugeordnet ist.  
  
 Ein bestimmter Filter ist immer spezifisch für einen bestimmten Dokumenttyp (DOC, PDF, XLS, XML usw.). Diese Filter implementieren die IFilter-Schnittstelle. Weitere Informationen zu diesen Dokumenttypen erhalten Sie, indem Sie die [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) -Katalogsicht abfragen.  
  
 Binäre Dokumente können in einer einzelnen `varbinary(max)`- oder `image`-Spalte gespeichert werden. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wählt für jedes Dokument anhand der Dateierweiterung den entsprechenden Filter aus. Da die Dateierweiterung nicht sichtbar ist, wenn die Datei in einer `varbinary(max)`- oder `image`-Spalte gespeichert wird, muss die Dateierweiterung (DOC, XLS, PDF usw.) in einer separaten Spalte der Tabelle gespeichert werden. Diese wird als Typspalte bezeichnet. Die Typspalte kann einen beliebigen zeichenbasierten Datentyp aufweisen. Sie enthält die Dokumentdateierweiterung, beispielsweise DOC für ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word-Dokument. In der **Document** -Tabelle in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] hat die **Document** -Spalte den Typ `varbinary(max)` , und die Typspalte **File Extension**hat den Typ `nvarchar(8)` .  
  
> [!NOTE]  
>  Ein Filter kann ggf. eingebettete Objekte im übergeordneten Objekt behandeln. Dies ist abhängig von der Implementierung des Filters. Filter werden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] jedoch nicht für das Verfolgen von Links zu anderen Objekten konfiguriert.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert seine eigenen XML- und HTML-Filter. Zusätzlich lädt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] auch alle Filter für proprietäre Formate von  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)](.doc, .xdoc, .ppt usw.), die bereits auf dem Betriebssystem installiert sind. Um die Filter zu identifizieren, die gerade auf eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]geladen werden, verwenden Sie die gespeicherte Prozedur [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) wie folgt:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Bevor Sie Filter für nicht von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] stammende Formate verwenden können, müssen Sie sie jedoch manuell in die Serverinstanz laden. Weitere Informationen zum Installieren zusätzlicher Filter finden Sie unter [Anzeigen oder Ändern von registrierten Filtern und Wörtertrennungen](view-or-change-registered-filters-and-word-breakers.md).  
  
 **So zeigen Sie die Typspalte in einem vorhandenen Volltextindex an**  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. fulltext_index_columns &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)   
 [FileStream-Kompatibilität mit anderen SQL Server Features](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
