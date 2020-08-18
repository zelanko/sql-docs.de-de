---
description: Anweisungsübergänge
title: Anweisungs Übergänge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transitioning states [ODBC], statement
- state transitions [ODBC], statement
- statement transitions [ODBC]
ms.assetid: 3d70e0e3-fe83-4b4d-beac-42c82495a05b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3515b1d6aea4cab66bc01ee3d071727e6cb8f447
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386516"
---
# <a name="statement-transitions"></a>Anweisungsübergänge
ODBC-Anweisungen weisen die folgenden Zustände auf.  
  
|Staat|Beschreibung|  
|-----------|-----------------|  
|S0|Nicht zugewiesene Anweisung. (Der Verbindungsstatus muss C4, C5 oder C6 lauten. Weitere Informationen finden Sie unter [Verbindungs Übergänge](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Zugewiesene Anweisung.|  
|S2|Vorbereitete Anweisung. Es wird kein Resultset erstellt.|  
|S3|Vorbereitete Anweisung. Ein (möglicherweise leeres) Resultset wird erstellt.|  
|S4|Die Anweisung wurde ausgeführt, und es wurde kein Resultset erstellt.|  
|S5|Die Anweisung wurde ausgeführt, und es wurde ein (möglicherweise leeres) Resultset erstellt. Der Cursor ist geöffnet und positioniert vor der ersten Zeile des Resultsets.|  
|S6|Cursor, der mit **SQLFetch** oder **SQLFetchScroll**positioniert ist.|  
|S7|Cursor mit **sqlextendecodfetch**positioniert.|  
|S8|Die Funktion benötigt Daten. **SQLParamData** wurde nicht aufgerufen.|  
|S9|Die Funktion benötigt Daten. **SQLPutData** wurde nicht aufgerufen.|  
|S10|Die Funktion benötigt Daten. **SQLPutData** wurde aufgerufen.|  
|S11|Wird noch ausgeführt. Eine-Anweisung verbleibt in diesem Zustand, nachdem eine Funktion, die asynchron ausgeführt wird, SQL_STILL_EXECUTING zurückgibt. Eine-Anweisung befindet sich vorübergehend in diesem Zustand, während alle Funktionen, die ein Anweisungs Handle akzeptieren, ausgeführt werden. Der temporäre Wohnsitz in Bundesstaat wird in Zustands Tabellen mit Ausnahme der Statustabelle für **SQLCancel**nicht angezeigt. Während sich eine-Anweisung temporär im Bundesstaat S11 befindet, kann die Funktion durch Aufrufen von **SQLCancel** von einem anderen Thread abgebrochen werden.|  
|S12|Asynchrone Ausführung abgebrochen. In S12 muss eine Anwendung die abgebrochene Funktion so lange aufzurufen, bis Sie einen anderen Wert als SQL_STILL_EXECUTING zurückgibt. Die Funktion wurde nur erfolgreich abgebrochen, wenn die Funktion SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurückgibt. Wenn ein anderer Wert zurückgegeben wird, z. b. SQL_SUCCESS, ist der Abbruch Vorgang fehlgeschlagen, und die Funktion wird normal ausgeführt.|  
  
 Die Zustände S2 und S3 werden als vorbereitete Zustände bezeichnet, Zustände S5 bis S7 als Cursor Zustände, Status S8 bis S10 als benötigte Datenzustände und Bundesstaaten S11 und S12 als asynchrone Zustände. In jeder dieser Gruppen werden die Übergänge separat angezeigt, wenn Sie für jeden Status in der Gruppe unterschiedlich sind. in den meisten Fällen sind die Übergänge für jeden Status in jeder Gruppe identisch.  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Anweisungs Zustand auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1 [3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DBC wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [4] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde.  
  
 [5] das Aufrufen von **sqlbinchandle** mit *outputhandleptr* , das auf ein gültiges Handle verweist, überschreibt dieses Handle ohne Berücksichtigung der vorherigen Inhalte dieses Handles und kann zu Problemen mit ODBC-Treibern führen. Es ist eine falsche ODBC-Anwendungsprogrammierung zum doppelten Aufrufen von **sqlzuordchandle** mit der gleichen Anwendungsvariablen, die für * \* outputhandleptr* definiert ist, ohne **SQLFreeHandle** aufzurufen, um das Handle vor der erneuten Zuordnung freizugeben. Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistenten Verhalten oder Fehlern im Rahmen der ODBC-Treiber führen.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>Sqlbrowseconnetct, SQLCONNECT und SQLDriverConnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Nächste Tabelle anzeigen|HY010|NS [c] HY010 o|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[s] S8 [d] S11 [x]|--[s] S8 [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|S1 [1] S2 [Nr] und [2] S3 [r] und [2] S5 [3] und [5] S6 ([3] oder [4]) und [6] S7 [4] und [7]|Nächste Tabelle anzeigen|  
  
 [1]   **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2]   **SQLExecute** hat SQL_NEED_DATA zurückgegeben.  
  
 [3]   **SQLBulkOperations** hat SQL_NEED_DATA zurückgegeben.  
  
 [4]   **SQLSetPos** haben SQL_NEED_DATA zurückgegeben.  
  
 [5] '   **SQLFetch**', ' **SQLFetchScroll**' oder ' **sqlextendebug** ' wurde nicht aufgerufen.  
  
 [6]   **SQLFetch** oder **SQLFetchScroll** wurde aufgerufen.  
  
 [7]   **sqlextendebug** wurde aufgerufen.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (asynchrone Zustände)  
  
|S11<br /><br /> Wird noch ausgeführt|S12<br /><br /> Asynch abgebrochen|  
|-----------------------------|-----------------------------|  
|NS [1] S12 [2]|S12|  
  
 [1] die Anweisung befand sich vorübergehend im Zustand "S11", während eine Funktion ausgeführt wurde. **SQLCancel** wurde von einem anderen Thread aufgerufen.  
  
 [2] die Anweisung befand sich im Status "S11", da eine Funktion, die asynchron aufgerufen wurde, SQL_STILL_EXECUTING.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|24.000|24.000|24.000|S1 [NP] S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Nächste Tabelle anzeigen|24.000|--[s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|--[1] 07005 [2]|--[s] S11 x|  
  
 [1]   *fieldidentifier* wurde SQL_DESC_COUNT.  
  
 [2]   *fieldidentifier* wurde nicht SQL_DESC_COUNT.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, sqlauslännkeys, SQLGetTypeInfo, SQLPrimaryKeys, sqlprocedurecolrens, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S5 [s] S11 [x]|S1 [e] S5 [s] S11 [x]|S1 [e] und [1] S5 [s] und [1] S11 [x] und [1] 24000 [2]|Nächste Tabelle anzeigen|HY010|NS [c] HY010 o|  
  
 [1] das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es sind keine aktuellen Ergebnisse vorhanden. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, sqlauslännkeys, SQLGetTypeInfo, SQLPrimaryKeys, sqlprocedurecolumschlag, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24000 [1]|24.000|  
  
 [1] dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben wurde und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlcopydesc"></a>Sqlcopyde SC  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|--|--|HY010|NS [c] und [3] HY010 [o] oder [4]|  
|IH [2]|HY010|Nächste Tabelle anzeigen|24.000|--[s] S11 x|HY010|NS [c] und [3] HY010 [o] oder [4]|  
  
 [1] diese Zeile zeigt Übergänge an, wenn das *sourcedeschandle* -Argument ein ARD, eine APD oder eine IPD war.  
  
 [2] diese Zeile zeigt Übergänge an, wenn das *sourcedeschandle* -Argument ein IRD war.  
  
 [3] die Argumente *sourcedebug* und *targetbeschandle* waren identisch mit denen in der **sqlcopydebug** -Funktion, die asynchron ausgeführt wird.  
  
 [4] das *sourceenschandle* -Argument oder das *targetbeschandle* -Argument (oder beides) unterscheiden sich von der asynchronen Ausführung in der **sqlcopydebug** -Funktion.  
  
## <a name="sqlcopydesc-prepared-states"></a>Sqlcopyde SC (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|24000 [1]|--[s] S11 [x]|  
  
 1 Diese Zeile zeigt Übergänge an, wenn das *sourcedeschandle* -Argument ein IRD war.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Nächste Tabelle anzeigen|24.000|--[s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|07005|--[s] S11 [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--[s] S11 [x]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0 [1]|S0 [1]|S0 [1]|S0 [1]|HY010|HY010|  
  
 [1] durch den Aufruf von **SQLDisconnect** werden alle der Verbindung zugeordneten Anweisungen freigegeben. Außerdem wird der Verbindungsstatus in C2 zurückgegeben. der Verbindungsstatus muss C4 lauten, bevor der Anweisungs Zustand S0 lautet.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--[2] oder [3] S1 [1]|--[3] S1 [NP] und ([1] oder [2]) S1 [p] und [1] S2 [p] und [2]|--[3] S1 [NP] und ([1] oder [2]) S1 [p] und [1] S3 [p] und [2]|HY010|HY010|  
  
 [1] das *CompletionType* -Argument ist SQL_COMMIT, und **SQLGetInfo** gibt SQL_CB_DELETE für den SQL_CURSOR_COMMIT_BEHAVIOR Informationstyp zurück, oder das *CompletionType* -Argument ist SQL_ROLLBACK, und **SQLGetInfo** gibt SQL_CB_DELETE für den SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstyp zurück.  
  
 [2] das *CompletionType* -Argument ist SQL_COMMIT, und **SQLGetInfo** gibt SQL_CB_CLOSE für den SQL_CURSOR_COMMIT_BEHAVIOR Informationstyp zurück, oder das *CompletionType* -Argument ist SQL_ROLLBACK, und **SQLGetInfo** gibt SQL_CB_CLOSE für den SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstyp zurück.  
  
 [3] das *CompletionType* -Argument ist SQL_COMMIT, und **SQLGetInfo** gibt SQL_CB_PRESERVE für den SQL_CURSOR_COMMIT_BEHAVIOR Informationstyp zurück, oder das *CompletionType* -Argument ist SQL_ROLLBACK, und **SQLGetInfo** gibt SQL_CB_PRESERVE für den SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstyp zurück.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S4 [s] und [Nr] S5 [s] und [r] S8 [d] S11 [x]|--[e] und [1] S1 [e] und [2] S4 [s] und [Nr] S5 [s] und [r] S8 [d] S11 [x]|--[e], [1] und [3] S1 [e], [2] und [3] S4 [s], [Nr] und [3] S5 [s], [r] und [3] S8 [d] und [3] S11 [x] und [3] 24000 [4]|Nächste Tabelle anzeigen|HY010|NS [c] HY010 [o]|  
  
 [1] der Fehler wurde vom Treiber-Manager zurückgegeben.  
  
 [2] der Fehler wurde vom Treiber-Manager nicht zurückgegeben.  
  
 [3] das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es sind keine aktuellen Ergebnisse vorhanden. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24000 [1]|24.000|  
  
 [1] dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Nächste Tabelle anzeigen|S2 [e], p, und [1] S4 [s], [p], [Nr] und [1] S5 [s], [p], [r] und [1] S8 [d], [p] und [1] S11 [x], [p] und [1] 24000 [p] und [2] HY010 [NP]|Siehe Cursor Statustabelle|HY010|NS [c] HY010 [o]|  
  
 [1] das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es sind keine aktuellen Ergebnisse vorhanden. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|S4 [s], S8 [d] S11 [x]|S5 [s], S8 [d] S11 [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 [p] HY010 [NP]|24000 [p], [1] HY010 [NP]|24000 [p] HY010 [NP]|  
  
 [1] dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** nicht SQL_NO_DATA zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S1010|S1010|24.000|Nächste Tabelle anzeigen|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>Sqlextendebug (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] oder [NF] S11 [x]|S1010|--[s] oder [NF] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch und SQLFetchScroll  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Nächste Tabelle anzeigen|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch und SQLFetchScroll (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] oder [NF] S11 [x]|--[s] oder [NF] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|IH [2]|S0|S0|S0|S0|HY010|HY010|  
|--[3]|--|--|--|--|--|--|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV oder SQL_HANDLE_DBC wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [3] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_DESC wurde und der Deskriptor explizit zugewiesen wurde.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|S1 [NP] S2 [p]|S1 [NP] S3 [p]|HY010|HY010|  
|IH [2]|--|--|--|--|HY010|HY010|  
  
 [1] diese Zeile zeigt Übergänge an, wenn die *Option* SQL_CLOSE wurde.  
  
 [2] diese Zeile zeigt Übergänge an, wenn die *Option* SQL_UNBIND oder SQL_RESET_PARAMS. Wenn das *options* Argument SQL_DROP und der zugrunde liegende Treiber ein ODBC 3 *. x* -Treiber ist, ordnet der Treiber-Manager diese einem **SQLFreeHandle** -aufrufsSQL_HANDLE_STMT *Typ* zu Weitere Informationen finden Sie in der Übergangs Tabelle für [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Nächste Tabelle anzeigen|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|--[s] oder [NF] S11 [x] 24000 [b] HY109 [i]|--[s] oder [NF] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1] oder [2] HY010 [3]|Nächste Tabelle anzeigen|--[1] oder [2] 24000 [3]|--[1], [2] oder [3] S11 [3] und [x]|HY010|NS [c] oder [4] HY010 [o] und [5]|  
  
 [1] das *Deskriptorhandle* -Argument war eine APD oder ein ARD.  
  
 [2] das *Deskriptorhandle* -Argument war eine IPD.  
  
 [3] das *Deskriptorhandle* -Argument war ein IRD.  
  
 [4] das *Deskriptorhandle* -Argument war mit dem *Deskriptorhandle* -Argument in der **SQLGetDescField** -oder **SQLGetDescRec** -Funktion identisch, die asynchron ausgeführt wird.  
  
 [5] das *Deskriptorhandle* -Argument unterscheidet sich vom *Deskriptorhandle* -Argument in der **SQLGetDescField** -oder **SQLGetDescRec** -Funktion, die asynchron ausgeführt wird.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField und SQLGetDescRec (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|--[1], [2] oder [3] S11 [2] und [x]|--[1], [2] oder [3] S11 [x]|  
  
 [1] das *Deskriptorhandle* -Argument war eine APD oder ein ARD.  
  
 [2] das *Deskriptorhandle* -Argument war eine IPD.  
  
 [3] das *Deskriptorhandle* -Argument war ein IRD. Beachten Sie, dass diese Funktionen immer SQL_NO_DATA in Status S2 zurückgeben, wenn *descriptorhandle* ein IRD war.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|IH [2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_ENV, SQL_HANDLE_DBC oder SQL_HANDLE_DESC war.  
  
 [2] diese Zeile zeigt Übergänge an, wenn der *Handtyp* SQL_HANDLE_STMT wurde.  
  
 [3]   **SQLGetDiagField** gibt immer einen Fehler in diesem Zustand zurück, wenn *DiagIdentifier* SQL_DIAG_ROW_COUNT ist.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1] 24000 [2]|--[1] 24000 [2]|--[1] 24000 [2]|Nächste Tabelle anzeigen|HY010|HY010|  
  
 [1] das Anweisungs Attribut wurde nicht SQL_ATTR_ROW_NUMBER.  
  
 [2] das Anweisungs Attribut wurde SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000 [2]|--[1] oder ([v] und [2]) 24000 [b] und [2] HY109 [i] und [2]|--[i] oder ([v] und [2]) 24000 [b] und [2] HY109 [1] und [2]|  
  
 [1] das *Attribut* Argument wurde nicht SQL_ATTR_ROW_NUMBER.  
  
 [2] das *Attribut* Argument wurde SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1]|--[1]|--[s] und [2] S1 [NF], [NP] und [4] S2 [NF], [p] und [4] S5 [s] und [3] S11 [x]|S1 [NF], [NP] und [4] S3 [NF], [p] und [4] S4 [s] und [2] S5 [s] und [3] S11 [x]|HY010|NS [c] HY010 [o]|  
  
 [1] die Funktion gibt immer SQL_NO_DATA in diesem Zustand zurück.  
  
 [2] das nächste Ergebnis ist eine Zeilen Anzahl.  
  
 [3] das nächste Ergebnis ist ein Resultset.  
  
 [4] das aktuelle Ergebnis ist das letzte Ergebnis.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--[s] S11 [x]|--[s] S11 [x]|--[s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|--[s] S11 [x]|--[s] S11 [x]|--[s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Nächste Tabelle anzeigen|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (Datenzustände erforderlich)  
  
|S8<br /><br /> Benötigen von Daten|S9<br /><br /> Muss|S10<br /><br /> Kann einfügen|  
|----------------------|---------------------|---------------------|  
|S1 [e] und [1] S2 [e], [Nr] und [2] S3 [e], [r] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S9 [d] S11 [x]|HY010|S1 [e] und [1] S2 [e], [Nr] und [2] S3 [e], [r] und [2] S4 [s], [Nr], and ([1] or [2]) S5 [s], [r], and ([1] oder [2]) S5 ([s] oder [e]) und [4] S6 ([s] oder [e]) und [5] S7 ([s] oder [e]) und [3] S9 [d] S11 [x]|  
  
 [1]   **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2]   **SQLExecute** hat SQL_NEED_DATA zurückgegeben.  
  
 [3]   **SQLSetPos** wurde von State S7 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [4]   **SQLBulkOperations** wurde aus dem Status "S5" aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [5]   **SQLSetPos** oder **SQLBulkOperations** wurde von Status S6 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S2 [s] und [Nr] S3 [s] und [r] S11 [x]|--[s] oder ([e] und [1]) S1 [e] und [2] S11 [x]|S1 [e] und [3] S2 [s], [Nr] und [3] S3 [s], [r] und [3] S11 [x] und [3] 24000 [4]|Nächste Tabelle anzeigen|HY010|NS [c] HY010 [o]|  
  
 [1] die Vorbereitung schlägt aus einem anderen Grund als dem Validieren der Anweisung fehl (SQLSTATE war HY009 [Ungültiger Argument Wert] oder HY090 [ungültige Zeichenfolge oder Pufferlänge]).  
  
 [2] die Vorbereitung schlägt fehl, während die Anweisung überprüft wird (SQLSTATE war nicht HY009 [Ungültiger Argument Wert] oder HY090 [ungültige Zeichenfolge oder Pufferlänge]).  
  
 [3] das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es sind keine aktuellen Ergebnisse vorhanden. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24.000|24.000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Nächste Tabelle anzeigen|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (Datenzustände erforderlich)  
  
|S8<br /><br /> Benötigen von Daten|S9<br /><br /> Muss|S10<br /><br /> Kann einfügen|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] und [1] S2 [e], [Nr] und [2] S3 [e], [r] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S10 [s] S11 [x]|--[s] S1 [e] und [1] S2 [e], [Nr], [2] S3 [e], [r] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S11 [x] HY011 [6]|  
  
 [1]   **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2]   **SQLExecute** hat SQL_NEED_DATA zurückgegeben.  
  
 [3]   **SQLSetPos** wurde von State S7 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [4]   **SQLBulkOperations** wurde aus dem Status "S5" aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [5]   **SQLSetPos** oder **SQLBulkOperations** wurde von Status S6 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [6] mindestens ein Aufruf von **SQLPutData** für einen einzelnen Parameter, der SQL_SUCCESS zurückgegeben wurde, und anschließend wurde ein Aufruf von **SQLPutData** für denselben Parameter durchgeführt, wobei *StrLen_Or_Ind* auf SQL_NULL_DATA festgelegt wurde.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|--|--|HY010|HY010|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000 [3]|HY010|HY010|  
  
 [1] diese Zeile zeigt Übergänge an, wenn das *Attribut* ein Verbindungs Attribut war. Informationen zu Übergängen, bei denen das *Attribut* ein Anweisungs Attribut war, finden Sie in der Anweisungs Übergangs Tabelle für **SQLSetStmtAttr**.  
  
 [2] das *Attribut* Argument wurde nicht SQL_ATTR_CURRENT_CATALOG.  
  
 [3] das *Attribut* Argument wurde SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|24.000|24.000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|--|--|HY010|HY010|  
  
 [1] diese Zeile zeigt Übergänge an, bei denen das *Deskriptorhandle* -Argument eine ARD, APD, IPD oder (für **SQLSetDescField**) ein IRD ist, wenn das *fieldidentifier* -Argument SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR ist. Es ist ein Fehler, **SQLSetDescField** für einen IRD aufzurufen, wenn *fieldidentifier* ein beliebiger anderer Wert ist.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Nächste Tabelle anzeigen|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (Cursor Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|--[s] S8 [d] S11 [x] 24000 [b] HY109 [i]|--[s] S8 [d] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--[1] HY011 [2]|--[1] 24000 [2]|--[1] 24000 [2]|HY010 [NP] oder [1] HY011 [p] und [2]|HY010 [NP] oder [1] HY011 [p] und [2]|  
  
 [1] das *Attribut* Argument wurde nicht SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE oder SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] das *Attribut* Argument lautete SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE oder SQL_ATTR_CURSOR_SENSITIVITY.
