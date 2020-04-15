---
title: SQLGetStmtOption Zuordnung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68819269d41407f2ce9dee172c889f7d7f286793
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300600"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption-Zuordnung
Wenn eine Anwendung **SQLGetStmtOption** auf einen ODBC *3.x-Treiber* aufruft, der ihn nicht unterstützt,  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 wird wie folgt führen:  
  
-   Wenn *fOption* eine ODBC-definierte Anweisungsoption angibt, die eine Zeichenfolge zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Wenn *fOption* eine ODBC-definierte Anweisungsoption angibt, die einen 32-Bit-Ganzzahlwert zurückgibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Wenn *fOption* eine treiberdefinierte Anweisungsoption angibt, ruft der Treiber-Manager  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 In den ersten drei Fällen wird das *StatementHandle-Argument* auf den Wert in *hstmt*festgelegt, das *Attributargument* wird auf den Wert in *fOption*festgelegt, und das *ValuePtr-Argument* wird auf den gleichen Wert wie *pvParam*festgelegt.  
  
 Bei ODBC-definierten Zeichenfolgenverbindungsoptionen legt der Treiber-Manager das *Argument BufferLength* im Aufruf von **SQLGetConnectAttr** auf die vordefinierte maximale Länge (SQL_MAX_OPTION_STRING_LENGTH) fest. für eine Nicht-Zeichenfolgenverbindungsoption ist *BufferLength* auf 0 festgelegt.  
  
 Die SQL_GET_BOOKMARK Anweisungsoption wurde in ODBC *3.x*veraltet. Damit ein ODBC *3.x-Treiber* mit ODBC *2.x-Anwendungen* arbeitet, die SQL_GET_BOOKMARK verwenden, muss er SQL_GET_BOOKMARK unterstützen. Damit ein ODBC *3.x-Treiber* mit ODBC *2.x-Anwendungen* arbeiten kann, muss er die Einstellung SQL_USE_BOOKMARKS auf SQL_UB_ON unterstützen und Lesezeichen mit fester Länge verfügbar machen. Wenn ein ODBC *3.x-Treiber* nur Lesezeichen mit variabler Länge und keine Lesezeichen mit fester Länge unterstützt, muss er SQLSTATE HYC00 (Optionale Funktion nicht implementiert) zurückgeben, wenn eine ODBC *2.x-Anwendung* versucht, SQL_USE_BOOKMARKS auf SQL_UB_ON festzulegen.  
  
 Bei einem ODBC *3.x-Treiber* überprüft der Treiber-Manager nicht mehr, ob sich *die Option* zwischen SQL_STMT_OPT_MIN und SQL_STMT_OPT_MAX befindet oder größer als SQL_CONNECT_OPT_DRVR_START ist. Der Fahrer muss dies überprüfen.
