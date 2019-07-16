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
ms.openlocfilehash: 2973455ff4ee7e8dc51b2cd07a6423c9b1c36346
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073813"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption-Zuordnung
Wenn eine Anwendung ruft **SQLGetStmtOption** an die ODBC *3.x* Treiber, den sie den Aufruf von nicht unterstützt  
  
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
  
 Die SQL_GET_BOOKMARK Option-Anweisung ist veraltet in ODBC *3.x*. Für eine ODBC *3.x* -Treiber zur Arbeit mit ODBC *2.x* Anwendungen, die SQL_GET_BOOKMARK, muss er SQL_GET_BOOKMARK unterstützen. Für eine ODBC *3.x* -Treiber zur Arbeit mit ODBC *2.x* Anwendungen, es muss unterstützen SQL_USE_BOOKMARKS auf SQL_UB_ON festlegen und sollte verfügbar zu machen Lesezeichen mit fester Länge. Wenn eine ODBC *3.x* -Treiber unterstützt nur variabler Länge, die Lesezeichen nicht Lesezeichen mit fester Länge, sie muss SQLSTATE HYC00 zurückgeben (optionales Feature nicht implementiert) Wenn ODBC *2.x* Anwendung versucht, SQL_USE_BOOKMARKS auf SQL_UB_ON festgelegt.  
  
 Für eine ODBC *3.x* -Treiber verwenden, der Treiber-Manager nicht mehr überprüft, ob *Option* zwischen SQL_STMT_OPT_MIN und SQL_STMT_OPT_MAX ist, oder ist größer als SQL_CONNECT_OPT_DRVR_START. Der Treiber muss dies zu überprüfen.
