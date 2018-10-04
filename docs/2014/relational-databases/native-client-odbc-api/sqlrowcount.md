---
title: SQLRowCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9858619250b5f71e973e4af8eb92868f094e2193
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48165030"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Arrays für Parameterwerte für anweisungsausführungen gebunden, gibt `SQLRowCount` gibt SQL_ERROR zurück, wenn eine Zeile mit Parameterwerten eine fehlerbedingung bei der anweisungsausführung generiert. Kein Wert wird durch das *RowCountPtr* -Argument der Funktion zurückgegeben.  
  
 Die Anwendung nutzt das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut, um die Anzahl der vor Auftreten des Fehlers verarbeiteten Parameter zu erfassen.  
  
 Darüber hinaus kann die Anwendung ein Array von Statuswerten verwenden, die mithilfe des SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattributs gebunden sind, um die Arrayoffsets der ungültigen Parameterzeilen zu erfassen. Die Anwendung kann das Statusarray durchsuchen, um die tatsächliche Anzahl verarbeiteter Zeilen zu bestimmen.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT-, Update-, DELETE- oder MERGE-Anweisung mit einer OUTPUT-Klausel ausgeführt wird, gibt die Anzahl der Zeilen betroffen sind, bis alle Zeilen in der von der OUTPUT-Klausel erzeugte Resultset verarbeitet wurden SQLRowCount nicht zurück. Zu verarbeiten rufen diesen Zeilen können Sie SQLFetch oder SQLFetchScroll. SQLResultCols gibt-1 zurück, bis alle Ergebniszeilen verwendet wurden. Nach dem SQLFetch oder SQLFetchScroll SQL_NO_DATA zurückgegeben wird, muss die Anwendung SQLRowCount zum Ermitteln der Anzahl der vor dem Aufrufen von SQLMoreResults auf das nächste Ergebnis verschoben betroffenen Zeilen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLRowCount-Funktion](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
