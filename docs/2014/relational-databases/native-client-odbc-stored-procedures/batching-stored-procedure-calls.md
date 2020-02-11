---
title: Batch Verarbeitung von Aufrufen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b50350006abba5085b11010f26aa88a89b07393f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205491"
---
# <a name="batching-stored-procedure-calls"></a>Batchverarbeitung von gespeicherten Prozeduraufrufen
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber stapelt bei Bedarf automatisch Aufrufe gespeicherter Prozeduren an den Server. Der Treiber führt diese Aktion nur aus, wenn die ODBC CALL-Escapesequenz verwendet wird, aber nicht für die [!INCLUDE[tsql](../../includes/tsql-md.md)]-EXECUTE-Anweisung. Durch die Batchverarbeitung gespeicherter Prozeduraufrufe wird die Anzahl der Roundtrips zum Server reduziert und die Leistung deutlich verbessert.  
  
 Der Treiber führt Prozeduraufrufe an den Server als Batches aus, wenn Sie einen Batch ausführen, der mehrere ODBC CALL-Escapesequenzen enthält. Außerdem werden Prozeduraufrufe als Batches ausgeführt, wenn gebundene Parameterarrays mit einer ODBC CALL-Escapesequenz verwendet werden. Wenn Sie z. b. entweder zeilenweise oder spaltenweise Parameter Bindung verwenden, um ein Array mit fünf Elementen an die Parameter einer SQL-Anweisung des ODBC-Anrufs zu binden, sendet der Treiber beim Aufrufen von **SQLExecute** oder **SQLExecDirect** einen einzelnen Batch mit fünf Prozedur aufrufen an den Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](running-stored-procedures.md)  
  
  
