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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 965b04d609053dabae694b2409677d0499497186
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85788037"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Bei ausgeführten Anweisungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nimmt der Native Client-ODBC-Treiber den Server nicht an, um die Anzahl der Spalten in einem Resultset zu melden. In diesem Fall verursacht **SQLNumResultCols** keinen Serverroundtrip. Wie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) und [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)wird beim Aufrufen von **SQLNumResultCols** bei vorbereiteten, aber nicht ausgeführten Anweisungen ein Serverroundtrip generiert.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder ein Anweisungsbatch mehrere Resultsets für Zeilen zurückgibt, kann die Anzahl der Resultset-Spalten sich von einem Set zum nächsten ändern. **SQLNumResultCols** sollte für jeden Satz aufgerufen werden. Wenn sich die Anzahl der Spalten ändert, sollte die Anwendung Datenwerte vor dem Abrufen von Zeilenergebnissen erneut binden. Weitere Informationen zum Verarbeiten mehrerer Resultsets finden Sie unter [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Verbesserungen in der Datenbank-Engine, die mit beginnen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ermöglichen SQLNumResultCols, genauere Beschreibungen der erwarteten Ergebnisse zu erhalten. Diese präziseren Ergebnisse können sich von den Werten unterscheiden, die von SQLNumResultCols in früheren Versionen von zurückgegeben wurden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLNumResultCols-Funktion](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
