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
ms.openlocfilehash: 4ff2a744f68cf6152330179eb8dcab1f33911914
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046605"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Wenn Arrays von Parameterwerten für die Ausführung der Anweisung gebunden `SQLRowCount` werden, gibt SQL_ERROR zurück, wenn eine Zeile mit Parameterwerten in der Anweisungs Ausführung eine Fehlerbedingung generiert. Kein Wert wird durch das *RowCountPtr* -Argument der Funktion zurückgegeben.  
  
 Die Anwendung nutzt das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut, um die Anzahl der vor Auftreten des Fehlers verarbeiteten Parameter zu erfassen.  
  
 Darüber hinaus kann die Anwendung ein Array von Statuswerten verwenden, die mithilfe des SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattributs gebunden sind, um die Arrayoffsets der ungültigen Parameterzeilen zu erfassen. Die Anwendung kann das Statusarray durchsuchen, um die tatsächliche Anzahl verarbeiteter Zeilen zu bestimmen.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT-, Update-, DELETE-oder MERGE-Anweisung mit einer OUTPUT-Klausel ausgeführt wird, gibt SQLRowCount nicht die Anzahl der betroffenen Zeilen zurück, bis alle Zeilen im Resultset, das von der OUTPUT-Klausel generiert wurde, genutzt wurden. Um diese Zeilen zu sverarbeiten, rufen Sie SQLFetch oder SQLFetchScroll auf. SQLResultCols gibt-1 zurück, bis alle Ergebniszeilen verarbeitet wurden. Nachdem SQLFetch oder SQLFetchScroll SQL_NO_DATA zurückgegeben hat, muss die Anwendung SQLRowCount aufrufen, um die Anzahl der betroffenen Zeilen zu bestimmen, bevor SQLMoreResults aufgerufen wird, um zum nächsten Ergebnis zu gelangen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLRowCount-Funktion](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
