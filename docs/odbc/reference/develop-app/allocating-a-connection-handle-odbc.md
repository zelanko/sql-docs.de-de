---
description: Zuordnen eines ODBC-Verbindungshandles
title: Zuordnen eines Verbindungs Handles (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6c17003ed3746f2953eb167f2dc3d944659e352
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456436"
---
# <a name="allocating-a-connection-handle-odbc"></a>Zuordnen eines ODBC-Verbindungshandles
Bevor die Anwendung eine Verbindung mit einer Datenquelle oder einem Treiber herstellen kann, muss Sie wie folgt ein Verbindungs Handle zuordnen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ SQLHDBC. Anschließend wird **SQLAllocHandle** aufgerufen und die Adresse dieser Variablen, das Handle der Umgebung, in der die Verbindung zugeordnet werden soll, und die SQL_HANDLE_DBC Option übergibt. Beispiel:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Der Treiber-Manager ordnet eine-Struktur zu, in der Informationen über die-Anweisung gespeichert werden, und gibt das Verbindungs Handle in der Variablen zurück.  
  
 Der Treiber-Manager ruft zu diesem Zeitpunkt nicht " **sqlzuweisung** " im Treiber auf, weil er nicht weiß, welcher Treiber aufgerufen werden soll. Der Aufruf von **sqlverbinchandle** im Treiber wird verzögert, bis die Anwendung eine Funktion zum Herstellen einer Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie unter [Treiber-Manager-Rolle im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)weiter unten in diesem Abschnitt.  
  
 Beachten Sie unbedingt, dass die Zuordnung eines Verbindungs Handles nicht mit dem Laden eines Treibers identisch ist. Der Treiber wird erst geladen, wenn eine Verbindungsfunktion aufgerufen wird. Folglich sind nach dem Zuordnen eines Verbindungs Handles und vor dem Herstellen einer Verbindung mit dem Treiber oder der Datenquelle die einzigen Funktionen, die die Anwendung mit dem Verbindungs Handle aufrufen kann, **SQLSetConnectAttr**, **SQLGetConnectAttr**oder **SQLGetInfo** mit der Option SQL_ODBC_VER. Wenn Sie andere Funktionen mit dem Verbindungs Handle aufrufen, z. b. **SQLEndTran**, wird SQLSTATE 08003 (Verbindung nicht geöffnet) zurückgegeben. Ausführliche Informationen finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen zu Verbindungs Handles finden Sie unter [Verbindungs Handles](../../../odbc/reference/develop-app/connection-handles.md).
