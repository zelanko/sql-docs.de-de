---
title: Systemintern kompilierte gespeicherte Prozeduren und deren Ausführung mit SET-Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: baf4de1df4bdd64b32182e6fbb72fbbd0ed110b6
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394468"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Systemintern kompilierte gespeicherte Prozeduren und deren Ausführung mit SET-Optionen
  Sitzungsoptionen sind in ATOMIC-Blöcken fest definiert. Die Ausführung einer gespeicherten Prozedur wird durch die SET-Optionen einer Sitzung nicht beeinflusst. Bestimmte SET-Optionen, wie SET NOEXEC und SET SHOWPLAN_XML, bewirken jedoch, dass gespeicherte Prozeduren (einschließlich systemintern kompilierter gespeicherter Prozeduren) nicht ausgeführt werden.  
  
 Wenn eine systemintern kompilierte gespeicherte Prozedur mit einer aktivierten STATISTICS-Option ausgeführt wird, werden Statistiken für die Prozedur als Ganzes und nicht pro Anweisung erfasst. Weitere Informationen finden Sie unter [SET STATISTICS IO &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-io-transact-sql), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-profile-transact-sql), [SET STATISTICS TIME &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-time-transact-sql) und [SET STATISTICS XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql). Um für systemintern gespeicherte Prozeduren eine Ausführungsstatistik pro Anweisung abzurufen, verwenden Sie für das sp_statement_completed-Ereignis eine Sitzung für erweiterte Ereignisse. Diese startet, nachdem alle Abfragen in der Ausführung einer gespeicherten Prozedur abgeschlossen sind. Weitere Informationen zum Erstellen einer Sitzung für erweiterte Ereignisse finden Sie unter [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql).  
  
 `SHOWPLAN_XML` wird für systemintern kompilierte gespeicherte Prozeduren unterstützt. `SHOWPLAN_ALL` und `SHOWPLAN_TEXT` werden bei systemintern kompilierten gespeicherten Prozeduren nicht unterstützt.  
  
 `SET FMTONLY` wird bei systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Verwenden Sie stattdessen [sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [Systemintern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
