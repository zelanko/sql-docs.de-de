---
title: MSSQLSERVER_2530 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dc84999be0485c9b6aa03875d0e96978b0531f0b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2530"></a>MSSQLSERVER_2530
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Aktivieren von Indizes und Einschränkungen](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
