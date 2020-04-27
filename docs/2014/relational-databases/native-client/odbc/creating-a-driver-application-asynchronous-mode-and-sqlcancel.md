---
title: Asynchroner Modus und SQLCancel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a4ec4e5d7575fdf5d915c8209999e1285fa79aa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63144321"
---
# <a name="asynchronous-mode-and-sqlcancel"></a>Asynchroner Modus und SQLCancel
  Einige ODBC-Funktionen können synchron oder asynchron verwendet werden. Die Anwendung kann asynchrone Vorgänge für ein Anweisungshandle oder ein Verbindungshandle aktivieren. Wenn die Option für ein Verbindungshandle eingerichtet ist, wirkt sie sich auf alle Anweisungshandles auf dem Verbindungshandle aus. Die Anwendung verwendet die folgenden Anweisungen, um asynchrone Vorgänge zu aktivieren oder zu deaktivieren:  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Wenn eine Anwendung eine ODBC-Funktion im synchronen Modus aufruft, gibt der Treiber die Steuerung nicht an die Anwendung zurück, bis sie darüber benachrichtigt wird, dass der Server den Befehl abgeschlossen hat.  
  
 Beim asynchronen Betrieb gibt der Treiber unmittelbar die Steuerung an die Anwendung zurück, noch bevor der Befehl an den Server gesendet wird. Der Treiber setzt den Rückgabecode auf SQL_STILL_EXECUTING. Die Anwendung kann dann andere Arbeiten ausführen.  
  
 Wenn die Anwendung überprüft, ob der Befehl ausgeführt wurde, führt sie den gleichen Funktionsaufruf mit den gleichen Parametern für den Treiber durch. Wenn der Treiber noch keine Antwort vom Server erhalten hat, gibt er erneut SQL_STILL_EXECUTING zurück. Die Anwendung muss den Befehl regelmäßig testen, bis der Rückgabecode einen anderen Wert als SQL_STILL_EXECUTING annimmt. Wenn die Anwendung einen anderen Rückgabecode erhält (auch SQL_ERROR), kann sie ermitteln, ob der Befehl abgeschlossen wurde.  
  
 Gelegentlich ist ein Befehl längere Zeit ausstehend. Wenn die Anwendung den Befehl abbrechen muss, ohne auf eine Antwort zu warten, kann dies dazu führen, dass **SQLCancel** mit dem gleichen Anweisungs Handle wie der ausstehende Befehl aufgerufen wird. Dies ist der einzige Zeitpunkt, an dem **SQLCancel** verwendet werden sollte. Einige Programmierer verwenden **SQLCancel** , wenn Sie einen Teil des Resultsets verarbeitet haben und den Rest des Resultsets abbrechen möchten. [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) oder [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) sollte verwendet werden, um den Rest eines ausstehenden Resultsets, nicht **SQLCancel**, abzubrechen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](creating-a-driver-application.md)  
  
  
