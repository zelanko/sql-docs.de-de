---
title: SQLSetScrollOptions Zuordnung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77050df283b10abd17ba62a48bd366d6c1b3f601
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300500"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions-Zuordnung
Wenn eine Anwendung **SQLSetScrollOptions** über einen ODBC *3.x-Treiber* aufruft und der Treiber **SQLSetScrollOptions**nicht unterstützt,  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 wird wie folgt führen:  
  
-   Ein Aufruf an  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     mit dem *InfoType-Argument,* das auf einen der Werte in der folgenden Tabelle festgelegt ist, abhängig vom Wert des *KeysetSize-Arguments* in **SQLSetScrollOptions**.  
  
    |*KeysetSize-Argument*|*InfoType-Argument*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Ein Wert größer als das *RowsetSize-Argument*|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Wenn der Wert des *KeysetSize-Arguments* in der obigen Tabelle nicht aufgeführt ist, gibt der Aufruf von **SQLSetScrollOptions** SQLSTATE S1107 (Zeilenwert a-range) zurück, und keiner der folgenden Schritte wird ausgeführt.  
  
     Der Treiber-Manager überprüft dann, ob das entsprechende Bit im **InfoValuePtr-Wert* festgelegt ist, der vom Aufruf von **SQLGetInfo**zurückgegeben wird, entsprechend dem Wert des *Concurrency-Arguments* in **SQLSetScrollOptions**.  
  
    |*Parallelitätsargument*|*InfoType-Einstellung*|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Wenn das *Concurrency-Argument* nicht einer der Werte in der obigen Tabelle ist, gibt der Aufruf von **SQLSetScrollOptions** SQLSTATE S1108 (Concurrency-Option außerhalb des gültigen Bereichs) zurück, und keiner der folgenden Schritte wird ausgeführt. Wenn das entsprechende Bit (wie in der obigen Tabelle angegeben) nicht in **InfoValuePtr* auf einen der Werte festgelegt ist, die dem *Concurrency-Argument* entsprechen, gibt der Aufruf von **SQLSetScrollOptions** SQLSTATE S1C00 zurück (Treiber nicht fähig) und keiner der folgenden Schritte wird ausgeführt.  
  
-   Ein Aufruf an  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     wenn * \*ValuePtr* auf einen der Werte in der folgenden Tabelle festgelegt ist, entsprechend dem Wert des *KeysetSize-Arguments* in **SQLSetScrollOptions**.  
  
    |*KeysetSize-Argument*|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Ein Wert größer als das *RowsetSize-Argument*|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Ein Aufruf an  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     mit * \*ValuePtr* auf das *Concurrency-Argument* in **SQLSetScrollOptions**festgelegt.  
  
-   Wenn das *KeysetSize-Argument* im Aufruf von **SQLSetScrollOptions** positiv ist,  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     mit * \*ValuePtr* auf das *KeysetSize-Argument* in **SQLSetScrollOptions**festgelegt.  
  
-   Ein Aufruf an  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     mit * \*ValuePtr* auf das *RowsetSize-Argument* in **SQLSetScrollOptions**festgelegt.  
  
    > [!NOTE]  
    >  Wenn der Treiber-Manager **SQLSetScrollOptions** für eine Anwendung zuordnet, die mit einem ODBC *3.x-Treiber* arbeitet, der **SQLSetScrollOptions**nicht unterstützt, legt der Treiber-Manager die SQL_ROWSET_SIZE-Anweisungsoption und nicht das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf das *RowsetSize-Argument* in **SQLSetScrollOption**fest. Daher kann **SQLSetScrollOptions** nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen Aufruf von **SQLFetch** oder **SQLFetchScroll**abgerufen werden. Sie kann nur verwendet werden, wenn mehrere Zeilen durch einen Aufruf von **SQLExtendedFetch**abgerufen werden.
