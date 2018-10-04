---
title: MSSQLSERVER_601 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "601"
helpviewer_keywords:
- 601 (Database Engine error)
ms.assetid: 2039cc0a-9a43-4369-a04a-935e384388b6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9aebe73ac73ee09ed2ba6de9162877d0e70bc7e6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176900"
---
# <a name="mssqlserver601"></a>MSSQLSERVER_601
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|601|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|Aufgrund von Datenverschiebungen konnte der Scanvorgang mit NOLOCK nicht fortgesetzt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Die Abfrage kann von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nicht weiter ausgeführt werden, da versucht wird, Daten zu lesen, die durch eine andere Transaktion aktualisiert oder gelöscht wurden. Für die Abfrage wird der Sperrhinweis NOLOCK oder die Isolationsstufe für Transaktionen READ UNCOMMITTED verwendet.  
  
 Normalerweise wird der Zugriff auf Daten verweigert, die durch eine andere Transaktion geändert wurden, da die Daten mit Sperren belegt werden. Mithilfe des Sperrhinweises NOLOCK und der Isolationsstufe für Transaktionen READ UNCOMMITTED können mit einer Abfrage jedoch Daten gelesen werden, die durch eine andere Transaktion gesperrt sind. Dies wird als Dirty Read bezeichnet, da Sie Werte lesen können, für die noch kein Commit ausgeführt wurde und an denen Änderungen vorgenommen werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Durch diesen Fehler wird die Abfrage abgebrochen. Übermitteln Sie die Abfrage erneut, oder entfernen Sie den Sperrhinweis NOLOCK.  
  
## <a name="see-also"></a>Siehe auch  
 [MSSQLSERVER_605](mssqlserver-605-database-engine-error.md)   
 [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)   
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)  
  
  
