---
title: Batchverarbeitung von gespeicherten Prozeduraufrufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1a6c75c4dd4d13a5905615836d666fe33769a6a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427789"
---
# <a name="batching-stored-procedure-calls"></a>Batchverarbeitung von gespeicherten Prozeduraufrufen
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber batches automatisch gespeicherte Prozeduraufrufe an den Server bei Bedarf. Der Treiber führt diese Aktion nur aus, wenn die ODBC CALL-Escapesequenz verwendet wird, aber nicht für die [!INCLUDE[tsql](../../includes/tsql-md.md)]-EXECUTE-Anweisung. Durch die Batchverarbeitung gespeicherter Prozeduraufrufe wird die Anzahl der Roundtrips zum Server reduziert und die Leistung deutlich verbessert.  
  
 Der Treiber führt Prozeduraufrufe an den Server als Batches aus, wenn Sie einen Batch ausführen, der mehrere ODBC CALL-Escapesequenzen enthält. Außerdem werden Prozeduraufrufe als Batches ausgeführt, wenn gebundene Parameterarrays mit einer ODBC CALL-Escapesequenz verwendet werden. Angenommen, Sie verwenden entweder zeilenweise oder spaltenweise parameterbindungen so binden ein Array mit fünf Elementen an die Parameter einer ODBC CALL SQL-Anweisung, wenn **SQLExecute** oder **SQLExecDirect** aufgerufen wird, der Treiber sendet einen einzelnen Batch mit fünf Prozeduraufrufen an den Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen gespeicherter Prozeduren](running-stored-procedures.md)  
  
  
