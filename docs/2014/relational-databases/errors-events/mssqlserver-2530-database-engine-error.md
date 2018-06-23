---
title: MSSQLSERVER_2530 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ccf0b157984cce59ceff84fcff0c25a2f708e26f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161815"
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
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
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren von Indizes und Einschränkungen](../indexes/enable-indexes-and-constraints.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dbreindex-transact-sql)  
  
  
