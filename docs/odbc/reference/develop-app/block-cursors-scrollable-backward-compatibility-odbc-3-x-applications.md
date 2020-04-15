---
title: Block- und Scrollable Cursor-Kompatibilität für ODBC 3.x | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c526eff6e19014c923f05ad91551a7d7c66f5294
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306341"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Anwendungen
Das Vorhandensein von **SQLFetchScroll** und **SQLExtendedFetch** stellt die erste klare Aufteilung in ODBC zwischen der APPLICATION Programming Interface (API), dem Satz von Funktionen, die die Anwendung aufruft, und der Dienstanbieterschnittstelle (Service Provider Interface, SPI), dem Satz von Funktionen, die der Treiber implementiert, dar. Diese Aufteilung ist erforderlich, um die Anforderung in ODBC *3.x*auszugleichen, das **SQLFetchScroll**verwendet, um sich an den Standards auszurichten und mit ODBC *2.x*kompatibel zu sein, das **SQLExtendedFetch**verwendet.  
  
 Die ODBC *3.x-API,* die den Satz von Funktionen ist, die die Anwendung aufruft, enthält **SQLFetchScroll** und zugehörige Anweisungsattribute. Der ODBC *3.x* SPI, der Satz von Funktionen, die der Treiber implementiert, enthält **SQLFetchScroll**, **SQLExtendedFetch**und zugehörige Anweisungsattribute. Da ODBC diese Aufteilung zwischen api und SPI formal nicht erzwingt, ist es für ODBC *3.x-Anwendungen* möglich, **SQLExtendedFetch** und zugehörige Anweisungsattribute aufzurufen. Es gibt jedoch keinen Grund für ODBC *3.x-Anwendungen,* dies zu tun. Weitere Informationen zu APIs und SPIs finden Sie in der Einführung in [ODBC Architecture](../../../odbc/reference/odbc-architecture.md).  
  
 Informationen dazu, wie der ODBC *3.x* Driver Manager Aufrufe von ODBC *2.x-* und ODBC *3.x-Treibern* zuordnet und welche Funktionen und Anweisungsattribute ein ODBC *3.x-Treiber* für Block- und Scroll-Cursor implementieren sollte, finden Sie unter Was der Treiber in Anhang G: Treiberrichtlinien für die Abwärtskompatibilität [tut.](../../../odbc/reference/appendixes/what-the-driver-does.md)  
  
 In der folgenden Tabelle werden zusammengefasst, welche Funktionen und Anweisungsattribute eine ODBC *3.x-Anwendung* mit Block- und Scrollable-Cursor verwenden soll. Außerdem werden Änderungen zwischen ODBC *2.x* und ODBC *3.x* in diesem Bereich aufgeführt, die ODBC *3.x-Anwendungen* als mit ODBC *2.x-Treibern* kompatibel sein sollten.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Zeigt auf das Lesezeichen, das mit **SQLFetchScroll**verwendet werden soll.<br /><br /> Wenn eine Anwendung dies in einem ODBC *2.x-Treiber* festlegt, muss dies auf eine Textmarke mit fester Länge verweisen.|  
|SQL_ATTR_ROW_STATUS_PTR|Verweist auf das Zeilenstatusarray, das von **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**und **SQLSetPos**gefüllt wird.<br /><br /> Wenn eine Anwendung dies in einem ODBC *2.x-Treiber* festlegt und **SQLBulkOperation** mit einem *Vorgang* von SQL_ADD aufruft, bevor **SQLFetchScroll**, **SQLFetch**oder **SQLExtendedFetch**aufgerufen werden, wird SQLSTATE HY011 (Attribut kann jetzt nicht festgelegt werden) zurückgegeben.<br /><br /> Wenn eine Anwendung **SQLFetch** in einem ODBC *2.x-Treiber* aufruft, wird **SQLFetch** **SQLExtendedFetch** zugeordnet und gibt daher Werte in diesem Array zurück.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Punkte auf den Puffer, in dem **SQLFetch** und **SQLFetchScroll** die Anzahl der abgerufenen Zeilen zurückgeben.<br /><br /> Wenn eine Anwendung **SQLFetch** in einem ODBC *2.x-Treiber* aufruft, wird **SQLFetch** **SQLExtendedFetch** zugeordnet und gibt daher einen Wert in diesem Puffer zurück.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die Rowsetgröße fest.<br /><br /> Wenn eine Anwendung **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD in einem ODBC *2.x-Treiber* aufruft, wird SQL_ROWSET_SIZE für den Aufruf und nicht für SQL_ATTR_ROW_ARRAY_SIZE verwendet, da der Aufruf **SQLSetPos** mit einem *Vorgang* von SQL_ADD zugeordnet ist, der SQL_ROWSET_SIZE verwendet.<br /><br /> Das Aufrufen von **SQLSetPos** mit einem *Vorgang* von SQL_ADD oder **SQLExtendedFetch** in einem ODBC *2.x-Treiber* verwendet SQL_ROWSET_SIZE.<br /><br /> Das Aufrufen von **SQLFetch** oder **SQLFetchScroll** in einem ODBC *2.x-Treiber* verwendet SQL_ATTR_ROW_ARRAY_SIZE.|  
|**SQLBulkOperations**|Führt Einfüge- und Lesezeichenvorgänge aus. Wenn **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD in einem ODBC *2.x-Treiber* aufgerufen wird, wird es **SQLSetPos** mit einem *Vorgang* von SQL_ADD zugeordnet. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Bei der Arbeit mit einem ODBC *2.x-Treiber* darf eine Anwendung nur die implizit zugewiesene ARD verwenden, die dem *StatementHandle*zugeordnet ist; Eine andere ARD kann keine Zeilen hinzufügen, da explizite Deskriptorvorgänge in einem ODBC *2.x-Treiber* nicht unterstützt werden. Eine Anwendung muss **SQLBindCol** verwenden, um sie an die ARD zu binden, nicht **SQLSetDescField** oder **SQLSetDescRec**.<br />- Beim Aufrufen eines ODBC *3.x-Treibers* kann eine Anwendung **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD aufrufen, bevor **sie SQLFetch** oder **SQLFetchScroll aufruft.** Beim Aufrufen eines ODBC *2.x-Treibers* muss eine Anwendung **SQLFetchScroll** aufrufen, bevor **SQLBulkOperations** mit einem Vorgang von SQL_ADD aufgerufen wird.|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Wenn eine Anwendung **SQLFetch** in einem ODBC *2.x-Treiber* aufruft, wird sie **SQLExtendedFetch**zugeordnet.<br />- Wenn eine Anwendung **SQLFetch** in einem ODBC *3.x-Treiber* aufruft, gibt sie die Anzahl der Zeilen zurück, die mit dem Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung angegeben sind.|  
|**SQLFetchScroll**|Gibt das angegebene Rowset zurück. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *2.x-Treiber* aufruft, gibt sie SQLSTATE 01S01 (Fehler in zeile) vor jedem Fehler zurück, der für eine einzelne Zeile gilt. Dies geschieht nur, weil der ODBC *3.x-Treiber-Manager* dies **SQLExtendedFetch** zuordnet und **SQLExtendedFetch** diese SQLSTATE zurückgibt. Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *3.x-Treiber* aufruft, gibt sie SQLSTATE 01S01 (Fehler in zeile) nie zurück.<br />- Wenn eine Anwendung **SQLFetchScroll** in einem ODBC *2.x-Treiber* aufruft, wobei *FetchOrientation* auf SQL_FETCH_BOOKMARK festgelegt ist, muss das *FetchOffset-Argument* auf 0 gesetzt sein. SQLSTATE HYC00 (Optionale Funktion nicht implementiert) wird zurückgegeben, wenn Offset-basiertes Lesezeichen-Abruf mit einem ODBC *2.x-Treiber* versucht wird.|  
  
> [!NOTE]  
>  ODBC *3.x-Anwendungen* sollten **sqlExtendedFetch** oder das attribut SQL_ROWSET_SIZE-Anweisung nicht verwenden. Stattdessen sollten sie **SQLFetchScroll** und das Attribut SQL_ATTR_ROW_ARRAY_SIZE-Anweisung verwenden. ODBC *3.x-Anwendungen* sollten **SQLSetPos** nicht mit einem *Vorgang* von SQL_ADD, sondern **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD verwenden.
