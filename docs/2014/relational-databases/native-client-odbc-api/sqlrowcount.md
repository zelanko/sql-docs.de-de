---
title: SQLRowCount | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae4c2fa55f5975357d94eaecb2f92e9468fee98f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149880"
---
# <a name="sqlrowcount"></a>SQLRowCount
  Bei Arrays für Parameterwerte für anweisungsausführungen, gebunden sind `SQLRowCount` gibt SQL_ERROR zurück, wenn jede Zeile von Parameterwerten eine fehlerbedingung bei der anweisungsausführung generiert. Kein Wert wird durch das *RowCountPtr* -Argument der Funktion zurückgegeben.  
  
 Die Anwendung nutzt das SQL_ATTR_PARAMS_PROCESSED_PTR-Anweisungsattribut, um die Anzahl der vor Auftreten des Fehlers verarbeiteten Parameter zu erfassen.  
  
 Darüber hinaus kann die Anwendung ein Array von Statuswerten verwenden, die mithilfe des SQL_ATTR_PARAM_STATUS_PTR-Anweisungsattributs gebunden sind, um die Arrayoffsets der ungültigen Parameterzeilen zu erfassen. Die Anwendung kann das Statusarray durchsuchen, um die tatsächliche Anzahl verarbeiteter Zeilen zu bestimmen.  
  
 Wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT-, Update-, DELETE- oder MERGE-Anweisung mit einer OUTPUT-Klausel ausgeführt wird, SQLRowCount wird zurückgegeben, die Anzahl der Zeilen betroffen sind, bis alle Zeilen in der von der OUTPUT-Klausel erzeugte Resultset verarbeitet wurden. Zu verarbeiten rufen Sie auf diese Zeilen SQLFetch oder SQLFetchScroll. SQLResultCols gibt-1 zurück, bis alle Ergebniszeilen verarbeitet wurden. Nachdem SQLFetch oder SQLFetchScroll SQL_NO_DATA zurückgegeben wird, muss die Anwendung SQLRowCount zum Ermitteln der Anzahl der Zeilen, die vor dem Aufrufen von SQLMoreResults auf das nächste Ergebnis verschieben betroffen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLRowCount-Funktion](http://go.microsoft.com/fwlink/?LinkId=59367)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  