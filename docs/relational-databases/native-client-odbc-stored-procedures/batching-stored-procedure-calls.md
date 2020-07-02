---
title: Batch Verarbeitung von Aufrufen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c357c5c5830aac57b9489537df96b339af882ab4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755622"
---
# <a name="batching-stored-procedure-calls"></a>Batchverarbeitung von gespeicherten Prozeduraufrufen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber stapelt bei Bedarf automatisch Aufrufe gespeicherter Prozeduren an den Server. Der Treiber führt diese Aktion nur aus, wenn die ODBC CALL-Escapesequenz verwendet wird, aber nicht für die [!INCLUDE[tsql](../../includes/tsql-md.md)]-EXECUTE-Anweisung. Durch die Batchverarbeitung gespeicherter Prozeduraufrufe wird die Anzahl der Roundtrips zum Server reduziert und die Leistung deutlich verbessert.  
  
 Der Treiber führt Prozeduraufrufe an den Server als Batches aus, wenn Sie einen Batch ausführen, der mehrere ODBC CALL-Escapesequenzen enthält. Außerdem werden Prozeduraufrufe als Batches ausgeführt, wenn gebundene Parameterarrays mit einer ODBC CALL-Escapesequenz verwendet werden. Wenn Sie z. b. entweder zeilenweise oder spaltenweise Parameter Bindung verwenden, um ein Array mit fünf Elementen an die Parameter einer SQL-Anweisung des ODBC-Anrufs zu binden, sendet der Treiber beim Aufrufen von **SQLExecute** oder **SQLExecDirect** einen einzelnen Batch mit fünf Prozedur aufrufen an den Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
