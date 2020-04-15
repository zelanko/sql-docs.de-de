---
title: Anweisungsübergänge | Microsoft Docs
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
ms.openlocfilehash: 55f82e275bfd5bff12544b35a1370cdb31495320
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302851"
---
# <a name="statement-transitions"></a>Anweisungsübergänge
ODBC-Anweisungen haben die folgenden Zustände.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|S0|Nicht zugewiesene Anweisung. (Der Verbindungsstatus muss C4, C5 oder C6 sein. Weitere Informationen finden Sie unter [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Zugeordnete Anweisung.|  
|S2|Vorbereitete Erklärung. Es wird kein Resultset erstellt.|  
|S3|Vorbereitete Erklärung. Es wird ein (möglicherweise leeres) Resultset erstellt.|  
|S4|Anweisung ausgeführt und es wurde kein Resultset erstellt.|  
|S5|Anweisung ausgeführt und ein (möglicherweise leeres) Resultset wurde erstellt. Der Cursor ist geöffnet und vor der ersten Zeile des Resultsets positioniert.|  
|S6|Cursor positioniert mit **SQLFetch** oder **SQLFetchScroll**.|  
|S7|Cursor positioniert mit **SQLExtendedFetch**.|  
|S8|Funktion benötigt Daten. **SQLParamData** wurde nicht aufgerufen.|  
|S9|Funktion benötigt Daten. **SQLPutData** wurde nicht aufgerufen.|  
|S10|Funktion benötigt Daten. **SQLPutData** wurde aufgerufen.|  
|S11|Wird immer noch ausgeführt. Eine Anweisung wird in diesem Zustand verbleibt, nachdem eine Funktion, die asynchron ausgeführt wird, SQL_STILL_EXECUTING zurückgibt. Eine Anweisung befindet sich vorübergehend in diesem Zustand, während jede Funktion, die ein Anweisungshandle akzeptiert, ausgeführt wird. Der temporäre Aufenthalt im Status S11 wird in keiner Zustandstabelle mit Ausnahme der Zustandstabelle für **SQLCancel**angezeigt. Während sich eine Anweisung vorübergehend im Status S11 befindet, kann die Funktion abgebrochen werden, indem **SQLCancel** von einem anderen Thread aufgerufen wird.|  
|S12|Asynchrone Ausführung abgebrochen. In S12 muss eine Anwendung die abgebrochene Funktion aufrufen, bis sie einen anderen Wert als SQL_STILL_EXECUTING zurückgibt. Die Funktion wurde nur dann erfolgreich abgebrochen, wenn die Funktion SQL_ERROR und SQLSTATE HY008 (Vorgang abgebrochen) zurückgibt. Wenn ein anderer Wert zurückgegeben wird, z. B. SQL_SUCCESS, ist der Abbruchvorgang fehlgeschlagen und die Funktion wird normal ausgeführt.|  
  
 Die Staaten S2 und S3 werden als die vorbereiteten Zustände, die Zustände S5 bis S7 als Cursorstaaten, die Zustände S8 bis S10 als Bedarfsdatenstaaten und die Zustände S11 und S12 als asynchrone Zustände bezeichnet. In jeder dieser Gruppen werden die Übergänge nur dann separat angezeigt, wenn sie für jeden Zustand in der Gruppe unterschiedlich sind. In den meisten Fällen sind die Übergänge für jeden Zustand in jeder Gruppe identisch.  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Anweisungsstatus auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1[3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [4] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] Aufrufen von **SQLAllocHandle** mit *OutputHandlePtr,* der auf ein gültiges Handle verweist, überschreibt, dass das Handle ohne Rücksicht auf den vorherigen Inhalt dieses Handles behandelt wird und Probleme für ODBC-Treiber verursachen kann. Es ist falsch, dass die ODBC-Anwendungsprogrammierung **SQLAllocHandle** zweimal mit derselben Anwendungsvariablen aufruft, die für * \*OutputHandlePtr* definiert ist, ohne **SQLFreeHandle** aufzurufen, um das Handle freizugeben, bevor es neu zugewiesen wird. Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistentem Verhalten oder Fehlern seitens odBC-Treibern führen.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect, SQLConnect und SQLDriverConnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Siehe nächste Tabelle|HY010|NS [c] HY010 o|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|-- [s] S8 [d] S11 [x]|-- [s] S8 [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|S1[1] S2 [nr] und [2] S3 [r] und [2] S5[3] und [5] S6([3] oder [4]) und [6] S7[4] und [7]|Siehe nächste Tabelle|  
  
 [1] **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** gab SQL_NEED_DATA zurück.  
  
 [3] **SQLBulkOperations** hat SQL_NEED_DATA zurückgegeben.  
  
 [4] **SQLSetPos** gab SQL_NEED_DATA zurück.  
  
 [5] **SQLFetch**, **SQLFetchScroll**oder **SQLExtendedFetch** wurden nicht aufgerufen.  
  
 [6] **SQLFetch** oder **SQLFetchScroll** wurden aufgerufen.  
  
 [7] **SQLExtendedFetch** wurde aufgerufen.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (Asynchrone Zustände)  
  
|S11<br /><br /> Noch ausführen|S12<br /><br /> Asynch abgebrochen|  
|-----------------------------|-----------------------------|  
|NS[1] S12[2]|S12|  
  
 [1] Die Anweisung befand sich vorübergehend im Zustand S11, während eine Funktion ausgeführt wurde. **SQLCancel** wurde von einem anderen Thread aufgerufen.  
  
 [2] Die Anweisung befand sich im Zustand S11, da eine Funktion namens asynchron SQL_STILL_EXECUTING zurückgegeben wurde.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|24.000|24.000|24.000|S1 [np] S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Siehe nächste Tabelle|24.000|-- [s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|--[1] 07005[2]|-- [s] S11 x|  
  
 [1] *FieldIdentifier* wurde SQL_DESC_COUNT.  
  
 [2] *FieldIdentifier* wurde nicht SQL_DESC_COUNT.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S5 [s] S11 [x]|S1 [e] S5 [s] S11 [x]|S1 [e] und [1] S5 [s] und [1] S11 [x] und [1] 24000[2]|Siehe nächste Tabelle|HY010|NS [c] HY010 o|  
  
 [1] Das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es gibt keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] Das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables (Cursor zu Zuständen)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24000[1]|24.000|  
  
 [1] Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat und vom Treiber zurückgegeben wird, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH[1]|--|--|--|--|HY010|NS [c] und [3] HY010 [o] oder [4]|  
|IH[2]|HY010|Siehe nächste Tabelle|24.000|-- [s] S11 x|HY010|NS [c] und [3] HY010 [o] oder [4]|  
  
 [1] Diese Zeile zeigt Übergänge, wenn das *SourceDescHandle-Argument* eine ARD, APD oder IPD war.  
  
 [2] Diese Zeile zeigt Übergänge, wenn das *SourceDescHandle-Argument* ein IRD war.  
  
 [3] Die *Argumente SourceDescHandle* und *TargetDescHandle* waren identisch mit der **SQLCopyDesc-Funktion,** die asynchron ausgeführt wird.  
  
 [4] Entweder das *SourceDescHandle-Argument* oder das *TargetDescHandle-Argument* (oder beide) unterschieden sich von der **SQLCopyDesc-Funktion,** die asynchron ausgeführt wird.  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (Vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|24000[1]|-- [s] S11 [x]|  
  
 [1] Diese Zeile zeigt Übergänge, wenn das *SourceDescHandle-Argument* ein IRD war.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|Siehe nächste Tabelle|24.000|-- [s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (Vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|07005|-- [s] S11 [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|-- [s] S11 [x]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0[1]|S0[1]|S0[1]|S0[1]|(HY010)|(HY010)|  
  
 [1] Beim Aufrufen von **SQLDisconnect** werden alle Anweisungen frei, die der Verbindung zugeordnet sind. Darüber hinaus wird der Verbindungsstatus an C2 zurückgegeben. Der Verbindungsstatus muss C4 sein, bevor der Anweisungsstatus S0 ist.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--[2] oder [3] S1[1]|--[3] S1 [np] und ([1] oder [2]) S1 [p] und [1] S2 [p] und [2]|--[3] S1 [np] und ([1] oder [2]) S1 [p] und [1] S3 [p] und [2]|(HY010)|(HY010)|  
  
 [1] Das *CompletionType-Argument* lautet SQL_COMMIT und **SQLGetInfo** gibt SQL_CB_DELETE für den SQL_CURSOR_COMMIT_BEHAVIOR-Informationstyp zurück, oder das *CompletionType-Argument* ist SQL_ROLLBACK und **SQLGetInfo** gibt SQL_CB_DELETE für den SQL_CURSOR_ROLLBACK_BEHAVIOR-Informationstyp zurück.  
  
 [2] Das *CompletionType-Argument* lautet SQL_COMMIT und **SQLGetInfo** gibt SQL_CB_CLOSE für den SQL_CURSOR_COMMIT_BEHAVIOR-Informationstyp zurück, oder das *CompletionType-Argument* ist SQL_ROLLBACK und **SQLGetInfo** gibt SQL_CB_CLOSE für den SQL_CURSOR_ROLLBACK_BEHAVIOR-Informationstyp zurück.  
  
 [3] Das *CompletionType-Argument* ist SQL_COMMIT und **SQLGetInfo** gibt SQL_CB_PRESERVE für den SQL_CURSOR_COMMIT_BEHAVIOR-Informationstyp zurück, oder das *CompletionType-Argument* ist SQL_ROLLBACK und **SQLGetInfo** gibt SQL_CB_PRESERVE für den SQL_CURSOR_ROLLBACK_BEHAVIOR-Informationstyp zurück.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S4 [s] und [nr] S5 [s] und [r] S8 [d] S11 [x]|-- [e] und [1] S1 [e] und [2] S4 [s] und [nr] S5 [s] und [r] S8 [d] S11 [x]|-- [e], [1] und [3] S1 [e], [2] und [3] S4 [s], [nr], und [3] S5 [s], [r], und [3] S8 [d] und [3] S11 [x] und [3] 24000 [4]|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
 [1] Der Fehler wurde vom Treiber-Manager zurückgegeben.  
  
 [2] Der Fehler wurde vom Treiber-Manager nicht zurückgegeben.  
  
 [3] Das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es gibt keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] Das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24000 [1]|24.000|  
  
 [1] Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|Siehe nächste Tabelle|S2 [e], p und [1] S4 [s], [p], [nr] und [1] S5 [s], [p], [r] und [1] S8 [d], [p] und [1] S11 [x], [p] und [1] 24000 [p] und [2] HY010 [np]|Siehe Cursor-Zustände-Tabelle|HY010|NS [c] HY010 [o]|  
  
 [1] Das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es gibt keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] Das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (Vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|S4 [s] S8 [d] S11 [x]|S5 [s] S8 [d] S11 [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 [p] HY010 [np]|24000 [p], [1] HY010 [np]|24000 [p] HY010 [np]|  
  
 [1] Dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA nicht zurückgegeben hat, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben haben.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|S1010|S1010|24.000|Siehe nächste Tabelle|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] oder [nf] S11 [x]|S1010|-- [s] oder [nf] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch und SQLFetchScroll  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch und SQLFetchScroll (Cursor-Zustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] oder [nf] S11 [x]|-- [s] oder [nf] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|IH [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 [1] Diese Zeile zeigt Übergänge an, wenn *HandleType* SQL_HANDLE_ENV oder SQL_HANDLE_DBC wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [3] Diese Zeile zeigt Übergänge an, bei denen *HandleType* SQL_HANDLE_DESC und der Deskriptor explizit zugewiesen wurde.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH [1]|--|--|S1 [np] S2 [p]|S1 [np] S3 [p]|HY010|HY010|  
|IH [2]|--|--|--|--|HY010|HY010|  
  
 [1] Diese Zeile zeigt Übergänge, wenn *Option* SQL_CLOSE wurde.  
  
 [2] Diese Zeile zeigt Übergänge, wenn *Option* SQL_UNBIND oder SQL_RESET_PARAMS wurde. Wenn das *Argument Option* SQL_DROP wurde und der zugrunde liegende Treiber ein ODBC 3 *.x-Treiber* ist, ordnet der Treiber-Manager dies einem Aufruf von **SQLFreeHandle** zu, wobei *HandleType* auf SQL_HANDLE_STMT festgelegt ist. Weitere Informationen finden Sie in der Übergangstabelle für [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|-- [s] oder [nf] S11 [x] 24000 [b] HY109 [i]|-- [s] oder [nf] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|-- [1] oder [2] HY010 [3]|Siehe nächste Tabelle|-- [1] oder [2] 24000 [3]|-- [1], [2] oder [3] S11 [3] und [x]|HY010|NS [c] oder [4] HY010 [o] und [5]|  
  
 [1] Das *DescriptorHandle-Argument* war eine APD oder ARD.  
  
 [2] Das *DescriptorHandle-Argument* war ein IPD.  
  
 [3] Das *DescriptorHandle-Argument* war ein IRD.  
  
 [4] Das *DescriptorHandle-Argument* war identisch mit dem *DescriptorHandle-Argument* in der **SQLGetDescField-** oder **SQLGetDescRec-Funktion,** die asynchron ausgeführt wird.  
  
 [5] Das *DescriptorHandle-Argument* unterscheidet sich von dem *DescriptorHandle-Argument* in der **SQLGetDescField-** oder **SQLGetDescRec-Funktion,** die asynchron ausgeführt wird.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField und SQLGetDescRec (Vorbereitete Zustände)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|--[1], [2] oder [3] S11[2] und [x]|--[1], [2] oder [3] S11 [x]|  
  
 [1] Das *DescriptorHandle-Argument* war eine APD oder ARD.  
  
 [2] Das *DescriptorHandle-Argument* war ein IPD.  
  
 [3] Das *DescriptorHandle-Argument* war ein IRD. Beachten Sie, dass diese Funktionen immer SQL_NO_DATA im Zustand S2 zurückgeben, wenn *DescriptorHandle* ein IRD war.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|IH[2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] Diese Zeile zeigt Übergänge an, bei denen *HandleType* SQL_HANDLE_ENV, SQL_HANDLE_DBC oder SQL_HANDLE_DESC wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [3] **SQLGetDiagField** gibt immer einen Fehler in diesem Zustand zurück, wenn *DiagIdentifier* SQL_DIAG_ROW_COUNT ist.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|Siehe nächste Tabelle|HY010|HY010|  
  
 [1] Das Anweisungsattribut wurde nicht SQL_ATTR_ROW_NUMBER.  
  
 [2] Das Anweisungsattribut wurde SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|--[1] oder ([v] und [2]) 24000 [b] und [2] HY109 [i] und [2]|-- [i] oder ([v] und [2]) 24000 [b] und [2] HY109[1] und [2]|  
  
 [1] Das *Attributargument* wurde nicht SQL_ATTR_ROW_NUMBER.  
  
 [2] Das *Attributargument* wurde SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|--[1]|--[1]|-- [s] und [2] S1 [nf], [np] und [4] S2 [nf], [p] und [4] S5 [s] und [3] S11 [x]|S1 [nf], [np] und [4] S3 [nf], [p] und [4] S4 [s] und [2] S5 [s] und [3] S11 [x]|HY010|NS [c] HY010 [o]|  
  
 [1] Die Funktion gibt immer SQL_NO_DATA in diesem Zustand zurück.  
  
 [2] Das nächste Ergebnis ist eine Zeilenanzahl.  
  
 [3] Das nächste Ergebnis ist ein Resultset.  
  
 [4] Das aktuelle Ergebnis ist das letzte Ergebnis.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|-- [s] S11 [x]|-- [s] S11 [x]|-- [s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|-- [s] S11 [x]|-- [s] S11 [x]|-- [s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Siehe nächste Tabelle|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (Datenzustände benötigen)  
  
|S8<br /><br /> Benötigen Von Daten|S9<br /><br /> Must Put|S10<br /><br /> Can Put|  
|----------------------|---------------------|---------------------|  
|S1 [e] und [1] S2 [e], [nr] und [2] S3 [e], [r], und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S9 [d] S11 [x]|HY010|S1 [e] und [1] S2 [e], [nr] und [2] S3 [e], [r], und [2] S4 [s], [nr] und ([1] oder [2]) S5 [s], [r], und ([1] oder [2]) S5 ([s] oder [e]) und [4] S6 ([s] oder [e]) und [5] S7 ([s] oder [e]) und [3] S9 [d] S11 [x]|  
  
 [1] **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** gab SQL_NEED_DATA zurück.  
  
 [3] **SQLSetPos** wurde vom Zustand S7 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [4] **SQLBulkOperations** wurde vom Status S5 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [5] **SQLSetPos** oder **SQLBulkOperations** wurden vom Status S6 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S2 [s] und [nr] S3 [s] und [r] S11 [x]|-- [s] oder ([e] und [1]) S1 [e] und [2] S11 [x]|S1 [e] und [3] S2 [s], [nr] und [3] S3 [s], [r] und [3] S11 [x] und [3] 24000[4]|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
 [1] Die Vorbereitung schlägt aus einem anderen Grund als der Validierung der Anweisung fehl (der SQLSTATE war HY009 [Ungültiger Argumentwert] oder HY090 [Ungültige Zeichenfolge oder Pufferlänge]).  
  
 [2] Die Vorbereitung schlägt beim Überprüfen der Anweisung fehl (die SQLSTATE war nicht HY009 [Ungültiger Argumentwert] oder HY090 [Ungültige Zeichenfolge oder Pufferlänge]).  
  
 [3] Das aktuelle Ergebnis ist das letzte oder einzige Ergebnis, oder es gibt keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen finden Sie unter [Mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] Das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|24.000|24.000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|HY010|HY010|Siehe nächste Tabelle|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (Datenzustände benötigen)  
  
|S8<br /><br /> Benötigen Von Daten|S9<br /><br /> Must Put|S10<br /><br /> Can Put|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] und [1] S2 [e], [nr] und [2] S3 [e], [r], und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S10 [s] S11 [x]|-- [s] S1 [e] und [1] S2 [e], [nr] und [2] S3 [e], [r], und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S11 [x] HY011[6]|  
  
 [1] **SQLExecDirect** hat SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** gab SQL_NEED_DATA zurück.  
  
 [3] **SQLSetPos** wurde vom Zustand S7 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [4] **SQLBulkOperations** wurde vom Status S5 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [5] **SQLSetPos** oder **SQLBulkOperations** wurden vom Status S6 aufgerufen und SQL_NEED_DATA zurückgegeben.  
  
 [6] Ein oder mehrere Aufrufe von **SQLPutData** für einen einzelnen Parameter, der SQL_SUCCESS zurückgegeben wurde, und dann wurde ein Aufruf von **SQLPutData** für denselben Parameter mit *StrLen_or_Ind* auf SQL_NULL_DATA festgelegt.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 [1] Diese Zeile zeigt Übergänge an, wenn *Attribute* ein Verbindungsattribut war. Informationen zu Übergängen, bei denen *Attribute* ein Anweisungsattribut war, finden Sie in der Anweisungsübergangstabelle für **SQLSetStmtAttr**.  
  
 [2] Das *Attributargument* wurde nicht SQL_ATTR_CURRENT_CATALOG.  
  
 [3] Das *Attributargument* wurde SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--|24.000|24.000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH[1]|--|--|--|--|HY010|HY010|  
  
 [1] Diese Zeile zeigt Übergänge, bei denen das *DescriptorHandle-Argument* ein ARD-, APD-, IPD- oder (für **SQLSetDescField**) eine IRD ist, wenn das *FieldIdentifier-Argument* SQL_DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR ist. Es ist ein Fehler, **SQLSetDescField** für eine IRD aufzurufen, wenn *FieldIdentifier* ein anderer Wert ist.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|HY010|HY010|24.000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (Cursorzustände)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24.000|-- [s] S8 [d] S11 [x] 24000 [b] HY109 [i]|-- [s] S8 [d] S11 [x] 24000 [b] HY109 [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> Zugeordnet|S2-S3<br /><br /> Vorbereitet|S4<br /><br /> Ausgeführt|S5-S7<br /><br /> Cursor|S8-S10<br /><br /> Benötigen Von Daten|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|IH|--|--[1] HY011[2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [np] oder [1] HY011 [p] und [2]|HY010 [np] oder [1] HY011 [p] und [2]|  
  
 [1] Das *Attributargument* war nicht SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE oder SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] Das *Attributargument* wurde SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE oder SQL_ATTR_CURSOR_SENSITIVITY.
