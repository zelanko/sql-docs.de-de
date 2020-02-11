---
title: Doppelte Features | Microsoft-Dokumentation
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
ms.openlocfilehash: ca73b5b9b41c99bd6db8e6181fa3582cae47c1d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046904"
---
# <a name="duplicated-features"></a>Doppelte Funktionen
Die folgenden ODBC *2. x* -Funktionen wurden von ODBC *3. x* -Funktionen dupliziert. Folglich sind die ODBC *2. x* -Funktionen in ODBC *3. x*veraltet. Die ODBC *3. x* -Funktionen werden als Ersatz Funktionen bezeichnet.  
  
 Wenn eine Anwendung eine veraltete ODBC *2. x* -Funktion verwendet und der zugrunde liegende Treiber ein ODBC *3. x* -Treiber ist, ordnet der Treiber-Manager den Funktions Aufrufder entsprechenden Ersetzungs Funktion zu. Die einzige Ausnahme von dieser Regel ist **sqlextendecodfetch**. (Weitere Informationen finden Sie in der Fußnote am Ende der folgenden Tabelle.) Weitere Informationen zu diesen Zuordnungen finden Sie unter [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Driver Guidelines for abwärts Compatibility.  
  
 Wenn eine Anwendung eine Ersatzfunktion verwendet und der zugrunde liegende Treiber ein ODBC *2. x* -Treiber ist, ordnet der Treiber-Manager den Funktionsaufrufe der entsprechenden veralteten Funktion zu.  
  
|ODBC *2. x* -Funktion|ODBC *3. x* -Funktion|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**Sqlextendebug**[1]|**SQLFetchScroll**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**'SQLGetStmtAttr'**|  
|**SQLParamOptions**|**SQLSetStmtAttr**, **SQLGetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**|**SQLBindParameter**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLtransact**|**SQLEndTran**|  
  
 [1] die **SQLExtendedFetch** -Funktion ist duplizierte Funktionen. **SQLFetchScroll** bietet die gleiche Funktionalität in ODBC *3. x*. Der Treiber-Manager ordnet **sqlextendecodfetch** jedoch nicht zu **SQLFetchScroll** zu, wenn ein ODBC *3. x* -Treiber verwendet wird. Weitere Informationen finden Sie unter [What the Driver Manager](../../../odbc/reference/appendixes/what-the-driver-manager-does.md) in Anhang G: Driver Guidelines for abwärts Compatibility. Der Treiber-Manager ordnet **SQLFetchScroll** zu **sqlextendecodfetch** zu, wenn ein ODBC *2. x* -Treiber durchlaufen wird.  
  
> [!NOTE]
>  Die **SQLBindParam** -Funktion ist ein Sonderfall. **SQLBindParam** ist eine duplizierte Funktionalität. Dabei handelt es sich nicht um eine ODBC *2. x* -Funktion, sondern um eine Funktion, die in den Open Group-und ISO-Standards vorhanden ist. Die von dieser Funktion bereitgestellte Funktionalität wird von **SQLBindParameter**vollständig unterstützt. Folglich ordnet der Treiber-Manager **SQLBindParam** einen **SQLBindParameter** -Befehl zu, wenn es sich bei dem zugrunde liegenden Treiber um einen ODBC *3. x* -Treiber handelt. Wenn der zugrunde liegende Treiber jedoch ein ODBC *2. x* -Treiber ist, führt der Treiber-Manager diese Zuordnung nicht durch.
