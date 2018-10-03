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
manager: craigg
ms.openlocfilehash: 5520554b509b0c25d62e4a191e16ad3524a02652
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47651441"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions-Zuordnung
Wenn eine Anwendung ruft **SQLSetScrollOptions** über einen ODBC 3.*.x* Treiber und der Treiber unterstützt keine **SQLSetScrollOptions**, den Aufruf von  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 wird wie folgt ausgegeben:  
  
-   Ein Aufruf von  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     mit der *Informationsart* Argument festgelegt wird, um einen der Werte in der folgenden Tabelle, abhängig vom Wert der *KeysetSize* -Argument in **SQLSetScrollOptions**.  
  
    |*KeysetSize-argument*|*Informationsart-argument*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Ein Wert größer als die *RowsetSize* Argument|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Wenn der Wert des der *KeysetSize* Argument ist nicht aufgeführt, in der obigen Tabelle, die den Aufruf von **SQLSetScrollOptions** SQLSTATE S1107 zurückgibt (Zeilenwert außerhalb des gültigen Bereichs) und keine der folgenden Schritte sind ausgeführt.  
  
     Der Treiber-Manager klicken Sie dann wird überprüft, ob das entsprechende Bit, in festgelegt ist der **InfoValuePtr* durch den Aufruf zurückgegebene Wert **SQLGetInfo**, nach dem Wert des der *Parallelität* -Argument in **SQLSetScrollOptions**.  
  
    |*Parallelität* Argument|*Informationsart* Einstellung|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Wenn die *Parallelität* -Argument ist keiner der Werte in der obigen Tabelle, die den Aufruf von **SQLSetScrollOptions** SQLSTATE S1108 zurückgibt (Parallelitätsoption außerhalb des gültigen Bereichs) und keine der folgenden Schritte sind ausgeführt. Wenn das entsprechende Bit (wie in der obigen Tabelle angegeben) nicht, in festgelegt ist **InfoValuePtr* auf einen der Werte für die *Parallelität* Argument, das den Aufruf von  **SQLSetScrollOptions** SQLSTATE S1C00 zurückgibt (nicht-Treiber) und für keine der folgenden Schritte ausgeführt werden.  
  
-   Ein Aufruf von  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     mit  *\*ValuePtr* legen Sie auf einen der Werte in der folgenden Tabelle entsprechend dem Wert des der *KeysetSize* -Argument in **SQLSetScrollOptions**.  
  
    |*KeysetSize* Argument|*\*ValuePtr*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Ein Wert größer als die *RowsetSize* Argument|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Ein Aufruf von  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     mit  *\*ValuePtr* legen Sie auf die *Parallelität* -Argument in **SQLSetScrollOptions**.  
  
-   Wenn die *KeysetSize* Argument im Aufruf von **SQLSetScrollOptions** positiv ist, einen Aufruf von  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     mit  *\*ValuePtr* legen Sie auf die *KeysetSize* -Argument in **SQLSetScrollOptions**.  
  
-   Ein Aufruf von  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     mit  *\*ValuePtr* legen Sie auf die *RowsetSize* -Argument in **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Wenn der Treiber-Manager zugeordnet **SQLSetScrollOptions** für eine Anwendung, die Arbeit mit einer ODBC 3.*.x* Treiber, der nicht unterstützt. **SQLSetScrollOptions**, den Treiber Legt Manager die SQL_ROWSET_SIZE setzen Option-Anweisung, nicht das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut, zu der *RowsetSize* -Argument in **SQLSetScrollOption**. Daher **SQLSetScrollOptions** kann nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen Aufruf zum Abrufen von **SQLFetch** oder **SQLFetchScroll**. Kann verwendet werden, nur dann, wenn das Abrufen von mehreren durch einen Aufruf von Zeilen **SQLExtendedFetch**.
