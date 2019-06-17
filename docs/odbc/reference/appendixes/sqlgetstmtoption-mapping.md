---
title: SQLGetStmtOption-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2423d41b1e9c549b7202a68fb2a0e085e0a6e11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63297962"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption-Zuordnung
Wenn eine Anwendung ruft **SQLGetStmtOption** auf eine ODBC 3 *.x* Treiber, den sie den Aufruf von nicht unterstützt  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 wird wie folgt ausgegeben:  
  
-   Wenn *fOption* gibt an, eine ODBC-definierten Anweisungsoption, die eine Zeichenfolge, die Treiber-Manager ruft zurückgibt  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Wenn *fOption* gibt an, eine ODBC-definierten Anweisungsoption, die einen 32-Bit-Ganzzahl-Wert, der Treiber-Manager ruft zurückgibt.  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Wenn *fOption* gibt an, eine treiberdefinierten-Anweisungsoption, die Treiber-Manager-Aufrufe  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 In den vorherigen drei Fällen die *StatementHandle* Argument festgelegt ist, mit dem Wert im *Befehls beschäftigt*, *Attribut* Argument festgelegt ist, mit dem Wert im *fOption* , und die *ValuePtr* Argument festgelegt ist, auf den gleichen Wert wie *PvParam*.  
  
 Für ODBC definierte Zeichenfolge Verbindungsoptionen, des Treiber-Managers festlegt der *Pufferlänge* Argument im Aufruf von **SQLGetConnectAttr** auf die vordefinierte maximale Länge (SQL_MAX_OPTION_STRING_LENGTH); für eine Verbindungsoption keine Zeichenfolgen darstellen *Pufferlänge* auf 0 festgelegt ist.  
  
 Die SQL_GET_BOOKMARK Option-Anweisung ist veraltet in ODBC 3 *.x*. Eine ODBC 3 *.x* -Treiber zur Arbeit mit ODBC 2. *X* Anwendungen, die SQL_GET_BOOKMARK, muss er SQL_GET_BOOKMARK unterstützen. Eine ODBC 3 *.x* -Treiber zur Arbeit mit ODBC 2. *X* Anwendungen, es muss unterstützen SQL_USE_BOOKMARKS auf SQL_UB_ON festlegen und sollte verfügbar zu machen Lesezeichen mit fester Länge. Wenn eine ODBC 3 *.x* -Treiber unterstützt nur variabler Länge, die Lesezeichen nicht Lesezeichen mit fester Länge, sie muss SQLSTATE HYC00 zurückgeben (optionales Feature nicht implementiert) Wenn einer ODBC 2. *X* Anwendung versucht, SQL_UB_ON SQL_USE_BOOKMARKS fest.  
  
 Eine ODBC 3 *.x* -Treiber verwenden, der Treiber-Manager nicht mehr überprüft, ob *Option* zwischen SQL_STMT_OPT_MIN und SQL_STMT_OPT_MAX ist, oder ist größer als SQL_CONNECT_OPT_DRVR_START. Der Treiber muss dies zu überprüfen.
