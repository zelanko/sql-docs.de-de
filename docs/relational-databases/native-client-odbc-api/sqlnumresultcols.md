---
title: SQLNumResultCols | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5ec47c112a41d579710a42c1913785d794f040c
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786036"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Bei ausgeführten Anweisungen wird vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber der Server nicht zum Melden der Anzahl von Spalten in einem Resultset besucht. In diesem Fall verursacht **SQLNumResultCols** keinen Serverroundtrip. Wie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) und [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)wird beim Aufrufen von **SQLNumResultCols** bei vorbereiteten, aber nicht ausgeführten Anweisungen ein Serverroundtrip generiert.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. **SQLNumResultCols** sollte für jeden Satz aufgerufen werden. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Verbesserungen in der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ermöglichen SQLNumResultCols, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von SQLNumResultCols zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLNumResultCols-Funktion](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
