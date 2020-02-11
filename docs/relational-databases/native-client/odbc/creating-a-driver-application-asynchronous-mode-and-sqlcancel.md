---
title: Asynchroner Modus und SQLCancel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e49e9cd9fdf9b4aeeaad4480a222914aaeb607e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73787779"
---
# <a name="creating-a-driver-application---asynchronous-mode-and-sqlcancel"></a>Erstellen einer Treiberanwendung – Asynchroner Modus und SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
  
 Gelegentlich ist ein Befehl längere Zeit ausstehend. Wenn die Anwendung den Befehl abbrechen muss, ohne auf eine Antwort zu warten, kann dies dazu führen, dass **SQLCancel** mit dem gleichen Anweisungs Handle wie der ausstehende Befehl aufgerufen wird. Dies ist der einzige Zeitpunkt, an dem **SQLCancel** verwendet werden sollte. Einige Programmierer verwenden **SQLCancel** , wenn Sie einen Teil des Resultsets verarbeitet haben und den Rest des Resultsets abbrechen möchten. [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) oder [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) sollte verwendet werden, um den Rest eines ausstehenden Resultsets, nicht **SQLCancel**, abzubrechen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
  
