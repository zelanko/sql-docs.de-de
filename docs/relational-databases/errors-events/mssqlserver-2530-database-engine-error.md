---
description: MSSQLSERVER_2530
title: MSSQLSERVER_2530 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
ms.assetid: 5d4be07a-38a5-4b25-819c-4dcb4636cc15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3da9afc7a5a648b541cf88a2d83aa6c738895832
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482821"
---
# <a name="mssqlserver_2530"></a>MSSQLSERVER_2530
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
[Aktivieren von Indizes und Einschränkungen](~/relational-databases/indexes/enable-indexes-and-constraints.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](~/t-sql/statements/create-index-transact-sql.md)  
[DBCC DBREINDEX &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)  
  
