---
title: Funktionsweise des Treibers | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301391"
---
# <a name="what-the-driver-does"></a>Funktionen des Treibers
In der folgenden Tabelle ist zusammengefasst, welche Funktionen und Anweisungs Attribute ein ODBC *3. x* -Treiber für Block-und scrollfähige Cursor implementieren soll.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|Legt die Adresse des Zeilen Status Arrays fest, das von **SQLFetch** und **SQLFetchScroll**ausgefüllt wird. Dieses Array wird auch von **SQLSetPos** ausgefüllt, wenn **SQLSetPos** im Anweisungs Status S6 aufgerufen wird. Wenn **SQLSetPos** in State S7 aufgerufen wird, wird dieses Array nicht aufgefüllt, aber das Array, auf das das *rowstatusarray* -Argument von **sqlextendecodfetch** verweist, wird ausgefüllt. Weitere Informationen finden Sie unter [Anweisungs Übergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Status Übergangs Tabellen.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Legt die Adresse des Puffers fest, in der **SQLFetch** und **SQLFetchScroll** die Anzahl der abgerufenen Zeilen zurückgeben. Wenn **sqlextendecodfetch** aufgerufen wird, wird dieser Puffer nicht aufgefüllt, aber das *rowzähltptr* -Argument zeigt auf die Anzahl der abgerufenen Zeilen.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die von **SQLFetch** und **SQLFetchScroll**verwendete Rowsetgröße fest.|  
|SQL_ROWSET_SIZE|Legt die von **sqlextendecodfetch**verwendete Rowsetgröße fest. ODBC *3. x* -Treiber implementieren dies, wenn Sie mit ODBC *2. x* -Anwendungen arbeiten möchten, die **sqlextendebug** oder **SQLSetPos**aufrufen.|  
|**SQLBulkOperations**|Wenn ein ODBC *3. x* -Treiber mit ODBC *2. x* -Anwendungen verwendet werden soll, die **SQLSetPos** mit einem *Vorgang* von SQL_ADD verwenden, muss der Treiber **SQLSetPos** mit einem *Vorgang* von SQL_ADD unterstützen, zusätzlich zu **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD.|  
|**SQLExtendedFetch**|Gibt das angegebene Rowset zurück. ODBC *3. x* -Treiber implementieren dies, wenn Sie mit ODBC *2. x* -Anwendungen arbeiten möchten, die **sqlextendebug** oder **SQLSetPos**aufrufen. Im folgenden finden Sie Implementierungsdetails:<br /><br /> -Der Treiber ruft die Rowsetgröße aus dem Wert des Attributs der SQL_ROWSET_SIZE Anweisung ab.<br />-Der Treiber ruft die Adresse des Zeilen Status Arrays aus dem *rowstatusarray* -Argument ab, nicht das Attribut der SQL_ATTR_ROW_STATUS_PTR Anweisung. Das *rowstatus Array* -Argument in einem ' **sqlextendebug** '-Aufrufs darf kein NULL-Zeiger sein. (Beachten Sie, dass in ODBC *3. x*das SQL_ATTR_ROW_STATUS_PTR Statement-Attribut ein NULL-Zeiger sein kann.)<br />-Der Treiber ruft die Adresse des abgerufenen Zeilen Puffers aus dem *rowzähltptr* -Argument ab, nicht das Attribut der SQL_ATTR_ROWS_FETCHED_PTR Anweisung.<br />-Der Treiber gibt SQLSTATE 01s01 (Fehler in Zeile) zurück, um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen durch einen **SQLExtendedFetch**-Aufrufs abgerufen wurden. Ein ODBC *3. x* -Treiber sollte SQLSTATE 01s01 (Fehler in Zeile) nur dann zurückgeben, wenn **SQLExtendedFetch** aufgerufen wird, nicht wenn **SQLFetch** oder **SQLFetchScroll** aufgerufen wird. Um die Abwärtskompatibilität zu gewährleisten, werden von **SQLExtendedFetch**, wenn SQLSTATE 01s01 (Fehler in Zeile) von SQLExtendedFetch zurückgegeben wird, der Treiber-Manager keine Statusdaten Sätze in der Fehler Warteschlange entsprechend den Regeln in [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)in der Fehler Warteschlange sortiert.|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im folgenden finden Sie Implementierungsdetails:<br /><br /> -Der Treiber ruft die Rowsetgröße aus dem Wert des Attributs der SQL_ATTR_ROW_ARRAY_SIZE Anweisung ab.<br />-Der Treiber ruft die Adresse des Zeilen Status Arrays aus dem SQL_ATTR_ROW_STATUS_PTR Statement-Attribut ab.<br />-Der Treiber ruft die Adresse des abgerufenen Zeilen Puffers aus dem SQL_ATTR_ROWS_FETCHED_PTR Statement-Attribut ab.<br />-Die Anwendung kann Aufrufe zwischen **SQLFetchScroll** und **SQLFetch**kombinieren.<br />-   **SQLFetch** gibt Lesezeichen zurück, wenn die Spalte 0 gebunden ist.<br />-   **SQLFetch** kann aufgerufen werden, um mehr als eine Zeile zurückzugeben.<br />-Der Treiber gibt SQLSTATE 01s01 (Fehler in Zeile) nicht zurück, um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen durch einen **SQLFetch**-Befehl abgerufen wurden.|  
|**SQLFetchScroll**|Gibt das angegebene Rowset zurück. Im folgenden finden Sie Implementierungsdetails:<br /><br /> -Der Treiber ruft die Rowsetgröße aus dem SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut ab.<br />-Der Treiber ruft die Adresse des Zeilen Status Arrays aus dem SQL_ATTR_ROW_STATUS_PTR Statement-Attribut ab.<br />-Der Treiber ruft die Adresse des abgerufenen Zeilen Puffers aus dem SQL_ATTR_ROWS_FETCHED_PTR Statement-Attribut ab.<br />-Die Anwendung kann Aufrufe zwischen **SQLFetchScroll** und **SQLFetch**kombinieren.<br />-Der Treiber gibt SQLSTATE 01s01 (Fehler in Zeile) nicht zurück, um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen durch einen-Befehl von **SQLFetchScroll**abgerufen wurden.|  
|**SQLSetPos**|Führt verschiedene positionierte Vorgänge aus. Im folgenden finden Sie Implementierungsdetails:<br /><br /> : Kann in den Anweisungs Zuständen S6 oder S7 aufgerufen werden. Weitere Informationen finden Sie unter [Anweisungs Übergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Status Übergangs Tabellen.<br />-Wenn dies im Anweisungs Zustand S5 oder S6 aufgerufen wird, ruft der Treiber die Rowsetgröße aus dem Attribut der SQL_ATTR_ROWS_FETCHED_PTR Anweisung und die Adresse des Zeilen Status Arrays aus dem Attribut der SQL_ATTR_ROW_STATUS_PTR Anweisung ab.<br />-Wenn dies im Anweisungs Zustand "S7" aufgerufen wird, ruft der Treiber die Rowsetgröße aus dem SQL_ROWSET_SIZE-Anweisungs Attribut und die Adresse des Zeilen Status Arrays aus dem *rowstatusarray* -Argument von **SQLExtendedFetch**ab.<br />-Der Treiber gibt SQLSTATE 01s01 (Fehler in Zeile) nur zurück, um anzugeben, dass ein Fehler aufgetreten ist, während Zeilen durch einen Aufruf von **SQLSetPos** abgerufen wurden, um einen Massen Vorgang auszuführen, wenn die Funktion in Status "S7" aufgerufen wird. Wenn SQLSTATE 01s01 (Fehler in Zeile) von **SQLSetPos**zurückgegeben wird, sortiert der Treiber-Manager in der Fehler Warteschlange keine Status Einträge gemäß den Regeln, die im Abschnitt "Sequenz von Statusdaten Sätzen" von [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)angegeben sind, um die Abwärtskompatibilität aufrechtzuerhalten.<br />-Wenn der Treiber mit ODBC *2. x* -Anwendungen arbeiten soll, die **SQLSetPos** mit einem *Vorgangs* Argument von SQL_ADD aufrufen, muss der Treiber **SQLSetPos** mit dem *Vorgangs* Argument SQL_ADD unterstützen.|
