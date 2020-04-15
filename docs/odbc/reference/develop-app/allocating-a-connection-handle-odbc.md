---
title: Zuweisen eines Verbindungsgriffs ODBC | Microsoft Docs
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
ms.openlocfilehash: 12e9f65ee81612e269c1f86ebabd049588443cb8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288520"
---
# <a name="allocating-a-connection-handle-odbc"></a>Zuordnen eines ODBC-Verbindungshandles
Bevor die Anwendung eine Verbindung mit einer Datenquelle oder einem Treiber herstellen kann, muss sie wie folgt ein Verbindungshandle zuweisen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ SQLHDBC. Anschließend wird **SQLAllocHandle** aufund die Adresse dieser Variablen, das Handle der Umgebung, in der die Verbindung zugewiesen werden soll, und die Option SQL_HANDLE_DBC. Beispiel:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zu, in der Informationen über die Anweisung gespeichert werden sollen, und gibt das Verbindungshandle in der Variablen zurück.  
  
 Der Treiber-Manager ruft **SQLAllocHandle** derzeit nicht im Treiber auf, da er nicht weiß, welchen Treiber er aufrufen soll. Es verzögert den Aufruf von **SQLAllocHandle** im Treiber, bis die Anwendung eine Funktion zum Herstellen einer Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie weiter unten in diesem Abschnitt unter [Die Rolle des Treiber-Managers im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Es ist wichtig zu beachten, dass das Zuweisen eines Verbindungshandles nicht mit dem Laden eines Treibers identisch ist. Der Treiber wird erst geladen, wenn eine Verbindungsfunktion aufgerufen wird. Nach dem Zuweisen eines Verbindungshandles und vor dem Herstellen einer Verbindung mit dem Treiber oder der Datenquelle sind die einzigen Funktionen, die die Anwendung mit dem Verbindungshandle aufrufen kann, **SQLSetConnectAttr**, **SQLGetConnectAttr**oder **SQLGetInfo** mit der Option SQL_ODBC_VER. Beim Aufrufen anderer Funktionen mit dem Verbindungshandle, z. B. **SQLEndTran**, wird SQLSTATE 08003 zurückgegeben (Verbindung nicht geöffnet). Ausführliche Informationen finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen zu Verbindungshandles finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md).
