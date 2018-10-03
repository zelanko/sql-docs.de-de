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
manager: craigg
ms.openlocfilehash: 8058c7c31c49935d244726bf9e8ea0ac6cfbe750
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215490"
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
  
  
