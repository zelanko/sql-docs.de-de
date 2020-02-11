---
title: SQLSetScrollOptions-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 06b6b0f982b5c8d864e5024c8544f1f8e9af75ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091697"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions-Zuordnung
Wenn eine Anwendung **SQLSetScrollOptions** über einen ODBC *3. x* -Treiber aufruft und der Treiber **SQLSetScrollOptions**nicht unterstützt, wird der Aufruf von  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 führt zu folgenden Ergebnissen:  
  
-   Ein-Rückruf  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     Wenn das *InfoType* -Argument auf einen der Werte in der folgenden Tabelle festgelegt ist, hängt vom Wert des *keysetsize* -Arguments in **SQLSetScrollOptions**ab.  
  
    |*Keysetsize-Argument*|*Infotype-Argument*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Ein Wert, der größer als das *rowsetsize* -Argument ist.|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Wenn der Wert des Arguments *keysetsize* nicht in der vorangehenden Tabelle aufgeführt ist, gibt der **SQLSetScrollOptions** -Befehl SQLSTATE S1107 (Zeilen Wert außerhalb des gültigen Bereichs) zurück, und es werden keine der folgenden Schritte ausgeführt.  
  
     Der Treiber-Manager überprüft dann gemäß dem *Wert des Parallelitäts Arguments in* **SQLSetScrollOptions**, ob das entsprechende Bit im **infovalueptr* -Wert festgelegt ist, der durch den **SQLGetInfo**-Befehl zurückgegeben wird.  
  
    |*Parallelitäts Argument*|*InfoType* -Einstellung|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Wenn das *Parallelitäts Argument nicht* einer der Werte in der obigen Tabelle ist, gibt der **SQLSetScrollOptions** -Befehl SQLSTATE S1108 (Parallelitäts Option außerhalb des gültigen Bereichs) zurück, und es werden keine der folgenden Schritte ausgeführt. Wenn das entsprechende Bit (wie in der obigen Tabelle angegeben) nicht in **infovalueptr* auf einen der Werte festgelegt wird *, die dem Parallelitäts Argument entsprechen* , gibt der **SQLSetScrollOptions** -Befehl SQLSTATE S1C00 (Treiber nicht fähig) zurück, und es werden keine der folgenden Schritte ausgeführt.  
  
-   Ein-Rückruf  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     Wenn * \*ValuePtr* auf einen der Werte in der folgenden Tabelle festgelegt ist, gemäß dem Wert des *keysetsize* -Arguments in **SQLSetScrollOptions**.  
  
    |*Keysetsize* -Argument|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Ein Wert, der größer als das *rowsetsize* -Argument ist.|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Ein-Rückruf  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     Wenn * \*ValuePtr* *auf das* Parallelitäts Argument in **SQLSetScrollOptions**festgelegt ist.  
  
-   Wenn das *keysetsize* -Argument im Aufrufen von **SQLSetScrollOptions** positiv ist, wird ein-Aufrufen von  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     Wenn * \*ValuePtr* auf das *keysetsize* -Argument in **SQLSetScrollOptions**festgelegt ist.  
  
-   Ein-Rückruf  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     Wenn * \*ValuePtr* auf das *rowsetsize* -Argument in **SQLSetScrollOptions**festgelegt ist.  
  
    > [!NOTE]  
    >  Wenn der Treiber-Manager **SQLSetScrollOptions** für eine Anwendung zuordnet, die mit einem ODBC *3. x* -Treiber arbeitet, der **SQLSetScrollOptions**nicht unterstützt, legt der Treiber-Manager die SQL_ROWSET_SIZE Anweisungs Option, nicht das SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut, auf das *rowsetsize* -Argument in **sqlsetscrolloption**fest. Daher kann **SQLSetScrollOptions** nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen-Befehl von **SQLFetch** oder **SQLFetchScroll**abgerufen werden. Diese Option kann nur verwendet werden, wenn mehrere Zeilen durch einen **sqlextendebug**-Befehl abgerufen werden.
