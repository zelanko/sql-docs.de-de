---
title: Statusübergänge | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df4a73890841b4a72dbffa0d5a5ae934bf618f16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649842"
---
# <a name="statement-transitions"></a>Anweisungsübergänge
ODBC-Anweisungen werden die folgenden Status haben.  
  
|Status|Description|  
|-----------|-----------------|  
|S0|Nicht zugeordnete Anweisung. (Der Zustand der Verbindung muss C4, C5 oder C6 sein. Weitere Informationen finden Sie unter [Verbindungsübergänge](../../../odbc/reference/appendixes/connection-transitions.md).)|  
|S1|Zugeordnete Anweisung.|  
|S2|Vorbereitete Anweisung. Kein Resultset wird erstellt.|  
|S3|Vorbereitete Anweisung. Ein Resultset für die (möglicherweise leere) wird erstellt.|  
|S4|Anweisung ausgeführt wird und kein Resultset erstellt wurde.|  
|S5|-Anweisung ausgeführt und ein Resultset für die (möglicherweise leere) erstellt wurde. Der Cursor ist geöffnet und vor der ersten Zeile des Resultsets positioniert.|  
|S6|Cursor positioniert mit **SQLFetch** oder **SQLFetchScroll**.|  
|S7|Cursor positioniert mit **SQLExtendedFetch**.|  
|S8|Funktion benötigt Daten. **SQLParamData** nicht aufgerufen wurde.|  
|S9|Funktion benötigt Daten. **SQLPutData** nicht aufgerufen wurde.|  
|S10|Funktion benötigt Daten. **SQLPutData** aufgerufen wurde.|  
|S11|Immer noch ausgeführt wird. In diesem Status wird eine Anweisung bleibt, nachdem eine Funktion, die asynchron ausgeführt wird, SQL_STILL_EXECUTING zurückgibt. Eine Anweisung ist vorübergehend in diesem Zustand, bei der alle Funktionen, die akzeptiert, dass ein Anweisungshandle ausgeführt wird. Temporäre Wohnort in S11 nicht, in allen Statustabellen außer die Statustabelle für angezeigt wird **SQLCancel**. Während eine Anweisung vorübergehend im Zustand S11 befindet, kann die Funktion abgebrochen werden, durch den Aufruf **SQLCancel** aus einem anderen Thread.|  
|S12|Asynchrone Ausführung wurde abgebrochen. In S12 muss eine Anwendung die abgebrochene-Funktion aufrufen, bis sie einen anderen Wert als SQL_STILL_EXECUTING zurückgibt. Die Funktion wurde erfolgreich abgebrochen, nur dann, wenn die Funktion SQL_ERROR zurück, und SQLSTATE HY008 zurück (der Vorgang wurde abgebrochen). Wenn sie einen anderen Wert an, wie SQL_SUCCESS, Fehler beim Vorgang "Abbrechen", und die Funktion normalerweise ausführen zurückgibt.|  
  
 Zustände S2 und S3 bekannt sind, als die vorbereiteten Status ist, gibt die S5 über S7 der Cursor gibt, gibt S8 über S10 als die Notwendigkeit von datenänderungen und S11 "und" S12 als die asynchronen Status gibt. Die Übergänge werden in jedem dieser Gruppen können separat angezeigt, nur, wenn sich die Werte für die einzelnen Zustände in der Gruppe unterscheiden; in den meisten Fällen Statusübergänge der für jede in den einzelnen eine Gruppe sind identisch.  
  
 Die folgenden Tabellen zeigen, wie jede ODBC-Funktion den Zustand der Anweisung auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1 [3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde SQL_HANDLE_DBC auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [4] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] aufrufen **SQLAllocHandle** mit *OutputHandlePtr* verweist auf ein gültiges Handle dieses Handle ohne überschreibt, für den vorherigen Inhalt, verarbeiten und möglicherweise Probleme für ODBC-Treiber verursachen. Falsche ODBC-Anwendung programmieren aufrufen, ist **SQLAllocHandle** zweimal mit der gleichen Anwendungsvariablen, die für definierten  *\*OutputHandlePtr* ohne  **SQLFreeHandle** auf das Handle frei, bevor Sie es erneut zugewiesen werden. Überschreiben von ODBC können Handles auf diese Weise Fehler seitens der ODBC-Treiber zu inkonsistentem Verhalten führen.  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect SQLConnect und SQLDriverConnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|24000|Siehe nächste Tabelle|HY010|Die HY010 o NS [c]|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[s] S8 [d] S11 [X]|--[s] S8 [d] S11 [X]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|--|--|--|S1 [1] S2 [Nr.] und [2] S3 [R] und [2] S5 [3] und [5] S6 ([3] oder [4]) und [6] S7 [4] und [7]|Siehe nächste Tabelle|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** SQL_NEED_DATA zurückgegeben.  
  
 [3] **SQLBulkOperations** SQL_NEED_DATA zurückgegeben.  
  
 [4] **SQLSetPos** SQL_NEED_DATA zurückgegeben.  
  
 [5] **SQLFetch**, **SQLFetchScroll**, oder **SQLExtendedFetch** nicht aufgerufen wurde.  
  
 [6] **SQLFetch** oder **SQLFetchScroll** war aufgerufen wurde.  
  
 [7] **SQLExtendedFetch** war aufgerufen wurde.  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (asynchrone Zustand)  
  
|S11<br /><br /> Immer noch ausgeführt|S12<br /><br /> Asynch abgebrochen|  
|-----------------------------|-----------------------------|  
|[1]-NS-S12 [2]|S12|  
  
 [1] die Anweisung wurde vorübergehend im Zustand S11 während eine Funktion ausgeführt wurde. **SQLCancel** wurde von einem anderen Thread aufgerufen.  
  
 [2] Anweisung wurde im Zustand S11, da eine Funktion, die asynchron aufgerufen SQL_STILL_EXECUTING zurückgegeben.  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|24000|24000|24000|S1 [Np] S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|Siehe nächste Tabelle|24000|--[s] S11 [X]|HY010|Die HY010 o NS [c]|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (vorbereiteten Staaten)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|--[1] 07005[2]|--S11 [s] X|  
  
 [1] *FieldIdentifier* SQL_DESC_COUNT wurde.  
  
 [2] *FieldIdentifier* war nicht SQL_DESC_COUNT.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S5 [s] S11 [X]|S1 [e] S5 [s] S11 [X]|S1 [e] und [1] S5 [s] und [1] S11 [X] und [1] 24000 [2]|Siehe nächste Tabelle|HY010|Die HY010 o NS [c]|  
  
 [1] das aktuelle Ergebnis ist die letzte oder die nur als Ergebnis zurück, oder es sind keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000[1]|24000|  
  
 [1]. dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI [1]|--|--|--|--|HY010|NS [c] und [3] HY010 [o] oder [4]|  
|BEI [2]|HY010|Siehe nächste Tabelle|24000|--S11 [s] X|HY010|NS [c] und [3] HY010 [o] oder [4]|  
  
 [1] für diese Zeile zeigt die Übergänge bei der *SourceDescHandle* Argument war ein ARD, APD oder IPD.  
  
 [2] für diese Zeile zeigt die Übergänge bei der *SourceDescHandle* Argument war ein IRD.  
  
 [3] die *SourceDescHandle* und *TargetDescHandle* Argumente wurden entspricht der Vorgehensweise in der **SQLCopyDesc** -Funktion, die asynchron ausgeführt wird.  
  
 [4] entweder die *SourceDescHandle* Argument oder die *TargetDescHandle* Argument (oder beides) wurden anders als bei der **SQLCopyDesc** -Funktion, die ausgeführt wird asynchron.  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (vorbereiteten Staaten)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|24000[1]|--[s] S11 [X]|  
  
 [1] Diese Zeile zeigt die Übergänge bei der *SourceDescHandle* Argument war ein IRD.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|Siehe nächste Tabelle|24000|--[s] S11 [X]|HY010|Die HY010 o NS [c]|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (vorbereiteten Staaten)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|07005|--[s] S11 [X]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|--[s] S11 [X]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0 [1]|S0 [1]|S0 [1]|S0 [1]|(HY010)|(HY010)|  
  
 [1] aufrufen **SQLDisconnect** frei alle Anweisungen der Verbindung zugeordnet. Darüber hinaus gibt dies den Verbindungsstatus in C2 zurück. der Zustand der Verbindung muss C4 sein, bevor der Status der Anweisung S0 ist.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|: [2] oder [3] S1 [1]|: [3] S1 [Np] und ([1] oder [2]) S1 [p] und [1] S2 [p] und [2]|: [3] S1 [Np] und ([1] oder [2]) S1 [p] und [1] S3 [p] und [2]|(HY010)|(HY010)|  
  
 [1] der *' CompletionType '* Argument ist der sql_commit-Option und **SQLGetInfo** SQL_CB_DELETE für den Informationstyp SQL_CURSOR_COMMIT_BEHAVIOR zurückgegeben oder *' CompletionType '* Argument ist SQL_ROLLBACK und **SQLGetInfo** SQL_CB_DELETE für den Informationstyp SQL_CURSOR_ROLLBACK_BEHAVIOR zurückgegeben.  
  
 [2] der *' CompletionType '* Argument ist der sql_commit-Option und **SQLGetInfo** SQL_CB_CLOSE für den Informationstyp SQL_CURSOR_COMMIT_BEHAVIOR zurückgegeben oder *' CompletionType '* Argument ist SQL_ROLLBACK und **SQLGetInfo** SQL_CB_CLOSE für den Informationstyp SQL_CURSOR_ROLLBACK_BEHAVIOR zurückgegeben.  
  
 [3] die *' CompletionType '* Argument ist der sql_commit-Option und **SQLGetInfo** SQL_CB_PRESERVE für den Informationstyp SQL_CURSOR_COMMIT_BEHAVIOR zurückgegeben oder *' CompletionType '* Argument ist SQL_ROLLBACK und **SQLGetInfo** SQL_CB_PRESERVE für den Informationstyp SQL_CURSOR_ROLLBACK_BEHAVIOR zurückgegeben.  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S4 [s] und [Nr.] S5 [s] und [R] [d] S8 S11 [X]|--[e] und [1] S1 [e] und [2] S4 [s] und [Nr.] S5 [s] und [R] [d] S8 S11 [X]|--[e], [1], und [3] S1 [e], [2] und [3] S4 [s], [Nr.], und [3] S5 [s], [R] und [3] S8 [d] und [3] S11 [X] und [3] 24000 [4]|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
 [1] der Fehler wurde vom Treiber-Manager zurückgegeben.  
  
 [2] der Fehler wurde nicht vom Treiber-Manager zurückgegeben.  
  
 [3] das aktuelle Ergebnis ist die letzte oder die nur als Ergebnis zurück, oder es sind keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000 [1]|24000|  
  
 [1]. dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder  **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|Siehe nächste Tabelle|S2 [e], p und [1] S4 [s], [p], [Nr.], und [1] S5 [s], [p], [R], und sich S8 [d] [p] von [1] und [1] S11 [x] [p] und [1] 24000 [p] und [2] HY010 [Np]|Finden Sie unter Cursor-Statustabelle|HY010|NS [c] HY010 [o]|  
  
 [1] das aktuelle Ergebnis ist die letzte oder die nur als Ergebnis zurück, oder es sind keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [2] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (vorbereiteten Staaten)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|S4 [s] [d] S8 S11 [X]|S5 [s] [d] S8 S11 [X]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 [p] HY010 [Np]|24000 [p], [1] HY010 [Np]|24000 [p] HY010 [Np]|  
  
 [1]. dieser Fehler wird vom Treiber-Manager zurückgegeben, wenn **SQLFetch** oder **SQLFetchScroll** wurden keine SQL_NO_DATA zurückgegeben wird, und wird vom Treiber zurückgegeben, wenn **SQLFetch** oder  **SQLFetchScroll** SQL_NO_DATA zurückgegeben hat.  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|S1010|S1010|24000|Siehe nächste Tabelle|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] oder [nf] S11 [X]|S1010|--[s] oder [nf] S11 [X]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch und SQLFetchScroll  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|24000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch und SQLFetchScroll (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] oder [nf] S11 [X]|--[s] oder [nf] S11 [X]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|BEI [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* war SQL_HANDLE_ENV oder SQL_HANDLE_DBC auf.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [3] für diese Zeile zeigt die Übergänge beim *HandleType* SQL_HANDLE_DESC wurde, und der Deskriptor explizit zugewiesen wurde.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI [1]|--|--|S1 [Np] S2 [p]|S1 [Np] S3 [p]|HY010|HY010|  
|BEI [2]|--|--|--|--|HY010|HY010|  
  
 [1] für diese Zeile zeigt die Übergänge beim *Option* SQL_CLOSE wurde.  
  
 [2] für diese Zeile zeigt die Übergänge beim *Option* SQL_UNBIND oder SQL_RESET_PARAMS war. Wenn die *Option* Argument war SQL_DROP und der zugrunde liegenden Treiber ist ein ODBC 3.*.x* Treiber, der Treiber-Manager ordnet dies für einen Aufruf von **SQLFreeHandle** mit  *HandleType* auf SQL_HANDLE_STMT festgelegt. Weitere Informationen finden Sie in der Tabelle der Zustandsübergänge für [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|24000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|--[s] oder [nf] S11 [24000 [b] HY109 x] [i]|--[s] oder [nf] S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField und SQLGetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|: [1] oder [2] HY010 [3]|Siehe nächste Tabelle|: [1] oder [2] 24000 [3]|: [1], [2] oder [3] S11 [3] und [X]|HY010|NS [c] oder [4] HY010 [o] und [5]|  
  
 [1] der *DescriptorHandle* Argument war ein APD oder ARD.  
  
 [2] der *DescriptorHandle* Argument war ein IPD.  
  
 [3] die *DescriptorHandle* Argument war ein IRD.  
  
 [4] der *DescriptorHandle* Argument wurde das gleiche wie der *DescriptorHandle* -Argument in der **SQLGetDescField** oder **SQLGetDescRec** Funktion, die asynchron ausgeführt wird.  
  
 [5] die *DescriptorHandle* Argument war anders als die *DescriptorHandle* -Argument in der **SQLGetDescField** oder **SQLGetDescRec**-Funktion, die asynchron ausgeführt wird.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField und SQLGetDescRec (vorbereiteten Staaten)  
  
|S2<br /><br /> Keine Ergebnisse|S3<br /><br /> Ergebnisse|  
|-----------------------|--------------------|  
|: [1], [2] oder [3] S11 [2] und [X]|: [1], [2] oder [3] S11 [X]|  
  
 [1] der *DescriptorHandle* Argument war ein APD oder ARD.  
  
 [2] der *DescriptorHandle* Argument war ein IPD.  
  
 [3] die *DescriptorHandle* Argument war ein IRD. Beachten Sie, dass diese Funktionen immer SQL_NO_DATA in den Zustand S2 zurück Wenn *DescriptorHandle* wurde ein IRD.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|BEI [2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] für diese Zeile zeigt die Übergänge beim *HandleType* war SQL_HANDLE_ENV auf, SQL_HANDLE_DBC auf oder SQL_HANDLE_DESC.  
  
 [2] für diese Zeile zeigt die Übergänge beim *HandleType* wurde von SQL_HANDLE_STMT auf.  
  
 [3] **SQLGetDiagField** immer gibt einen Fehler in diesem Zustand über, wenn *DiagIdentifier* SQL_DIAG_ROW_COUNT ist.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|Siehe nächste Tabelle|HY010|HY010|  
  
 [1] das Anweisungsattribut war nicht SQL_ATTR_ROW_NUMBER.  
  
 [2]-Anweisungsattribut war SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|: [1] oder ([V] und [2]) 24000 [b] und [2] HY109 [i] und [2]|--[i] oder ([V] und [2]) 24000 [b] und [2] HY109 [1] und [2]|  
  
 [1] der *Attribut* Argument war kein SQL_ATTR_ROW_NUMBER.  
  
 [2] der *Attribut* Argument war SQL_ATTR_ROW_NUMBER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|--[1]|--[1]|--[s] und [2] S1 [nf], [Np], [4] S2 [nf], [p], [4] S5 [s] und [3] S11 [X]|S1 [nf], [Np], [4] S3 [nf], [p] und [4] S4 [s] und [2] S5 [s] und [3] S11 [X]|HY010|NS [c] HY010 [o]|  
  
 [1]. die Funktion gibt SQL_NO_DATA immer in diesem Zustand zurück.  
  
 [2] das nächste Ergebnis ist die Zeilenanzahl.  
  
 [3] das nächste Ergebnis ist ein Resultset.  
  
 [4] das aktuelle Ergebnis ist das letzte Ergebnis.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|--[s] S11 [X]|--[s] S11 [X]|--[s] S11 [X]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|--[s] S11 [X]|--[s] S11 [X]|--[s] S11 [X]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|HY010|HY010|Siehe nächste Tabelle|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>Der SQLParamData (müssen Daten Staaten)  
  
|S8<br /><br /> Daten erforderlich|S9<br /><br /> Müssen|S10<br /><br /> Können|  
|----------------------|---------------------|---------------------|  
|S1 [e] und [1] S2 [e], [Nr.], und [2] S3 [e], [R] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und S9 [3] [d] S11 [X]|HY010|S1 [e] und [1] S2 [e], [Nr.], und [2] S3 [e], [R] und [2] S4 [s], [Nr.], und ([1] oder [2]) S5 [s], [R], und ([1] oder [2]) S5 ([s] oder [e]) und [4] S6 ([s] oder [e]) und [5] S7 ([s] oder [e]) und S9 [3] [d] S11 [X]|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** SQL_NEED_DATA zurückgegeben.  
  
 [3] **SQLSetPos** SQL_NEED_DATA zurückgegeben und vom Zustand S7 aufgerufen wurde.  
  
 [4] **SQLBulkOperations** SQL_NEED_DATA zurückgegeben und vom Zustand S5 aufgerufen wurde.  
  
 [5] **SQLSetPos** oder **SQLBulkOperations** SQL_NEED_DATA zurückgegeben und vom Zustand S6 aufgerufen wurde.  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|S2 [s] und [Nr.] S3 [s] und [R] S11 [X]|--[s] oder ([e] und [1]) S1 [e] und [2] S11 [X]|S1 [e] und [3] S2 [s], [Nr.,] und [3] S3 [s], [R] und [3] S11 [X] und [3] 24000 [4]|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
 [1] für die Vorbereitung einem anderen Grund als überprüfen die Anweisung schlägt fehl (SQLSTATE wurde HY009 [Name des ungültigen Argumentwerts] oder HY090 [ungültige Zeichenfolgen- oder Pufferlänge Länge]).  
  
 [2] für die Vorbereitung ein Fehler auftritt, während der Überprüfung der Anweisung (SQLSTATE war nicht HY009 [Name des ungültigen Argumentwerts] oder HY090 [ungültige Zeichenfolgen- oder Pufferlänge Länge]).  
  
 [3] das aktuelle Ergebnis ist die letzte oder die nur als Ergebnis zurück, oder es sind keine aktuellen Ergebnisse. Weitere Informationen zu mehreren Ergebnissen, finden Sie unter [mehrere Ergebnisse](../../../odbc/reference/develop-app/multiple-results.md).  
  
 [4] das aktuelle Ergebnis ist nicht das letzte Ergebnis.  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000|24000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|HY010|HY010|Siehe nächste Tabelle|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (müssen Daten Staaten)  
  
|S8<br /><br /> Daten erforderlich|S9<br /><br /> Müssen|S10<br /><br /> Können|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] und [1] S2 [e], [Nr.], und [2] S3 [e], [R] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S10 [s] S11 [X]|--[s] S1 [e] und [1] S2 [e], [Nr.], und [2] S3 [e], [R] und [2] S5 [e] und [4] S6 [e] und [5] S7 [e] und [3] S11 [X] HY011 [6]|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA zurückgegeben.  
  
 [2] **SQLExecute** SQL_NEED_DATA zurückgegeben.  
  
 [3] **SQLSetPos** SQL_NEED_DATA zurückgegeben und vom Zustand S7 aufgerufen wurde.  
  
 [4] **SQLBulkOperations** SQL_NEED_DATA zurückgegeben und vom Zustand S5 aufgerufen wurde.  
  
 [5] **SQLSetPos** oder **SQLBulkOperations** SQL_NEED_DATA zurückgegeben und vom Zustand S6 aufgerufen wurde.  
  
 [6] eine oder mehrere Aufrufe von **SQLPutData** für ein einzelnen Parameter SQL_SUCCESS zurück, und klicken Sie dann einen Aufruf zurückgegebenen **SQLPutData** wurde versucht, für den gleichen Parameter mit *StrLen_or_Ind* festlegen auf SQL_NULL_DATA.  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(IH)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 [1] für diese Zeile zeigt die Übergänge beim *Attribut* wurde ein Verbindungsattribut. Für geht beim *Attribut* wurde eine Anweisung Attribut, finden Sie in der Anweisung übergangstabelle **SQLSetStmtAttr**.  
  
 [2] der *Attribut* Argument war kein SQL_ATTR_CURRENT_CATALOG.  
  
 [3] die *Attribut* Argument war SQL_ATTR_CURRENT_CATALOG.  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|--|24000|24000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField und SQLSetDescRec  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI [1]|--|--|--|--|HY010|HY010|  
  
 [1] für diese Zeile zeigt die Übergänge, in denen die *DescriptorHandle* Argument ist ein ARD, APD IPD, oder (für **SQLSetDescField**) eine IRD bei der *FieldIdentifier* Argument ist SQL_ DESC_ARRAY_STATUS_PTR oder SQL_DESC_ROWS_PROCESSED_PTR. Es ist ein Fehler Aufrufen **SQLSetDescField** für eine IRD beim *FieldIdentifier* einen anderen Wert.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|HY010|HY010|24000|Siehe nächste Tabelle|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (Cursor Staaten)  
  
|S5<br /><br /> Geöffnet|S6<br /><br /> SQLFetch oder SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|--[s] [d] S8 S11 [24000 [b] HY109 x] [i]|--[s] [d] S8 S11 [24000 [b] HY109 x] [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> Nicht zugeordnet|S1<br /><br /> zugewiesen|S2 – S3<br /><br /> Vorbereitet|S4<br /><br /> ausgeführt|S5 – S7<br /><br /> Cursor|S8-S10<br /><br /> Daten erforderlich|S11-S12<br /><br /> Async|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|BEI|--|: [1] HY011 [2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [Np] oder [1] HY011 [p] und [2]|HY010 [Np] oder [1] HY011 [p] und [2]|  
  
 [1] der *Attribut* Argument war kein SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE und SQL_ATTR_CURSOR_SENSITIVITY.  
  
 [2] der *Attribut* Argument war, SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE und SQL_ATTR_CURSOR_SENSITIVITY.
