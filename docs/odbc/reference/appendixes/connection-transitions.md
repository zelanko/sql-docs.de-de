---
title: Verbindungsübergänge | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transitioning states [ODBC], connection
- connection transitions [ODBC]
- state transitions [ODBC], connection
ms.assetid: 6b6e1a47-4a52-41c8-bb9e-7ddeae09913e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 225f8517a78f8e9d4d765163649da174d72e490c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284770"
---
# <a name="connection-transitions"></a>Verbindungsübergänge
ODBC-Verbindungen haben die folgenden Zustände.  
  
|State|BESCHREIBUNG|  
|-----------|-----------------|  
|C0|Nicht zugewiesene Umgebung, nicht zugewiesene Verbindung|  
|C1|Zugeordnete Umgebung, nicht zugewiesene Verbindung|  
|C2|Zugeordnete Umgebung, zugewiesene Verbindung|  
|C3|Verbindungsfunktion benötigt Daten|  
|C4|Verbundene Verbindung|  
|C5|Verbundene Verbindung, zugeordnete Anweisung|  
|C6|Verbundene Verbindung, laufende Transaktion. Es ist möglich, dass sich eine Verbindung im Zustand C6 befindet, ohne dass Anweisungen für die Verbindung zugewiesen sind. Angenommen, die Verbindung befindet sich im manuellen Commit-Modus und befindet sich im Status C4. Wenn eine Anweisung zugewiesen, ausgeführt (eine Transaktion gestartet) und dann freigegeben wird, bleibt die Transaktion aktiv, aber es gibt keine Anweisungen für die Verbindung.|  
  
 Die folgenden Tabellen zeigen, wie sich jede ODBC-Funktion auf den Verbindungsstatus auswirkt.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|C0<br /><br /> Kein Env.|C1 Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|--------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|C1[1]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [2]|C2|--[5]|--[5]|--[5]|--[5]|--[5]|  
|(IH) [3]|(IH)|(08003)|(08003)|C5|--[5]|--[5]|  
|(IH) [4]|(IH)|(08003)|(08003)|--[5]|--[5]|--[5]|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [4] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] Aufrufen von **SQLAllocHandle** mit *OutputHandlePtr,* der auf ein gültiges Handle verweist, überschreibt, dass das Handle ohne Rücksicht auf den vorherigen Inhalt dieses Handles behandelt wird und Probleme für ODBC-Treiber verursachen kann. Es ist falsch, dass die ODBC-Anwendungsprogrammierung **SQLAllocHandle** zweimal mit derselben Anwendungsvariablen aufruft, die für * \*OutputHandlePtr* definiert ist, ohne **SQLFreeHandle** aufzurufen, um das Handle freizugeben, bevor es neu zugewiesen wird. Das Überschreiben von ODBC-Handles auf diese Weise kann zu inkonsistentem Verhalten oder Fehlern seitens odBC-Treibern führen.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C3 [d] C4 [s]|-- [d] C2 [e] C4 [s]|(08002)|(08002)|(08002)|  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--[1] C5[2]|  
  
 [1] Die Verbindung befand sich im manuellen Commit-Modus.  
  
 [2] Die Verbindung befand sich im Autocommit-Modus.  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges und SQLTables  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--|  
  
 [1] Die Verbindung befand sich im Autocommit-Modus, oder die Datenquelle hat keine Transaktion gestartet.  
  
 [2] Die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle begann eine Transaktion.  
  
## <a name="sqlconnect"></a>SQLConnect  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlcopydesc-sqlgetdescfield-sqlgetdescrec-sqlsetdescfield-and-sqlsetdescrec"></a>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField und SQLSetDescRec  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|--[1]|--|--|  
  
 [1] In diesem Zustand sind die einzigen Deskriptoren, die der Anwendung zur Verfügung stehen, explizit zugewiesene Deskriptoren.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources und SQLDrivers  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|--|--|--|--|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|C2|C2|C2|25000|  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|C4 s -- n[f]|(08002)|(08002)|(08002)|(08002)|  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--[3]|--[3]|--[3]|--|--|--[4] oder ([5], [6] und [8]) C4[5] und [7] C5[5], [6] und [9]|  
|(IH) [2]|(IH)|(08003)|(08003)|--|--|C5|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Da sich die Verbindung nicht in einem verbundenen Zustand befindet, ist sie von der Transaktion nicht betroffen.  
  
 [4] Der Commit oder Rollback für die Verbindung ist fehlgeschlagen. Die Funktion gibt in diesem Fall SQL_ERROR zurück.  
  
 [5] Der Commit oder Rollback war für die Verbindung erfolgreich. Die Funktion gibt SQL_ERROR zurück, wenn der Commit oder Rollback bei einer anderen Verbindung fehlgeschlagen ist oder die Funktion SQL_SUCCESS zurückgibt, wenn der Commit oder Rollback für alle Verbindungen erfolgreich war.  
  
 [6] Es wurde mindestens eine Anweisung für die Verbindung zugewiesen.  
  
 [7] Es wurden keine Anweisungen für die Verbindung zugewiesen.  
  
 [8] Die Verbindung hatte mindestens eine Anweisung, für die ein offener Cursor vorhanden war, und die Datenquelle behält Cursor bei, wenn Transaktionen festgeschrieben oder zurückgesetzt werden, je nachdem, was angewendet wird (je nachdem, ob *CompletionType* SQL_COMMIT oder SQL_ROLLBACK war). Weitere Informationen finden Sie unter SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Attribute in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 [9] Wenn die Verbindung Anweisungen hatte, für die es offene Cursor gab, wurden die Cursor nicht beibehalten, wenn die Transaktion festgeschrieben oder zurückgesetzt wurde.  
  
## <a name="sqlexecdirect-and-sqlexecute"></a>SQLExecDirect und SQLExecute  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2] C6[3]|--|  
  
 [1] Die Verbindung befand sich im Autocommit-Modus, und die ausgeführte Anweisung war keine *Cursorspezifikation* *specification* (z. B. eine SELECT-Anweisung); oder die Verbindung befand sich im manuellen Commit-Modus, und die ausgeführte Anweisung hat keine Transaktion gestartet.  
  
 [2] Die Verbindung befand sich im Auto-Commit-Modus, und die ausgeführte Anweisung war eine *Cursorspezifikation* *specification* (z. B. eine SELECT-Anweisung).  
  
 [3] Die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle begann eine Transaktion.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|C0|(HY010)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [2]|(IH)|(C1)|(HY010)|(HY010)|(HY010)|(HY010)|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|C4[5] --[6]|--[7] C4[5] und [8] C5[6] und [8]|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [4] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
 [5] Es wurde nur eine Anweisung für die Verbindung zugewiesen.  
  
 [6] Es wurden mehrere Anweisungen für die Verbindung zugewiesen.  
  
 [7] Die Verbindung befand sich im manuellen Commit-Modus.  
  
 [8] Die Verbindung befand sich im Autocommit-Modus.  
  
## <a name="sqlfreestmt"></a>'SQLFreeStmt'  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|(IH)|(IH)|(IH)|(IH)|--|C5[3] --[4]|  
|(IH) [2]|(IH)|(IH)|(IH)|(IH)|--|--|  
  
 [1] Diese Zeile zeigt Transaktionen an, wenn das *Argument Option* SQL_CLOSE ist.  
  
 [2] Diese Zeile zeigt Transaktionen an, wenn das *Option-Argument* SQL_UNBIND oder SQL_RESET_PARAMS ist.  
  
 [3] Die Verbindung befand sich im Auto-Commit-Modus, und es waren keine Cursor für Anweisungen außer dieser geöffnet.  
  
 [4] Die Verbindung befand sich im manuellen Commit-Modus oder im Autocommit-Modus und ein Cursor war für mindestens eine andere Anweisung geöffnet.  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|HY010|--|--|--|  
  
 [1] Das *Attributargument* war SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE, oder es wurde ein Wert für das Verbindungsattribut festgelegt.  
  
 [2] Das *Attributargument* war nicht SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE oder SQL_ATTR_TRACEFILE, und für das Verbindungsattribut wurde kein Wert festgelegt.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField und SQLGetDiagRec  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH) [1]|--|--|--|--|--|--|  
|(IH) [2]|(IH)|--|--|--|--|--|  
|(IH) [3]|(IH)|(IH)|(IH)|(IH)|--|--|  
|(IH) [4]|(IH)|(IH)|(IH)|--|--|--|  
  
 [1] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_ENV wurde.  
  
 [2] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DBC wurde.  
  
 [3] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_STMT wurde.  
  
 [4] Diese Zeile zeigt Übergänge, als *HandleType* SQL_HANDLE_DESC wurde.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|HY010|HY010|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|08003|--|--|--|  
  
 [1] Das *InfoType-Argument* wurde SQL_ODBC_VER.  
  
 [2] Das *InfoType-Argument* wurde nicht SQL_ODBC_VER.  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--[3] C5[1]|  
  
 [1] Die Verbindung befand sich im Autocommit-Modus, und der Aufruf von **SQLMoreResults** hat die Verarbeitung eines Resultsets einer Cursorspezifikation nicht initialisiert.  
  
 [2] Die Verbindung befand sich im Autocommit-Modus, und der Aufruf von **SQLMoreResults** hat die Verarbeitung eines Resultsets einer Cursorspezifikation initialisiert.  
  
 [3] Die Verbindung befand sich im manuellen Commit-Modus.  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(08003)|(08003)|--|--|--|  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--[1] C6[2]|--|  
  
 [1] Die Verbindung befand sich im Autocommit-Modus, oder die Datenquelle hat keine Transaktion gestartet.  
  
 [2] Die Verbindung befand sich im manuellen Commit-Modus, und die Datenquelle begann eine Transaktion.  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|IH|IH|--[1] 08003[2]|HY010|--[3] 08002[4] HY011[5]|--[3] 08002[4] HY011[5]|--[3] und [6] C5[8] 08002[4] HY011[5] oder [7]|  
  
 [1] Das *Attributargument* war nicht SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [2] Das *Attributargument* wurde SQL_ATTR_TRANSLATE_LIB oder SQL_ATTR_TRANSLATE_OPTION.  
  
 [3] Das *Attributargument* wurde nicht SQL_ATTR_ODBC_CURSORS oder SQL_ATTR_PACKET_SIZE.  
  
 [4] Das *Attribut-Argument* wurde SQL_ATTR_ODBC_CURSORS.  
  
 [5] Das *Attributargument* wurde SQL_ATTR_PACKET_SIZE.  
  
 [6] Das *Attributargument* wurde nicht SQL_ATTR_AUTOCOMMIT, oder das *Attributargument* wurde SQL_ATTR_AUTOCOMMIT und das Festlegen dieses Attributs hat die Transaktion nicht übertragen.  
  
 [7] Das *Attribut-Argument* wurde SQL_ATTR_TXN_ISOLATION.  
  
 [8] Das *Attributargument* wurde SQL_ATTR_AUTOCOMMIT, und durch Festlegen dieses Attributs wurde die Transaktion festgeschrieben.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|--|--|(HY010)|--|--|--|  
  
## <a name="all-other-odbc-functions"></a>Alle anderen ODBC-Funktionen  
  
|C0<br /><br /> Kein Env.|C1<br /><br /> Nicht zugeordnet|C2<br /><br /> Zugeordnet|C3<br /><br /> Benötigen Von Daten|C4<br /><br /> Verbunden|C5<br /><br /> -Anweisung.|C6<br /><br /> Transaktion|  
|--------------------|------------------------|----------------------|----------------------|----------------------|----------------------|------------------------|  
|(IH)|(IH)|(IH)|(IH)|(IH)|--|--|
