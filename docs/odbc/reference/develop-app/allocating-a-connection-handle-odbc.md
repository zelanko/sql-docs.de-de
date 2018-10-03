---
title: Zuordnen eines ODBC-Verbindungshandles | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83964bf1e76eef5c7c4ba4121b0c581e8d8a406b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782408"
---
# <a name="allocating-a-connection-handle-odbc"></a>Zuordnen eines ODBC-Verbindungshandles
Bevor die Anwendung an eine Datenquelle oder der Treiber eine Verbindung herstellen kann, muss sie wie folgt ein Verbindungshandle zuordnen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ SQLHDBC. Es ruft dann **SQLAllocHandle** und übergibt die Adresse dieser Variablen wird das Handle für die Umgebung, in dem die Verbindung, und die Option SQL_HANDLE_DBC auf zuordnen. Zum Beispiel:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zum Speichern von Informationen über die Anweisung und gibt das Verbindungshandle in der Variablen zurück.  
  
 Der Treiber-Manager wird nicht aufgerufen. **SQLAllocHandle** im Treiber auf dieser Zeit, da er nicht, welcher Treiber weiß für das aufrufen. Erfolgt eine Verzögerung, Aufrufen **SQLAllocHandle** im Treiber, bis die Anwendung eine Funktion für die Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie unter [Treiber-Manager-Rolle in der Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)weiter unten in diesem Abschnitt.  
  
 Es ist wichtig zu beachten, dass Zuordnen eines Verbindungshandles nicht identisch mit einen Treiber zu laden. Der Treiber wurde nicht geladen werden, bis eine Verbindungsfunktion aufgerufen wird. Somit sind nach dem Zuordnen eines Verbindungshandles und vor dem Herstellen einer Verbindung mit dem Treiber oder der Datenquelle, die die einzigen Funktionen, die die Anwendung kann mit dem Verbindungshandle Aufrufen **SQLSetConnectAttr**, **SQLGetConnectAttr**, oder **SQLGetInfo** mit der Option SQL_ODBC_VER. Aufruf anderer Funktionen mit dem Verbindungshandle, z. B. **SQLEndTran**, gibt der SQLSTATE 08003 (Verbindung nicht geöffnet). Ausführliche Informationen finden Sie unter [Anhang B: ODBC-Übergang-Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Weitere Informationen zu Verbindungshandles, finden Sie unter [Verbindungshandles](../../../odbc/reference/develop-app/connection-handles.md).
