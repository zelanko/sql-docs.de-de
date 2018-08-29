---
title: SQLNumResultCols | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1c41aaa9348008707d0f883d68ca0f189470ac20
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078941"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Bei ausgeführten Anweisungen geht der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ist nicht besuchen Sie den Server aus, um die Anzahl der Spalten in einem Resultset zu melden. In diesem Fall **SQLNumResultCols** bewirkt nicht, dass ein Server-Roundtrip erstellt. Wie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) und [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), wird beim Aufruf **SQLNumResultCols** für vorbereitete aber nicht ausgeführte Anweisungen ein Server-Roundtrip erstellt.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. **SQLNumResultCols** für jede Gruppe aufgerufen werden soll. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Arbeiten mit mehreren resultsetergebnissen, finden Sie unter [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Verbesserungen in der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLNumResultCols abrufen genauere Beschreibungen der erwarteten Ergebnisse zu ermöglichen. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten, die vom SQLNumResultCols in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLNumResultCols-Funktion](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
