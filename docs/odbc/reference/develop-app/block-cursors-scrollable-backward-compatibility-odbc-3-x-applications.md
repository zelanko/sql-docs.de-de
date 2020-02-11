---
title: Kompatibilität von Block-und scrollfähigen Cursorn für ODBC 3. x | Microsoft-Dokumentation
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
ms.openlocfilehash: 7d12906f8dec0bfb12fc861c067e6e615e758a3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68134988"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen
Das vorhanden sein von **SQLFetchScroll** und **SQLExtendedFetch** stellt die erste Clear-Teilung in ODBC zwischen der Anwendungsprogrammierschnittstelle (Application Programming Interface, API) dar. dabei handelt es sich um den Satz von Funktionen, den die Anwendung aufruft, und um die Service Provider Interface (SPI), die den Satz von Funktionen darstellt, den der Treiber implementiert. Diese Aufteilung ist erforderlich, um die Anforderung in ODBC *3. x*auszugleichen, die **SQLFetchScroll**verwendet, um den Standards zu entsprechen und mit ODBC *2. x*kompatibel zu sein, das **sqlextendecodfetch**verwendet.  
  
 Die ODBC *3. x* -API, d. h. der Satz von Funktionen, die die Anwendung aufruft, umfasst **SQLFetchScroll** und verwandte Anweisungs Attribute. Der ODBC *3. x* SPI, d. h. der Satz von Funktionen, den der Treiber implementiert, umfasst **SQLFetchScroll**, **SQLExtendedFetch**und verwandte Anweisungs Attribute. Da ODBC diese Aufteilung zwischen der API und der SPI nicht formal erzwingt, ist es möglich, dass ODBC *3. x* -Anwendungen **sqlextenentdfetch** und verwandte Anweisungs Attribute aufruft. Hierfür gibt es jedoch keinen Grund für ODBC *3. x* -Anwendungen. Weitere Informationen zu APIs und SPIs finden Sie unter Einführung in die [ODBC-Architektur](../../../odbc/reference/odbc-architecture.md).  
  
 Informationen dazu, wie der ODBC *3. x* -Treiber-Manager Aufrufe an ODBC *2. x* -und ODBC *3. x* -Treiber zuordnet und welche Funktionen und Anweisungs Attribute ein ODBC *3. x* -Treiber für Block-und Bild lauffähige Cursor implementieren sollte, finden Sie unter [was der Treiber](../../../odbc/reference/appendixes/what-the-driver-does.md) in Anhang G: Treiber Richtlinien für die Abwärtskompatibilität.  
  
 In der folgenden Tabelle ist zusammengefasst, welche Funktionen und Anweisungs Attribute eine ODBC *3. x* -Anwendung mit Block-und scrollfähigen Cursorn verwenden soll. Außerdem werden die Änderungen zwischen ODBC *2. x* und ODBC *3. x* in diesem Bereich aufgelistet, die von ODBC *3. x* -Anwendungen beachtet werden müssen, damit Sie mit ODBC *2. x* -Treibern kompatibel sind.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Verweist auf das Lesezeichen, das mit **SQLFetchScroll**verwendet werden soll.<br /><br /> Wenn eine Anwendung diese in einem ODBC *2. x* -Treiber festlegt, muss dies auf ein Lesezeichen mit fester Länge zeigen.|  
|SQL_ATTR_ROW_STATUS_PTR|Verweist auf das Zeilen Status Array, das von **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**und **SQLSetPos**ausgefüllt wird.<br /><br /> Wenn eine Anwendung diese in einem ODBC *2. x* -Treiber festlegt und **sqlbulkoperation** mit einem *Vorgang* von SQL_ADD aufruft, **bevor SQLFetchScroll**, **SQLFetch**oder **SQLExtendedFetch**aufgerufen wird, wird SQLSTATE HY011 (das Attribut kann jetzt nicht festgelegt werden) zurückgegeben.<br /><br /> Wenn eine Anwendung **SQLFetch** in einem ODBC *2. x* -Treiber aufruft, wird **SQLFetch** **SQLExtendedFetch** zugeordnet und gibt daher Werte in diesem Array zurück.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Verweist auf den Puffer, in dem **SQLFetch** und **SQLFetchScroll** die Anzahl der abgerufenen Zeilen zurückgeben.<br /><br /> Wenn eine Anwendung **SQLFetch** in einem ODBC *2. x* -Treiber aufruft, wird **SQLFetch** **SQLExtendedFetch** zugeordnet und gibt daher einen Wert in diesem Puffer zurück.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die Rowsetgröße fest.<br /><br /> Wenn eine Anwendung **SQLBulkOperations** mit einem *Vorgang* SQL_ADD in einem ODBC *2. x* -Treiber aufruft, werden SQL_ROWSET_SIZE für den Aufruf verwendet, nicht SQL_ATTR_ROW_ARRAY_SIZE, da der Aufruf **SQLSetPos** mit einem *Vorgang* von SQL_ADD zugeordnet ist, der SQL_ROWSET_SIZE verwendet.<br /><br /> Beim Aufrufen von **SQLSetPos** mit einem *Vorgang* von SQL_ADD oder **SQLExtendedFetch** in einem ODBC *2. x* -Treiber wird SQL_ROWSET_SIZE verwendet.<br /><br /> Beim Aufrufen von **SQLFetch** oder **SQLFetchScroll** in einem ODBC *2. x* -Treiber wird SQL_ATTR_ROW_ARRAY_SIZE verwendet.|  
|**SQLBulkOperations**|Führt INSERT-und Bookmark-Vorgänge aus. Wenn **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD in einem ODBC *2. x* -Treiber aufgerufen wird, wird es **SQLSetPos** mit einem *Vorgang* von SQL_ADD zugeordnet. Im folgenden finden Sie Implementierungsdetails:<br /><br /> : Bei der Arbeit mit einem ODBC *2. x* -Treiber darf eine Anwendung nur den implizit zugeordneten ARD verwenden, der mit dem *StatementHandle*verknüpft ist. Es kann keinen anderen ARD zum Hinzufügen von Zeilen zuordnen, da explizite deskriptorvorgänge in einem ODBC *2. x* -Treiber nicht unterstützt werden. Eine Anwendung muss **SQLBindCol** zum Binden an den ARD, nicht an **SQLSetDescField** oder **SQLSetDescRec**verwenden.<br />-Wenn ein ODBC *3. x* -Treiber aufgerufen wird, kann eine **Anwendung SQLBulkOperations** mit einem *Vorgang* von SQL_ADD aufrufen, bevor **SQLFetch** oder **SQLFetchScroll**aufgerufen wird. Wenn ein ODBC *2. x* -Treiber aufgerufen wird, muss eine Anwendung **SQLFetchScroll** aufrufen, bevor **SQLBulkOperations** mit einem Vorgang von SQL_ADD aufgerufen wird.|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im folgenden finden Sie Implementierungsdetails:<br /><br /> : Wenn eine Anwendung **SQLFetch** in einem ODBC *2. x* -Treiber aufruft, wird Sie **SQLExtendedFetch**zugeordnet.<br />: Wenn eine Anwendung **SQLFetch** in einem ODBC *3. x* -Treiber aufruft, gibt Sie die Anzahl der Zeilen zurück, die mit dem SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut angegeben werden.|  
|**SQLFetchScroll**|Gibt das angegebene Rowset zurück. Im folgenden finden Sie Implementierungsdetails:<br /><br /> : Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *2. x* -Treiber aufruft, wird vor jedem Fehler, der auf eine einzelne Zeile angewendet wird, SQLSTATE 01s01 (Fehler in Zeile) zurückgegeben. Dies geschieht nur, weil der ODBC *3. x* -Treiber-Manager **sqlextendebug** und **sqlextendecodfetch** diesen SQLSTATE zurückgibt. Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *3. x* -Treiber aufruft, gibt Sie niemals SQLSTATE 01s01 zurück (Fehler in Zeile).<br />Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *2. x* -Treiber aufruft, bei dem *FetchOrientation* auf SQL_FETCH_BOOKMARK festgelegt ist, muss das *FetchOffset* -Argument auf 0 festgelegt werden. SQLSTATE HYC00 (optionales Feature nicht implementiert) wird zurückgegeben, wenn ein Offset basiertes Lesezeichen mit einem ODBC *2. x* -Treiber versucht wird.|  
  
> [!NOTE]  
>  ODBC *3. x* -Anwendungen sollten nicht **sqlextendecodfetch** oder das SQL_ROWSET_SIZE-Anweisungs Attribut verwenden. Stattdessen sollten Sie **SQLFetchScroll** und das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungs Attribut verwenden. ODBC *3. x* -Anwendungen sollten **SQLSetPos** nicht mit einem *Vorgang* von SQL_ADD verwenden, sondern **SQLBulkOperations** mit einem SQL_ADD *Vorgang* verwenden.
