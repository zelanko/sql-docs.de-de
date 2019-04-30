---
title: Blocks und bildlauffähigen Cursor-Kompatibilität für ODBC 3.x | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0bc45169a3c5eee2e23f581a66d5232c22e89b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199260"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen
Das Vorhandensein sowohl **SQLFetchScroll** und **SQLExtendedFetch** darstellt, die erste Klartext geteilt werden, in ODBC zwischen der Schnittstelle API (Application Programming), die den Satz von Funktionen ist die Anwendungsaufrufe und der Service Provider-Schnittstelle (SPI), wird der Satz von Funktionen der Treiber implementiert. Diese Auftrennung ist erforderlich, um die Anforderung in ODBC 3. auszugleichen. *x*, verwendet **SQLFetchScroll**, um den Standards entsprechen, und klicken Sie mit ODBC-2 kompatibel sein. *X*, verwendet **SQLExtendedFetch**.  
  
 Die ODBC 3.*.x* -API, die ist der Satz von Funktionen, die Anwendung ruft, umfasst **SQLFetchScroll** und zugehörigen Anweisungsattribute. Die ODBC 3.*.x* SPI, den Satz von Funktionen der Treiber implementiert wird, enthält **SQLFetchScroll**, **SQLExtendedFetch**, und zugehörigen Anweisungsattribute. Da es sich bei ODBC diese Auftrennung zwischen der API und der SPI formal nicht erzwingt, ist es möglich, ODBC 3.*.x* aufrufen, **SQLExtendedFetch** und zugehörigen Anweisungsattribute. Allerdings besteht kein Grund für die ODBC 3.*.x* Anwendungen zu diesem Zweck. Weitere Informationen zu APIs und SPIs, finden Sie unter der Einführung zur [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Informationen zur Verwendung der ODBC-3. *x* -Treiber-Manager zugeordnet ist, Aufrufe an ODBC 2. *X* und ODBC 3. *X* Treiber und welche Funktionen und die Anweisung eine ODBC-3-Attribute. *X* Treiber sollte für Blocks und bildlauffähigen Cursor zu implementieren, finden Sie unter [was der Treiber führt](../../../odbc/reference/appendixes/what-the-driver-does.md) in Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
 Die folgende Tabelle fasst zusammen, welche Funktionen und Anweisungsattribute eine ODBC-3. *x* sollte die Anwendung mit Blocks und bildlauffähigen Cursor verwenden. Außerdem werden Änderungen zwischen ODBC 2. aufgeführt. *x* und ODBC 3. *X* in diesem Bereich, ODBC 3. *X* Anwendungen sollte bekannt sein, mit ODBC-2 kompatibel. *X* Treiber.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Verweist auf das Lesezeichen mit **SQLFetchScroll**.<br /><br /> Wenn eine Anwendung dies in einer ODBC 2. festlegt. *x* -Treiber verwenden, muss dies auf ein Lesezeichen fester Länge zeigen.|  
|SQL_ATTR_ROW_STATUS_PTR|Verweist auf die zeilenstatusarray ausgefüllt, indem **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, und **SQLSetPos**.<br /><br /> Wenn eine Anwendung dies in einer ODBC 2. festlegt. *x* Treiber und Aufrufe **SQLBulkOperation** mit einer *Vorgang* von SQL_ADD vor dem Aufruf **SQLFetchScroll**,  **SQLFetch**, oder **SQLExtendedFetch**, SQLSTATE HY011 (Attribut kann nicht jetzt festgelegt werden) wird zurückgegeben.<br /><br /> Wenn eine Anwendung ruft **SQLFetch** in einer ODBC 2. *X* Treiber **SQLFetch** zugeordnet **SQLExtendedFetch** und aus diesem Grund gibt Werte in diesem Array zurück.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Verweist auf den Puffer, in dem **SQLFetch** und **SQLFetchScroll** geben die Anzahl der abgerufenen Zeilen zurück.<br /><br /> Wenn eine Anwendung ruft **SQLFetch** in einer ODBC 2. *X* Treiber **SQLFetch** zugeordnet **SQLExtendedFetch** und aus diesem Grund gibt einen Wert zurück, in diesem Puffer.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die Größe des Rowsets fest.<br /><br /> Wenn eine Anwendung ruft **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD in einer ODBC 2. *X* SQL_ROWSET_SIZE setzen-Treiber wird für den Aufruf nicht SQL_ATTR_ROW_ARRAY_SIZE, verwendet werden, weil der Aufruf zugeordnet ist **SQLSetPos** mit einer *Vorgang* von SQL_ADD, die verwendet SQL_ROWSET_SIZE SETZEN.<br /><br /> Aufrufen von **SQLSetPos** mit einer *Vorgang* von SQL_ADD oder **SQLExtendedFetch** in einer ODBC-2. *X* -Treiber verwendet SQL_ROWSET_SIZE setzen.<br /><br /> Aufrufen von **SQLFetch** oder **SQLFetchScroll** in einer ODBC-2. *X* verwendet der Treiber SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Führt Einfüge-und Lesezeichen. Wenn **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD in einer ODBC 2. aufgerufen wird. *X* Treiber zugeordnet, um **SQLSetPos** mit einer *Vorgang* von SQL_ADD. Im folgenden finden Details zur Implementierung:<br /><br /> – Wenn Sie mit einer ODBC 2. arbeiten zu können. *x* -Treiber verwenden, muss eine Anwendung nur die zugeordneten implizit zugewiesene ARD verwenden die *StatementHandle*; kann nicht einem anderen ARD zum Hinzufügen von Zeilen zugeordnet werden, da expliziten Deskriptors Vorgänge sind in einer ODBC 2. unterstützt nicht. *x* Treiber. Eine Anwendung verwenden, muss **SQLBindCol** so binden Sie nicht an die ARD **SQLSetDescField** oder **SQLSetDescRec**.<br />– Wenn Sie eine ODBC 3. aufrufen. *x* -Treiber verwenden, es kann eine Anwendung aufrufen **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD vor dem Aufruf **SQLFetch** oder **SQLFetchScroll**. Beim Aufrufen von einer ODBC 2. *x* -Treiber verwenden, es muss eine Anwendung aufrufen **SQLFetchScroll** vor dem Aufruf **SQLBulkOperations** mit einem Vorgang des SQL_ADD.|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im folgenden finden Details zur Implementierung:<br /><br /> – Wenn eine Anwendung ruft **SQLFetch** in einer ODBC 2. *X* Treiber zugeordnet, um **SQLExtendedFetch**.<br />– Wenn eine Anwendung ruft **SQLFetch** in einer ODBC 3. *X* -Treiber, die die Anzahl der Zeilen, die mit dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung angegeben wird.|  
|**SQLFetchScroll**|Gibt den angegebene Rowset zurück. Im folgenden finden Details zur Implementierung:<br /><br /> – Wenn eine Anwendung ruft **SQLFetchScroll** in einer ODBC 2. *X* -Treiber SQLSTATE 01 s 01 zurückgegeben (Fehler in Zeile) vor jedem Fehler, der auf eine einzelne Zeile angewendet wird. Es liegt nur daran, dass die ODBC 3.*.x* -Treiber-Manager zugeordnet wird, diese Option, um **SQLExtendedFetch** und **SQLExtendedFetch** SQLSTATE zurückgegeben. Wenn eine Anwendung ruft **SQLFetchScroll** in einer ODBC 3. *X* -Treiber verwenden, es gibt nie zurück SQLSTATE 01 s 01 (Fehler in Zeile).<br />– Wenn eine Anwendung ruft **SQLFetchScroll** in einer ODBC 2. *X* Treiber mit *FetchOrientation* festgelegt sql_fetch_bookmark auf, die *FetchOffset* Argument muss auf 0 festgelegt werden. SQLSTATE HYC00 (optionales Feature nicht implementiert) wird zurückgegeben, wenn die Offset-basierte Lesezeichen Abrufen mit einer ODBC 2. ausgeführt wird. *x* Treiber.|  
  
> [!NOTE]  
>  ODBC 3. *x* Anwendungen sollten nicht verwenden, **SQLExtendedFetch** oder das Anweisungsattribut SQL_ROWSET_SIZE setzen. Sie sollten stattdessen **SQLFetchScroll** und dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung. ODBC 3. *x* Anwendungen sollten nicht verwenden, **SQLSetPos** mit einer *Vorgang* von SQL_ADD sollten aber **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD.
