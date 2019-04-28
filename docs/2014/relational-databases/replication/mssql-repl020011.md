---
title: MSSQL_REPL020011 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 481e0b383fd877ec81385bcd4ca4ee37106bb298
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63022766"
---
# <a name="mssqlrepl020011"></a>MSSQL_REPL020011
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20011|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Der Prozess konnte '%1' nicht auf '%2' ausführen.|  
  
## <a name="explanation"></a>Erklärung  
 Dieser Fehler kann unter verschiedenen Bedingungen während der Transaktionsreplikationsverarbeitung ausgelöst werden, z.B., wenn der Protokolllese-Agent **sp_replcmds** ausführt (Der Prozess konnte „sp_replcmds“ nicht auf \<Servername> ausführen) oder **sp_repldone** ausführt (Der Prozess konnte „sp_repldone“ nicht auf \<Servername> ausführen).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn der Fehler in einer Datenbank ausgelöst wird, die Sie gerade erst aus einer Sicherung wiederhergestellt haben, müssen Sie sicherstellen, dass die in der Dokumentation zum Sichern und Wiederherstellen genannten Schritte ausgeführt wurden. Dazu zählt bei Bedarf auch die Ausführung von **sp_replrestart** . Weitere Informationen finden Sie unter [Strategien zum Sichern und Wiederherstellen einer Momentaufnahme- und Transaktionsreplikation](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Bei diesem Fehler handelt es sich um einen internen Verarbeitungsfehler. Wenn er nicht im Zusammenhang mit einer Wiederherstellung ausgelöst wird, weist er in der Regel darauf hin, dass die Replikation entfernt und neu konfiguriert werden muss. Wenn das Entfernen der Replikation nicht möglich ist, wenden Sie sich an den Kundendienst.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)   
 [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
