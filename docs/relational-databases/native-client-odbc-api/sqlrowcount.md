---
title: SQLRowCount | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 13a1019d2781ea71f5f1017051f113a985f989be
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014154"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sind Arrays für Parameterwerte für Anweisungsausführungen gebunden, gibt **SQLRowCount** den Wert SQL_ERROR zurück, wenn eine Zeile mit Parameterwerten eine Fehlerbedingung bei der Anweisungsausführung generiert. Kein Wert wird durch das *RowCountPtr* -Argument der Funktion zurückgegeben.  
  
 Die Anwendung nutzt das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut, um die Anzahl der vor Auftreten des Fehlers verarbeiteten Parameter zu erfassen.  
  
 Darüber hinaus kann die Anwendung ein Array von Statuswerten verwenden, die mithilfe des SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattributs gebunden sind, um die Arrayoffsets der ungültigen Parameterzeilen zu erfassen. Die Anwendung kann das Statusarray durchsuchen, um die tatsächliche Anzahl verarbeiteter Zeilen zu bestimmen.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT-, Update-, DELETE- oder MERGE-Anweisung mit einer OUTPUT-Klausel ausgeführt wird, gibt die Anzahl der Zeilen betroffen sind, bis alle Zeilen in der von der OUTPUT-Klausel erzeugte Resultset verarbeitet wurden SQLRowCount nicht zurück. Zu verarbeiten rufen diesen Zeilen können Sie SQLFetch oder SQLFetchScroll. SQLResultCols gibt-1 zurück, bis alle Ergebniszeilen verwendet wurden. Nach dem SQLFetch oder SQLFetchScroll SQL_NO_DATA zurückgegeben wird, muss die Anwendung SQLRowCount zum Ermitteln der Anzahl der vor dem Aufrufen von SQLMoreResults auf das nächste Ergebnis verschoben betroffenen Zeilen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLRowCount-Funktion](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
