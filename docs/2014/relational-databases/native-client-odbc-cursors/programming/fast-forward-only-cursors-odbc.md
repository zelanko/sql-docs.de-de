---
title: Schnelle Vorwärtscursor (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c6f72dec72efee850778a20315ee83adf7bd4b9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060267"
---
# <a name="fast-forward-only-cursors-odbc"></a>Schnelle Vorwärtscursor (ODBC)
  Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt leistungsoptimierungen für Vorwärtscursor und schreibgeschützte Cursor. Schnelle Vorwärtscursor werden vom Treiber und Server intern auf ganz ähnliche Weise implementiert wie Standardresultsets. Neben einer hohen Leistungsfähigkeit besitzen schnelle Vorwärtscursor auch folgende Eigenschaften:  
  
-   [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) wird nicht unterstützt. Die Resultsetspalten müssen an Programmvariablen gebunden sein.  
  
-   Wenn der Server auf das Ende des Cursors stößt, wird der Cursor automatisch geschlossen. Die Anwendung muss trotzdem aufrufen [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), aber der Treiber muss sich nicht in der schließen-Anforderung an den Server gesendet. Damit wird ein Roundtrip durch das Netzwerk zum Server eingespart.  
  
 Anwendungen fordern mit dem treiberspezifischen Anweisungsattribut SQL_SOPT_SS_CURSOR_OPTIONS schnelle Vorwärtscursor an. Wenn dieses auf SQL_CO_FFO festgelegt wird, werden schnelle Vorwärtscursor ohne die automatische Abrufoption aktiviert. Wenn es auf SQL_CO_FFO_AF festgelegt wird, wird auch die automatische Abrufoption aktiviert. Weitere Informationen zur automatischen Abrufoption finden Sie unter [Using Autofetch with ODBC Cursors](using-autofetch-with-odbc-cursors.md).  
  
 Schnelle Vorwärtscursor mit automatischer Abrufoption können eingesetzt werden, um kleine Resultsets mit nur einem Roundtrip zum Server abzurufen. In den folgenden Schritten *n* ist die Anzahl der zurückzugebenden Zeilen an:  
  
1.  Legen Sie SQL_SOPT_SS_CURSOR_OPTIONS auf SQL_CO_FFO_AF fest.  
  
2.  Legen Sie SQL_ATTR_ROW_ARRAY_SIZE auf *n* + 1.  
  
3.  Binden Sie die Ergebnisspalten an Arrays von *n* + 1 Elementen (sicher Wenn *n* + 1 Zeilen tatsächlich abgerufen werden).  
  
4.  Öffnen Sie den Cursors entweder mit **SQLExecDirect** oder **SQLExecute**.  
  
5.  Wenn der Rückgabestatus SQL_SUCCESS lautet, rufen Sie **SQLFreeStmt** oder **SQLCloseCursor** Schließen des Cursors. Alle Daten für die Zeilen sind in den gebundenen Programmvariablen enthalten.  
  
 Mit diesen Schritten die **SQLExecDirect** oder **SQLExecute** sendet eine offene Cursor-Anforderung mit der automatischen Abrufoption aktiviert. Auf diese einzelne Anforderung vom Client, führt der Server Folgendes aus:  
  
-   Er öffnet den Cursor.  
  
-   Er erstellt das Resultset und sendet die Zeilen an den Client.  
  
-   Weil die Rowsetgröße auf einen Wert festgelegt wurde, der um 1 größer als die Anzahl der Resultsetzeilen ist, erkennt der Server das Ende des Cursors und schließt den Cursor.  
  
## <a name="see-also"></a>Siehe auch  
 [Details zum Programmieren von Cursorn &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  