---
title: Was der Fahrer tut | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0438478f5aa625ffdd4d3bcd1c0a6f0f80d3367
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301391"
---
# <a name="what-the-driver-does"></a>Funktionen des Treibers
In der folgenden Tabelle werden zusammengefasst, welche Funktionen und Anweisungsattribute ein ODBC *3.x-Treiber* für Block- und Scrollable-Cursor implementieren soll.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|Legt die Adresse des Zeilenstatusarrays fest, das von **SQLFetch** und **SQLFetchScroll**ausgefüllt wird. Dieses Array wird auch von **SQLSetPos** gefüllt, wenn **SQLSetPos** im Anweisungszustand S6 aufgerufen wird. Wenn **SQLSetPos** im Status S7 aufgerufen wird, wird dieses Array nicht gefüllt, aber das Array, auf das durch das *RowStatusArray-Argument* von **SQLExtendedFetch** verwiesen wird, wird gefüllt. Weitere Informationen finden Sie unter [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Zustandsübergangstabellen.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Legt die Adresse des Puffers fest, in dem **SQLFetch** und **SQLFetchScroll** die Anzahl der abgerufenen Zeilen zurückgeben. Wenn **SQLExtendedFetch** aufgerufen wird, wird dieser Puffer nicht gefüllt, aber das *RowCountPtr-Argument* zeigt auf die Anzahl der abgerufenen Zeilen.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die von **SQLFetch** und **SQLFetchScroll**verwendete Rowsetgröße fest.|  
|SQL_ROWSET_SIZE|Legt die von **SQLExtendedFetch**verwendete Rowsetgröße fest. ODBC *3.x-Treiber* implementieren dies, wenn sie mit ODBC *2.x-Anwendungen* arbeiten möchten, die **SQLExtendedFetch** oder **SQLSetPos**aufrufen.|  
|**SQLBulkOperations**|Wenn ein ODBC *3.x-Treiber* mit ODBC *2.x-Anwendungen* arbeiten soll, **die SQLSetPos** mit einem *Vorgang* von SQL_ADD verwenden, muss der Treiber **SQLSetPos** mit einem *Vorgang* von SQL_ADD zusätzlich zu **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD unterstützen.|  
|**SQLExtendedFetch**|Gibt das angegebene Rowset zurück. ODBC *3.x-Treiber* implementieren dies, wenn sie mit ODBC *2.x-Anwendungen* arbeiten möchten, die **SQLExtendedFetch** oder **SQLSetPos**aufrufen. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Der Treiber ruft die Rowsetgröße aus dem Wert des Attributs SQL_ROWSET_SIZE-Anweisung ab.<br />- Der Treiber ruft die Adresse des Zeilenstatusarrays aus dem *RowStatusArray-Argument* ab, nicht das SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut. Das *RowStatusArray-Argument* in einem Aufruf von **SQLExtendedFetch** darf kein Nullzeiger sein. (Beachten Sie, dass in ODBC *3.x*das SQL_ATTR_ROW_STATUS_PTR Anweisungsattribut ein Nullzeiger sein kann.)<br />- Der Treiber ruft die Adresse der abgerufenen Zeilen-Puffer aus dem *RowCountPtr-Argument* ab, nicht das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut.<br />- Der Treiber gibt SQLSTATE 01S01 (Fehler in der Zeile) zurück, um anzuzeigen, dass ein Fehler aufgetreten ist, während Zeilen durch einen Aufruf von **SQLExtendedFetch**abgerufen wurden. Ein ODBC *3.x-Treiber* sollte SQLSTATE 01S01 (Fehler in der Zeile) nur zurückgeben, wenn **SQLExtendedFetch** aufgerufen wird, nicht, wenn **SQLFetch** oder **SQLFetchScroll** aufgerufen wird. Um die Abwärtskompatibilität zu erhalten, ordnet der Treiber-Manager Statusdatensätze **SQLExtendedFetch**in der Fehlerwarteschlange nicht gemäß den Regeln an, die im Abschnitt "Sequenz von Statusdatensätzen" von [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)angegeben sind.|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Der Treiber ruft die Rowsetgröße aus dem Wert des Attributs SQL_ATTR_ROW_ARRAY_SIZE-Anweisung ab.<br />- Der Treiber ruft die Adresse des Zeilenstatusarrays aus dem Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung ab.<br />- Der Treiber ruft die Adresse der abgerufenen Zeilen-Puffer aus dem SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut ab.<br />- Die Anwendung kann Aufrufe zwischen **SQLFetchScroll** und **SQLFetch**mischen.<br />-   **SQLFetch** gibt Lesezeichen zurück, wenn Spalte 0 gebunden ist.<br />-   **SQLFetch** kann aufgerufen werden, um mehr als eine Zeile zurückzugeben.<br />- Der Treiber gibt SQLSTATE 01S01 (Fehler in der Zeile) nicht zurück, um anzuzeigen, dass ein Fehler aufgetreten ist, während Zeilen durch einen Aufruf von **SQLFetch**abgerufen wurden.|  
|**SQLFetchScroll**|Gibt das angegebene Rowset zurück. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Der Treiber ruft die Rowsetgröße aus dem SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut ab.<br />- Der Treiber ruft die Adresse des Zeilenstatusarrays aus dem Attribut SQL_ATTR_ROW_STATUS_PTR-Anweisung ab.<br />- Der Treiber ruft die Adresse der abgerufenen Zeilen-Puffer aus dem SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut ab.<br />- Die Anwendung kann Aufrufe zwischen **SQLFetchScroll** und **SQLFetch**mischen.<br />- Der Treiber gibt SQLSTATE 01S01 (Fehler in der Zeile) nicht zurück, um anzuzeigen, dass ein Fehler aufgetreten ist, während Zeilen durch einen Aufruf von **SQLFetchScroll**abgerufen wurden.|  
|**SQLSetPos**|Führt verschiedene positionierte Vorgänge aus. Im Folgenden sind Implementierungsdetails zu finden:<br /><br /> - Dies kann in den Anweisungszuständen S6 oder S7 aufgerufen werden. Weitere Informationen finden Sie unter [Anweisungsübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Zustandsübergangstabellen.<br />- Wenn dies im Anweisungszustand S5 oder S6 aufgerufen wird, ruft der Treiber die Rowsetgröße aus dem Attribut SQL_ATTR_ROWS_FETCHED_PTR-Anweisung und die Adresse des Zeilenstatusarrays aus dem SQL_ATTR_ROW_STATUS_PTR-Anweisungsattribut ab.<br />- Wenn dies im Anweisungszustand S7 aufgerufen wird, ruft der Treiber die Rowsetgröße aus dem Attribut SQL_ROWSET_SIZE-Anweisung und die Adresse des Zeilenstatusarrays aus dem *RowStatusArray-Argument* von **SQLExtendedFetch**ab.<br />- Der Treiber gibt SQLSTATE 01S01 (Fehler in der Zeile) nur zurück, um anzuzeigen, dass ein Fehler aufgetreten ist, während Zeilen durch einen Aufruf von **SQLSetPos** abgerufen wurden, um einen Massenvorgang auszuführen, wenn die Funktion im Status S7 aufgerufen wird. Um die Abwärtskompatibilität zu erhalten, ordnet der Treiber-Manager Statusdatensätze **SQLSetPos**in der Fehlerwarteschlange nicht gemäß den Regeln an, die im Abschnitt "Sequenz von Statusaufzeichnungen" von [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)angegeben sind.<br />- Wenn der Treiber mit ODBC *2.x-Anwendungen* arbeiten soll, die **SQLSetPos** mit dem *Operation-Argument* von SQL_ADD aufrufen, muss der Treiber **SQLSetPos** mit einem *Operation-Argument* von SQL_ADD unterstützen.|
