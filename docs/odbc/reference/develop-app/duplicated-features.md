---
title: Funktionen dupliziert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- duplicated functions [ODBC]
- compatibility [ODBC], duplicated functions
- ODBC drivers [ODBC], backward compatibility
- functions [ODBC], duplicated functions
- backward compatibility [ODBC], duplicated functions
ms.assetid: 641b16bc-f791-46d8-b093-31736473fe3d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84752b7e23c5394757764bf5ade57cb54004b01a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62943146"
---
# <a name="duplicated-features"></a>Doppelte Funktionen
Die folgenden ODBC-2. *x* Funktionen wurden von ODBC 3. verdoppelt. *X* Funktionen. Als Ergebnis der ODBC-2. *x* Funktionen sind veraltet, in ODBC 3. *X*. Der ODBC-3. *x* Funktionen werden als Ersatzfunktionen bezeichnet.  
  
 Wenn eine Anwendung eine als veraltet markierte ODBC 2. verwendet. *x* -Funktion und der zugrunde liegenden Treiber ist ein ODBC-3. *X* Treiber, der Treiber-Manager ordnet den Funktionsaufruf mit der entsprechenden Ersatz-Funktion. Die einzige Ausnahme dieser Regel wird **SQLExtendedFetch**. (Siehe die Fußnote am Ende der in der folgenden Tabelle.) Weitere Informationen zu diesen Zuordnungen finden Sie unter [veraltete Zuordnungsfunktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
 Wenn eine Anwendung ein Ersatz-Funktion und der zugrunde liegenden Treiber verwendet, ist ein ODBC-2. *x* -Treiber verwenden, wird der Treiber-Manager den Funktionsaufruf an die entsprechende als veraltet markierte Funktion zugeordnet.  
  
|ODBC-2. *x* Funktion|ODBC 3. *x* Funktion|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] der Funktion **SQLExtendedFetch** sind doppelte Funktionen; **SQLFetchScroll** bietet dieselbe Funktionalität in ODBC 3. *X*. Der Treiber-Manager ordnet jedoch nicht **SQLExtendedFetch** zu **SQLFetchScroll** Wenn für eine ODBC 3. *X* Treiber. Weitere Informationen finden Sie unter [was der Treiber-Manager macht](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten. Der Treiber-Manager zugeordnet **SQLFetchScroll** zu **SQLExtendedFetch** Wenn mit einer ODBC 2. *X* Treiber.  
  
> [!NOTE]
>  Die Funktion **SQLBindParam** ist ein besonderer Fall. **SQLBindParam** sind doppelte Funktionen. Dies ist keiner ODBC 2. *.x* -Funktion, aber eine Funktion, die in den Open Group und ISO-Standards vorhanden ist. Die Funktionalität, die von dieser Funktion wird vollständig von der klassifiziert **SQLBindParameter**. Daher ordnet der Treiber-Manager einen Aufruf von **SQLBindParam** zu **SQLBindParameter** beim zugrunde liegenden Treiber ist ein ODBC 3. *X* Treiber. Wenn der zugrunde liegenden Treiber ist jedoch einer ODBC 2. *.x* -Treiber verwenden, der Treiber-Manager führt keine diese Zuordnung.
