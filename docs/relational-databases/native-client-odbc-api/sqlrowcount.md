---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3cfb76dbd1732e32238c484f589d3b4696ff89d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302306"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Sind Arrays für Parameterwerte für Anweisungsausführungen gebunden, gibt **SQLRowCount** den Wert SQL_ERROR zurück, wenn eine Zeile mit Parameterwerten eine Fehlerbedingung bei der Anweisungsausführung generiert. Kein Wert wird durch das *RowCountPtr* -Argument der Funktion zurückgegeben.  
  
 Die Anwendung nutzt das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut, um die Anzahl der vor Auftreten des Fehlers verarbeiteten Parameter zu erfassen.  
  
 Darüber hinaus kann die Anwendung ein Array von Statuswerten verwenden, die mithilfe des SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattributs gebunden sind, um die Arrayoffsets der ungültigen Parameterzeilen zu erfassen. Die Anwendung kann das Statusarray durchsuchen, um die tatsächliche Anzahl verarbeiteter Zeilen zu bestimmen.  
  
 Wenn [!INCLUDE[tsql](../../includes/tsql-md.md)] eine INSERT-, UPDATE-, DELETE- oder MERGE-Anweisung mit einer OUTPUT-Klausel ausgeführt wird, gibt SQLRowCount die Anzahl der betroffenen Zeilen erst zurück, wenn alle Zeilen im Resultset, die von der OUTPUT-Klausel generiert wurden, verbraucht wurden. Um diese Zeilen zu verwenden, rufen Sie SQLFetch oder SQLFetchScroll auf. SQLResultCols gibt -1 zurück, bis alle Ergebniszeilen verbraucht wurden. Nachdem SQLFetch oder SQLFetchScroll SQL_NO_DATA zurückgegeben haben, muss die Anwendung SQLRowCount aufrufen, um die Anzahl der betroffenen Zeilen zu ermitteln, bevor SQLMoreResults aufgerufen wird, um zum nächsten Ergebnis zu wechseln.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLRowCount-Funktion](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
