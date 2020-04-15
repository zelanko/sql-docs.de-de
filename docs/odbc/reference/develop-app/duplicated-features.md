---
title: Duplizierte Funktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 00f5529cfbfacebcad78a0a4433e84f34034694a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300480"
---
# <a name="duplicated-features"></a>Doppelte Funktionen
Die folgenden ODBC *2.x-Funktionen* wurden von ODBC *3.x-Funktionen* dupliziert. Daher sind die ODBC *2.x-Funktionen* in ODBC *3.x*veraltet. Die ODBC *3.x-Funktionen* werden als Ersatzfunktionen bezeichnet.  
  
 Wenn eine Anwendung eine veraltete ODBC *2.x-Funktion* verwendet und der zugrunde liegende Treiber ein ODBC *3.x-Treiber* ist, ordnet der Treiber-Manager den Funktionsaufruf der entsprechenden Ersatzfunktion zu. Die einzige Ausnahme von dieser Regel ist **SQLExtendedFetch**. (Siehe Fußnote am Ende der folgenden Tabelle.) Weitere Informationen zu diesen Zuordnungen finden Sie unter [Zuordnen veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
  
 Wenn eine Anwendung eine Ersatzfunktion verwendet und der zugrunde liegende Treiber ein ODBC *2.x-Treiber* ist, ordnet der Treiber-Manager den Funktionsaufruf der entsprechenden veralteten Funktion zu.  
  
|ODBC *2.x-Funktion*|ODBC *3.x-Funktion*|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**Sqlerror**|**SQLGetDiagRec**|  
|**SQLExtendedFetch**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**'SQLGetStmtAttr'**|  
|**SQLParamOptionen**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] Die Funktion **SQLExtendedFetch** ist duplizierte Funktionalität; **SQLFetchScroll** bietet die gleiche Funktionalität in ODBC *3.x*. Der Treiber-Manager wird **SQLExtendedFetch** jedoch nicht **SQLFetchScroll** zuordnen, wenn er mit einem ODBC *3.x-Treiber* ausgeht. Weitere Informationen finden Sie unter [Was der Treiber-Manager](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) in Anhang G: Treiberrichtlinien für die Abwärtskompatibilität tut. Der Treiber-Manager ordnet **SQLFetchScroll** **SQLExtendedFetch** zu, wenn er mit einem ODBC *2.x-Treiber* ausgeht.  
  
> [!NOTE]
>  Die Funktion **SQLBindParam** ist ein Sonderfall. **SQLBindParam** ist duplizierte Funktionalität. Dies ist keine ODBC *2.x-Funktion,* sondern eine Funktion, die in den Open Group- und ISO-Standards vorhanden ist. Die von dieser Funktion bereitgestellte Funktionalität wird vollständig durch die von **SQLBindParameter**subsumiert. Daher ordnet der Treiber-Manager einen Aufruf von **SQLBindParam** **SQLBindParameter** zu, wenn der zugrunde liegende Treiber ein ODBC *3.x-Treiber* ist. Wenn der zugrunde liegende Treiber jedoch ein ODBC *2.x-Treiber* ist, führt der Treiber-Manager diese Zuordnung nicht aus.
