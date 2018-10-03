---
title: MSSQL_ENG004929 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b879f78de050ddb8484607113235601457b4ee1e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210730"
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|4929|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Das %1!s!-Objekt '%2!s!' kann nicht geändert werden, da es für die Replikation veröffentlicht wird.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler tritt normalerweise auf, wenn Sie versuchen, die PRIMARY KEY-Einschränkung einer Tabelle zu löschen, die für die Transaktionsreplikation veröffentlicht wird. Die Transaktionsreplikation erfordert einen Primärschlüssel für jede veröffentlichte Tabelle. Aus diesem Grund kann die Einschränkung nicht gelöscht werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Um die Einschränkung zu löschen, löschen Sie zunächst den der Tabelle zugeordneten Artikel. Weitere Informationen finden Sie unter [Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen](publish/add-articles-to-and-drop-articles-from-existing-publications.md). Falls dieser Fehler in einer Datenbank auftritt, die nicht repliziert wird, führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) aus, um sicherzustellen, dass die Objekte in der Datenbank nicht als repliziert hervorgehoben sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
