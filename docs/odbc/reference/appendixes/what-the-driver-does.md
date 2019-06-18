---
title: Was bewirkt, dass der Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 685f67c9f24593a5c50097de426b76fef068d6e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735018"
---
# <a name="what-the-driver-does"></a>Funktionen des Treibers
Die folgende Tabelle fasst zusammen, welche Funktionen und Anweisungsattribute eine ODBC 3. *.x* -Treiber für Blockierung und scrollfähige Cursor implementieren soll.  
  
|Funktion oder<br /><br /> Anweisungsattribut|Kommentare|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|Legt die Adresse der zeilenstatusarray, indem ausgefüllt **SQLFetch** und **SQLFetchScroll**. Dieses Array wird auch durch gefüllt **SQLSetPos** Wenn **SQLSetPos** Anweisung Status S6 aufgerufen wird. Wenn **SQLSetPos** heißt S7 Status dieses Array nicht ausgefüllt ist, aber das Array verweist die *RowStatusArray* Argument **SQLExtendedFetch** gefüllt wird. Weitere Informationen finden Sie unter [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Übergang Statustabellen.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Legt die Adresse des Puffers, in dem **SQLFetch** und **SQLFetchScroll** geben die Anzahl der abgerufenen Zeilen zurück. Wenn **SQLExtendedFetch** wird aufgerufen, diesen Puffer nicht ausgefüllt ist aber die *RowCountPtr* -Argument zeigt auf die Anzahl der abgerufenen Zeilen.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Legt die Größe des Rowsets, die von verwendet **SQLFetch** und **SQLFetchScroll**.|  
|SQL_ROWSET_SIZE|Legt die Größe des Rowsets, die von verwendet **SQLExtendedFetch**. ODBC 3. *.x* Treiber implementieren Sie dies, wenn sie mit ODBC 2. arbeiten möchten. *X* Anwendungen, die Aufrufen **SQLExtendedFetch** oder **SQLSetPos**.|  
|**SQLBulkOperations**|Wenn eine ODBC 3. *.x* Treiber sollte mit ODBC 2. funktionieren. *X* Anwendungen, die **SQLSetPos** mit einer *Vorgang* von SQL_ADD, muss der Treiber unterstützen **SQLSetPos** mit einer  *Vorgang* von SQL_ADD zusätzlich zu **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD.|  
|**SQLExtendedFetch**|Gibt den angegebene Rowset zurück. ODBC 3. *.x* Treiber implementieren Sie dies, wenn sie mit ODBC 2. arbeiten möchten. *X* Anwendungen, die Aufrufen **SQLExtendedFetch** oder **SQLSetPos**. Im folgenden finden Details zur Implementierung:<br /><br /> -Der Treiber Ruft die Größe des Rowsets ab, aus dem Wert des Attributs Anweisung SQL_ROWSET_SIZE setzen.<br />-Der Treiber Ruft die Adresse der zeilenstatusarray aus der *RowStatusArray* Argument, das nicht das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR. Die *RowStatusArray* Argument in einem Aufruf von **SQLExtendedFetch** darf nicht null-Zeiger sein. (Beachten Sie, dass in ODBC 3. *.x*, das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR kann ein null-Zeiger sein.)<br />-Der Treiber Ruft die Adresse des Puffers abgerufenen Zeilen aus der *RowCountPtr* Argument, das nicht das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut.<br />-Der Treiber gibt SQLSTATE 01 s 01 (Fehler in Zeile), um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen, durch einen Aufruf von abgerufen wurden **SQLExtendedFetch**. Eine ODBC 3. *.x* Treiber SQLSTATE 01 s 01 sollte zurückgegeben werden (Fehler in Zeile) nur, wenn **SQLExtendedFetch** aufgerufen wird, nicht wenn **SQLFetch** oder **SQLFetchScroll** aufgerufen wird. Abwärtskompatibilität beibehalten. bei der SQLSTATE 01 s 01 (Fehler in Zeile) wird zurückgegeben, indem **SQLExtendedFetch**, sortiert der Treiber-Manager Statusdatensätze nicht in der Fehlerwarteschlange gemäß den Regeln in der "Reihenfolge der Status des angegebenen Zeichnet"im Abschnitt [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).|  
|**SQLFetch**|Gibt das nächste Rowset zurück. Im folgenden finden Details zur Implementierung:<br /><br /> -Der Treiber Ruft die Größe des Rowsets ab, aus dem Wert des Attributs SQL_ATTR_ROW_ARRAY_SIZE-Anweisung.<br />-Der Treiber Ruft die Adresse der zeilenstatusarray aus das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR ab.<br />-Der Treiber Ruft die Adresse der Puffer aus das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut abgerufenen Zeilen ab.<br />– Die Anwendung kann Aufrufe zwischen mischen **SQLFetchScroll** und **SQLFetch**.<br />-   **SQLFetch** Lesezeichen gibt zurück, wenn die Spalte 0 gebunden ist.<br />-   **SQLFetch** aufgerufen werden, um mehr als eine Zeile zurückgegeben.<br />-Der Treiber keinen SQLSTATE 01 s 01 zurückgibt (Fehler in Zeile), um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen, durch einen Aufruf von abgerufen wurden **SQLFetch**.|  
|**SQLFetchScroll**|Gibt den angegebene Rowset zurück. Im folgenden finden Details zur Implementierung:<br /><br /> -Der Treiber Ruft die Größe des Rowsets aus dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut-Anweisung ab.<br />-Der Treiber Ruft die Adresse der zeilenstatusarray aus das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR ab.<br />-Der Treiber Ruft die Adresse der Puffer aus das SQL_ATTR_ROWS_FETCHED_PTR-Anweisungsattribut abgerufenen Zeilen ab.<br />– Die Anwendung kann Aufrufe zwischen mischen **SQLFetchScroll** und **SQLFetch**.<br />-Der Treiber keinen SQLSTATE 01 s 01 zurückgibt (Fehler in Zeile), um anzugeben, dass ein Fehler aufgetreten ist, während die Zeilen, durch einen Aufruf von abgerufen wurden **SQLFetchScroll**.|  
|**SQLSetPos**|Führt verschiedene positionierte Operationen aus. Im folgenden finden Details zur Implementierung:<br /><br /> – Dies kann in der Anweisung Zustände S6 oder S7 aufgerufen werden. Weitere Informationen finden Sie unter [Statusübergänge](../../../odbc/reference/appendixes/statement-transitions.md) in Anhang B: ODBC-Übergang Statustabellen.<br />– Wenn Sie diese Anweisung Status S5 "oder" S6 aufgerufen wird, ruft der Treiber die Rowsetgröße von das SQL_ATTR_ROWS_FETCHED_PTR-Attribut-Anweisung und die Adresse der zeilenstatusarray aus das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR ab.<br />– Wenn Sie diese Anweisung Status S7 aufgerufen wird, ruft der Treiber die Rowsetgröße von das Anweisungsattribut SQL_ROWSET_SIZE setzen und die Adresse der zeilenstatusarray aus der *RowStatusArray* Argument  **SQLExtendedFetch**.<br />-Der Treiber gibt SQLSTATE 01 s 01 (Fehler in Zeile) nur an, wenn ein Fehler aufgetreten ist, während die Zeilen, durch einen Aufruf von abgerufen wurden **SQLSetPos** ein Massenvorgangs ausführen, wenn die Funktion im Zustand S7 aufgerufen wird. Um Abwärtskompatibilität zu gewährleisten, wenn beizubehalten SQLSTATE 01 s 01 (Fehler in Zeile) wird zurückgegeben, indem **SQLSetPos**, sortiert der Treiber-Manager Statusdatensätze nicht in der Fehlerwarteschlange gemäß den Regeln, die in die "Sequenz der Statusdatensätze" angegeben im Abschnitt [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).<br />– Wenn der Treiber für ODBC 2 geeignet sein sollte. *x* Anwendungen, die Aufrufen **SQLSetPos** mit einer *Vorgang* Argument SQL_ADD, der Treiber muss unterstützen **SQLSetPos** mit einer  *Vorgang* SQL_ADD Argument.|
