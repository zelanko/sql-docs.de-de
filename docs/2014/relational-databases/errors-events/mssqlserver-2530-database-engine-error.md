---
title: MSSQLSERVER_2530 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bb321f89c70983855e00b3eec4382c51fce1e16
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552049"
---
# <a name="mssqlserver_2530"></a>MSSQLSERVER_2530
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2530|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_INDEX_IS_OFFLINE|  
|Meldungstext|Der „%.*ls“-Index für die „%.\*ls“-Tabelle ist deaktiviert.|  
  
## <a name="explanation"></a>Erklärung  
 Die DBCC-Anweisung kann nicht fortfahren, da der angegebene Index deaktiviert wurde. Nachdem ein Index deaktiviert wurde, verbleibt er in einem deaktivierten Status, bis er neu erstellt oder gelöscht und erneut erstellt wird.  
  
## <a name="user-action"></a>Benutzeraktion  
  
1.  Aktivieren Sie den deaktivierten Index mit einer der folgenden Methoden:  
  
    -   ALTER INDEX-Anweisung mit der REBUILD-Klausel  
  
    -   CREATE INDEX mit der DROP_EXISTING-Klausel  
  
    -   DBCC DBREINDEX  
  
2.  Führen Sie die DBCC-Anweisung erneut aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren von Indizes und Einschränkungen](../indexes/enable-indexes-and-constraints.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
